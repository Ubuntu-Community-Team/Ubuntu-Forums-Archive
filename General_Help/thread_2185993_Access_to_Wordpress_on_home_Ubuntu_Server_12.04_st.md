---
title: "Access to Wordpress on home Ubuntu Server 12.04 stops working after logging out"
date: 2013-11-05
forum: General Help
---

### Post by FiremanEd on 2013-11-05
**Issue**: I recently installed wordpress on my home server successfully.  The problem is, when I log out of the server it (wordpress) stops working. Connecting to it via web browser comes back with 'Forbidden' messages.  I log back in and it starts working normally.

I have a home Ubuntu server with 12.04.3 setup directly connected to a router with a dynamic hosting service (DtDNS).  I installed Wordpress following the directions as so.

1.  Launched the terminal and went to my new document root path:

```
cd /home/your_Ubuntu_username/www
```

2.  Downloaded the latest WordPress version:

```
wget http://wordpress.org/latest.zip
```

3.  Unzipped, I saw the WordPress folder in document root.

4.  Connected to MySQL to create the WordPress database. Issued this command in the terminal, replaced PASSWORD with MySQL root password.

```
mysql -uroot -pPASSWORD -hlocalhost
```

5.  In the MySQL prompt, I created the WordPress database by entering this command:

```
create database wordpress;
```

6.  The database name became “wordpress”. I assigned the database a name:

```
create database MyWordpressDatabase;
```

7.  Went inside my WordPress directory in document root, found the file: wp-config-sample.php. Opened it with a text editor and defined my MySQL connection parameters. I Replaced:

```
define('DB_NAME', 'database_name_here');

/** MySQL database username */
define(‘DB_USER’, ‘username_here’);

/** MySQL database password */
define(‘DB_PASSWORD’, ‘password_here’);

/** MySQL hostname */
define(‘DB_HOST’, ‘localhost’);
```

With my database connection parameters (replacing “Your MYSQL password” with my correct password):

```

define('DB_NAME', 'wordpress');

/** MySQL database username */
define(‘DB_USER’, ‘root’);

/** MySQL database password */
define(‘DB_PASSWORD’, ‘YOUR MYSQL PASSWORD’);

/** MySQL hostname */
define(‘DB_HOST’, ‘localhost’);
```

8.  Replaced the following:

```
define('AUTH_KEY', 'put your unique phrase here');
define('SECURE_AUTH_KEY', 'put your unique phrase here');
define('LOGGED_IN_KEY', 'put your unique phrase here');
define('NONCE_KEY', 'put your unique phrase here');
define('AUTH_SALT', 'put your unique phrase here');
define('SECURE_AUTH_SALT', 'put your unique phrase here');
define('LOGGED_IN_SALT', 'put your unique phrase here');
define('NONCE_SALT', 'put your unique phrase here');
```

With the output provided in this URL:

[https://api.wordpress.org/secret-key/1.1/salt/](https://api.wordpress.org/secret-key/1.1/salt/)

9.  Then, In my text editor, I saved it as:
```

wp-config.php
```

I put wp-config.php inside my WordPress directory along with index.php.

10.  Finally launched the WordPress installation in the web browser by typing this URL:

[http://firemaned.dtdns.net/wordpress/wp-admin/install.php](http://firemaned.dtdns.net/wordpress/wp-admin/install.php)

Followed the rest of the instructions by providing your username, password, email, etc. Then after installation I logged  into the WordPress admin panel in this URL:

[http://firemaned.dtdns.net/wordpress/admin](http://firemaned.dtdns.net/wordpress/admin)

Everything went well. No issues installing and setting up. But, after finishing and logging out (I installed the former via SSH on my regular PC to the server), connecting to Wordpress via web browser results in:

Forbidden

You don't have permission to access / on this server.
Apache/2.2.22 (Ubuntu) Server at firemaned.dtdns.net Port 80

Logging back into the server and Wordpress becomes available again.


Thanks in Advance.  -Ed

---

### Post by mastablasta on 2013-11-05
that would mean that wordpress is locked to specific user. what are your permission settings (on files and folders) for www and wordpress? what groups can access it?

---

### Post by FiremanEd on 2013-11-05
The output of /home/sysadmin/www/
I am starting to see the issue.. Thinking that I need to use chown to change ownership, ie: sudo chown username:group directory

sysadmin@creature-ubuntu-server:~$ ls -la www
total 344

drwxr-xr-x  5 sysadmin sysadmin  4096 Nov  4 20:50 .
drwxrwxr-x  6 sysadmin sysadmin  4096 Nov  4 23:20 ..
-rw-r--r--  1 sysadmin sysadmin   418 Sep 24 20:18 index.php
-rw-r--r--  1 sysadmin sysadmin 19929 Jan 18  2013 license.txt
-rw-r--r--  1 sysadmin sysadmin  7128 Oct 23 16:08 readme.html
-rw-r--r--  1 sysadmin sysadmin  4892 Oct  4 10:12 wp-activate.php
drwxr-xr-x  9 sysadmin sysadmin 16384 Oct 29 16:08 wp-admin
-rw-r--r--  1 sysadmin sysadmin   271 Jan  8  2012 wp-blog-header.php
-rw-r--r--  1 sysadmin sysadmin  4795 Sep  5 21:38 wp-comments-post.php
-rw-r--r--  1 root     root      3450 Nov  4 13:02 wp-config.php
-rw-r--r--  1 sysadmin sysadmin  3152 Nov  4 12:59 wp-config-sample.php
drwxr-xr-x  4 sysadmin sysadmin  4096 Oct 29 16:08 wp-content
-rw-r--r--  1 sysadmin sysadmin  2932 Sep 24 20:18 wp-cron.php
drwxr-xr-x 11 sysadmin sysadmin 20480 Oct 29 16:08 wp-includes
-rw-r--r--  1 sysadmin sysadmin  2380 Sep 24 20:18 wp-links-opml.php
-rw-r--r--  1 sysadmin sysadmin  2359 Sep 12 02:57 wp-load.php
-rw-r--r--  1 sysadmin sysadmin 31739 Oct 23 10:40 wp-login.php
-rw-r--r--  1 sysadmin sysadmin  7772 Oct 22 13:22 wp-mail.php
-rw-r--r--  1 sysadmin sysadmin 10585 Oct  7 15:34 wp-settings.php
-rw-r--r--  1 sysadmin sysadmin 25673 Oct 22 13:22 wp-signup.php
-rw-r--r--  1 sysadmin sysadmin  4026 Sep 24 20:18 wp-trackback.php
-rw-r--r--  1 sysadmin sysadmin  3015 Oct 23 10:40 xmlrpc.php

---

