---
title: "Accessing a DB2 database from PHP"
date: 2007-09-28
forum: General Help
---

### Post by ryjal on 2007-09-28
I am trying to access a DB2 database running on an IBM AIX server from PHP running on Ubuntu 6.06 LTS (Dapper Drake). I have PHP5 and Appache2 installed and am currently using PHP5 to access a MySQL database but I now need to be able to retrieve data from the DB2 database and still retrieve data from the MySQL database. I am not unfamiliar with Linux but still have a lot to learn.

I have spent a great deal of time on this and have look all over the net for a step by step instruction list. Most of what I have found shows how to install a DB2 database then install Appache2 and PHP5. I already have PHP5 installed, working and connecting to a MySQL database. I don’t want to install the whole DB2 database I just want to access a DB2 database running on another server. 

This is what I have done so far. I downloaded the ibm_db2-1.6.3 driver, used Pear to install the driver and then put this line “extension=ibm_db2.so” in the /etc/php5/cli/php.ini file. I then downloaded the DB2 Application Development Client from the IBM support site modified the db2_install script to use alien then ran the db2_install script. I then created the user group db2iadm1 and a user db2inst1 with the primary group set to db2iadm1. I then added the line “ibm_db2.instance_name=db2inst1” in the /etc/php5/cli/php.ini. Then I started the DB2 instance as root using the user db2inst1.

This is where I am not sure where to go or even if I did anything right. I have read that I have to recompile PHP to use the IBM driver but I read somewhere else that PHP5 has the support built in and I am not sure what to do. If there is anyone that could help me out I would be sooooooooo grateful. I am ready to pull my hair out and head for the loony bin.](*,)

---

### Post by jure1873 on 2007-09-29
Check if your php has db2 support. Create a new php file with <?php phpinfo(); ?> in it and open it in your web browser trough apache.

If it's not there you'll have to recompile php from source, because i think there is no php5-db2 in the repositories. 

Maybe this will help you a little:
[http://64.233.183.104/search?q=cache:dFg8EOBcv1oJ:pintmaster.com/wordpress/index.php/20060530/how-to-compile-mssql-support-into-php-in-ubuntu-dapper-drake/+php+on+ubuntu+from+source&hl=en&ct=clnk&cd=6&client=firefox-a]("http://64.233.183.104/search?q=cache:dFg8EOBcv1oJ:pintmaster.com/wordpress/index.php/20060530/how-to-compile-mssql-support-into-php-in-ubuntu-dapper-drake/+php+on+ubuntu+from+source&hl=en&ct=clnk&cd=6&client=firefox-a")

---

### Post by ryjal on 2007-10-01
I ran the <?php phpinfo(); ?> file and this is what I found on db2

ibm_db2
IBM DB2, Cloudscape and Apache Derby support	enabled
Module release 	                                                        1.6.3
Module revision 	                                                1.71
Binary data mode (ibm_db2.binmode) 	                DB2_BINARY
DB2 instance name (ibm_db2.instance_name) 	  db2inst1

---

### Post by ryjal on 2007-10-02
I figured out what I was doing wrong. I was using the odbc_connect function instead of db2_connect. So now I can connect to the database I think. I can get server info but when I try to execute a sql statment I get errors. I am just trying to list the tables in the database. This is the error I am getting.

Connection succeeded.
Execute worked
[IBM][CLI Driver][DB2/6000] SQL0104N An unexpected token "END-OF-STATEMENT" was found following "LIST TABLES". Expected tokens may include: "JOIN ". SQLSTATE=42601

Warning: db2_fetch_row() [function.db2-fetch-row]: Column information cannot be retrieved in /var/www/db2Test.php on line 22

Connection Closed. 

Here is the code I am using.

<?php
        $user = "USERNAME";
        $password = "PASSWORD";
        $database = "DATABASE";
        $hostname = "IP ADDRESS";
        $port = "port";
        $conn_string = "DRIVER={IBM DB2 ODBC DRIVER};DATABASE=$database;" .  "HOSTNAME=$hostname;PORT=$port;PROTOCOL=TCPIP;UID=$user;PWD=$password;";
        $conn = db2_connect($conn_string, '', '');
        
        if ( $conn ) {
                echo "Connection succeeded.\n<br>";
                $stmt = db2_prepare($conn, "LIST TABLES;END");
                $bool = db2_execute( $stmt );
                if( $bool ) {
                        echo "Execute worked\n<br>";
                }
                else {
                        echo "Execute failed\n<br>";
                }
                
                echo db2_stmt_errormsg( $stmt ) . "<br>";
                while ( db2_fetch_row($stmt) ) {
                        $name = db2_result($stmt, 0);
                        echo "$name<br>\n";
                }   
                
                db2_close($conn);
                echo "\n<br>Connection Closed.\n<br>";
        }
        else {
                echo "Connection failed.\n";
                echo db2_conn_errormsg ($connection);
        }
?>

---

