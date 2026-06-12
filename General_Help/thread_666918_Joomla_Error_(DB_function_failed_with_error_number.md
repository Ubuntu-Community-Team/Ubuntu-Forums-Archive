---
title: "Joomla Error (DB function failed with error number 1146. Joe_session)"
date: 2008-01-13
forum: General Help
---

### Post by VolvoPunch on 2008-01-13
I posted this on Joomla forum but I had no imput and its been several days now so I thought I would try my luck here. 

When I type in my servers ip [http://192.168.0.110/atlbricks/](http://192.168.0.110/atlbricks/) I get the message below and I still get the same message even if I go to [http://atlbricks.homelinux.com/atlbricks](http://atlbricks.homelinux.com/atlbricks)

Apache directory (var/www/atlbricks) and get this message. I am sure its something simple but I cannot figure it out. I tried running (REPAIR TABLE Joe_session) but there is no table that I could find so it was unable to repair it. I am still very new to this so forgive my ignorance. 

```

DB function failed with error number 1146
Table 'atlbricksmain.jos_session' doesn't exist SQL=SELECT session_id FROM jos_session WHERE session_id = '0d0cddef583dd77150cf7733aafd4a3d'
SQL =

SELECT session_id
 FROM jos_session
 WHERE session_id = '0d0cddef583dd77150cf7733aafd4a3d'

```

Also I am currently running this on my lan to get things setup properly before opening it up to the world. But how would I create another mysql user and give the user only rights the my joomla site. 

Thanks for the help 

//edit I am using Joomla_1.0.13-Stable-Full_Package

---

### Post by VolvoPunch on 2008-01-13
bump :confused:

---

### Post by VolvoPunch on 2008-01-14
Anyone?

---

### Post by pwdsoft on 2008-04-28
> **VolvoPunch said:**
> Anyone?
DB function failed with error number 1146

[http://www.php-web-development.com/latest/db-function-failed-with-error-number-1146.html](http://www.php-web-development.com/latest/db-function-failed-with-error-number-1146.html)
You have recieved this error because your database is not using jos_ as its prefix , if you let us know what your database prefix is we will change the code to suit your needs or if you are happy to edit code yourself .

Thanks
[http://www.php-web-development.com](http://www.php-web-development.com)

---

### Post by jsblackmaro on 2008-05-31
I am also receiving this error.  I was running Joomla 1.0.15.  I decided to go to Joomla 1.5.    I removed everything (site, and Database) and uploaded the 1.5.3 package.  the first try I got an internal server error.  My hosting company had to rename my htaccess file to testhtaccess.  They said it may need to be rebulit.  After I changed the htaccess, I got to the landing page for Jooomla.  It told me to remove the installation directory before I proceeded, and I did.  I made my configuration.php had the correct database entries on it, and I proceeded.  now I get this:

jtablesession::Store Failed
DB function failed with error number 1146
Table 'x_joshspage_com.jos_session' doesn't exist SQL=INSERT INTO jos_session ( `session_id`,`time`,`username`,`gid`,`guest`,`client_id` ) VALUES ( 'd5c5d550faaed7eb42cd7612110aec00','1212270732','','0','1','0' )


Any ideas?????


Please help!!

Thanks
Josh

---

