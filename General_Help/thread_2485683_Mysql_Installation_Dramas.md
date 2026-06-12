---
title: "Mysql Installation Dramas"
date: 2023-04-05
forum: General Help
---

### Post by nickTaylor1181 on 2023-04-05
Hi all


I am attempting to install LAMP on Ubuntu 22.04

Apache/2.4.52 
PHP Version 8.1.2-1ubuntu2.11
Mysql Ver 8.0.32-0ubuntu0.22.04.2 for Linux on x86_64 

Apache and PHP running. I can log into Mysql from a CLI


When I try to run Mysql from PHP though it returns:

Fatal error: Uncaught mysqli_sql_exception: Access denied for user 'root'@'localhost' in /home/nick/Desktop/sites/db_test.php:13 Stack trace: #0 /home/nick/Desktop/sites/db_test.php(13): mysqli_connect() #1 {main} thrown in /home/nick/Desktop/sites/db_test.php on line 13

Any clues? 





More information:
............................................................

This is the code :

$servername = "localhost";
$username = "root";
$password = "test";
$dbname = "gm_numbers"; 


// Create connection
$conn = mysqli_connect($servername, $username, $password, $dbname);


// Check connection
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}
echo "Connected successfully";


....


This is the PHPINFO bit about mysql

[h=2]mysqli[/h][TABLE="width: 934"]
[TR="class: h, bgcolor: #9999CC"]
[TH="align: center"]MysqlI Support[/TH]
[TH="align: center"]enabled[/TH]
[/TR]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]Client API library version[/TD]
[TD="class: v, bgcolor: #DDDDDD"]mysqlnd 8.1.2-1ubuntu2.11[/TD]
[/TR]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]Active Persistent Links[/TD]
[TD="class: v, bgcolor: #DDDDDD"]0[/TD]
[/TR]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]Inactive Persistent Links[/TD]
[TD="class: v, bgcolor: #DDDDDD"]0[/TD]
[/TR]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]Active Links[/TD]
[TD="class: v, bgcolor: #DDDDDD"]0[/TD]
[/TR]
[/TABLE]

---

### Post by mrmonteith on 2023-12-04
I ran into the same permissions issue on a totally different system.  But basically the same issue.  You have to going into MySql and use commands to change permissions.  Look on this page
[URL="https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04"]https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04
[/URL] 
 The grant privilege command changes those.

---

### Post by yancek on 2023-12-04
Did you create a password for the root user in mysql?  This is usually done when you run:  mysql_secure_installation as well as doing some other basic things.

---

