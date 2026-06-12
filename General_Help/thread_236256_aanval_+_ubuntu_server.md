---
title: "aanval + ubuntu server"
date: 2006-08-14
forum: General Help
---

### Post by mega on 2006-08-14
I'm having trouble with aanval + dapper server


.! Fatal Error: mysql module not available.

The required module [mysql] is not available within your php binary (cgi).
You must recompile your php binary (cgi) with mysql support.
This must be corrected before Aanval will operate correctly.


I have php5-mysql installed, is there something I'm missing?  I believe I must have php compiled with mysql in, rather than as a module, is there a package for this?

---

### Post by rwlair on 2006-08-18
Okay, here's the fix (at least for me):
I found this little gem on the Ubuntu Web site, specifically:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
"...Edit PHP Configuration to Work With MYSQL (Ubuntu Dapper)

In Dapper Drake, "extension=mysql.so" and "extension=mysqli.so" are enabled in the php.ini file out-of-the-box. However, sometimes php is not looking for those files in the right directory. You have then to move your files or modify the php.ini configuration.:
First solution

locate the directory where the extension files are placed:

 locate mysql.so 

(change mysql.so in mysqli.so if you want to install the mysqli functions)

-then modify the php.ini file to indicate the right place for the extension directory:

$ gksudo "gedit /etc/php4/apache2/php.ini"

or if you are using php5

$ gksudo "gedit /etc/php5/apache2/php.ini"

Look for the 'extension_dir' property, and set it to the directory where you found the mysql(i).so file:

    *

      extension_dir= "/usr/lib/php5/20051025/"

Restart apache, and test if your mysql(i) functions are working.
Second solution

-locate the directory where the extension files are placed:

 locate mysql.so 

(change mysql.so in mysqli.so if you want to install the mysqli functions)

Let's say that you found the file in '/usr/lib/php5/20051025/'

-then check in the php.ini file for the extension directory

$ gksudo "gedit /etc/php4/apache2/php.ini"

or if you are using php5

$ gksudo "gedit /etc/php5/apache2/php.ini"

Look for the 'extension_dir' property. It should be by default '/usr/lib/php5/ext'. If it's not, change it for this value.

-Now create the default directory for extensions:

$ sudo mkdir /usr/lib/php5/ext

-Copy the extension file to the new directory:

$ sudo cp /usr/lib/php5/20051025/mysql.so /usr/lib/php5/ext/mysql.so

Change the first path to the one you found with the locate function, and change mysql.so into mysqli.so if you want to use mysqli functions.

-Restart apache (see below), and test if your mysql(i) functions are working. ..."
I used the nano text editor to do this.
I added the line extension=mysqli.so to the php.ini file as well.

You also need to change the include_path line in the Paths and Directories section to:
include_path = ".:/usr/share/php"
Here's the kicker - you have to do this in all 3 php.ini files listed above in my first post (/etc/php5/apache2/php.ini, /etc/php5/cgi/php/ini, and /etc/php5/cli/php.ini) exactly the same for it to work. Then restart Aanval and restart Apache.

---

