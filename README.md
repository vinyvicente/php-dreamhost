PHP class for the Dreamhost API
===============================

Interfaces with the Dreamhost API

Usage
-----
	
	<?php
	
	use DanielCosta\Dreamhost;

    $api = new Dreamhost('your api key'[,format]);
    $api->exec('command'[, array(arg => value[, ...])]);

Where 'command' is one of the many listed on the [Dreamhost Wiki API](http://wiki.dreamhost.com/API/Api_commands) article.

Method 'exec' returns either an array of associative arrays of the data returned by Dreamhost or throws an exception upon error.

You can define any preferred return format by passing a second argument to class constructor. Defaults to 'json'.

Example
-------

	<?php
	
	use DanielCosta\Dreamhost;
    
    $api = new Dreamhost('your api key'[,format]);

    try {
        print_r($api->exec('api-list_accessible_cmds'));
        // print_r($api->$cmd()); // this would also work
    } catch (Exception $e) {
        echo $e->getMessage(); // contains either the error data returned by dreamhost or a curl error string and number
    }