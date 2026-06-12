---
title: "How to verify APACHE accessing the correct directory ?"
date: 2014-08-17
forum: General Help
---

### Post by sarahfoxnz on 2014-08-17
Hello. 

After lots of probs upgrading from 12.04 LTS to 14.04 LTS, I have finally got my Pc running again.  HOWEVER, i needed to re-install Apache.

i sucessfully got the apache welcome screen going & server was running.

1) I deleted the index.htm file - & added an .htaccess file to allow directory indexes. 

2) my existing files do not appear to be wiped/erased - taht i had in the /var/www/ folder

However i am now getting a 500 server error (even if i added a index.htm) file back in.

Query 1 :- How do i verify / check WHICH directory is my root ?

Query 2 :- How do i add 'index'es to htm / html  / php  files ?

Query 3 :- How do i allow indexes if no index file found (is it .htaccess - or in a config file ?)

---

### Post by sarahfoxnz on 2014-08-17
here is my log file
> 
192.168.0.6 - - [18/Aug/2014:00:15:54 +1200] "GET / HTTP/1.1" 500 723 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:31.0) Gecko/20100101 Firefox/31.0"
192.168.0.6 - - [18/Aug/2014:00:15:57 +1200] "GET / HTTP/1.1" 500 723 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:31.0) Gecko/20100101 Firefox/31.0"


What does 500 723 mean ?  i've tried to google. but can't locate the meaning of the 723 ?

---

### Post by SeijiSensei on 2014-08-17
First, the default website directory was changed in 14.04 from /var/www to /var/www/html.  Most of your problems will probably disappear if you move your files to that location.

As for index files, Apache treats files as indexes if they are listed in the DirectoryIndex directive:
```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
```
In Ubuntu, this resides in /etc/apache2/mods-available/dir.conf.  The .htm ending is a Windows relic from the days when filenames in DOS/Windows could only have three-letter extensions.

I believe the number following the return code is the size of the object that was served, in this case 723 bytes.

---

### Post by sarahfoxnz on 2014-08-18
Ok.. 

sudo gedit /etc/apache2/mods-available/dir.conf

> 
IfModule mod_dir.c>
    DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet


i have index.htm *AND* index.html files in *BOTH*  /var/www/ and the /var/www/html/ directories. 

so if the web server can access those directories - one of those test html files should be displayed (very primitive 'hello world' html code.)


I'll try the /etc/apache2/ directory & see if i can find a config file to tell apache to look in /var/www etc...

---

### Post by sarahfoxnz on 2014-08-18
Ok - Further :-

/etc/apache2/sites-available/000-default.conf

(i'll remove most of the quoted out text - but leave some in...)

> 
<VirtualHost *:80>
    # The ServerName directive sets the request scheme, hostname and port that
    # However, you must set it for any further virtual host explicitly.
    #ServerName [www.example.com]("http://www.example.com")

    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html

    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    #LogLevel info ssl:warn

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet



what does VIM mean ?  ive seen it in a few files.

according to this - /var/www/html/index.htm  should work ?  or should it have a / at the end ?

EDIT: i've added a / at the end of DocumentRoot - but same problem, 500 error code. (i've removed the trailing / )

---

### Post by sarahfoxnz on 2014-08-18
My log file shows this :- 9no useful information)

> 
127.0.0.1 - - [18/Aug/2014:18:46:22 +1200] "GET / HTTP/1.1" 500 723 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:31.0) Gecko/20100101 Firefox/31.0"
127.0.0.1 - - [18/Aug/2014:18:49:06 +1200] "GET / HTTP/1.1" 500 723 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:31.0) Gecko/20100101 Firefox/31.0"


EDIT :-

Ah - found error log :)


> 

[Mon Aug 18 18:48:59.683752 2014] [mpm_worker:notice] [pid 5500:tid 140077612791680] AH00295: caught SIGTERM, shutting down
[Mon Aug 18 18:49:00.441497 2014] [mpm_worker:notice] [pid 5641:tid 140581687027584] AH00292: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Mon Aug 18 18:49:00.441670 2014] [core:notice] [pid 5641:tid 140581687027584] AH00094: Command line: '/usr/sbin/apache2'
[Mon Aug 18 18:49:06.347035 2014] [core:alert] [pid 5646:tid 140581485389568] [client 127.0.0.1:58258] /var/www/html/.htaccess: <Directory not allowed here



the .htaccess file has this :-

> 
<Directory /var/www/htdocs>
  Options +Indexes
</Directory>


UPDATE:-  If I move the .htaccess file out of the /html/ directory. i can see my index file :)

However - How do i remove the index file & allow the files to be listed - ie i can view the files & subdirecteries ?


My current error (without index.htm)

> 
**Forbidden**

 You don't have permission to access / on this server.




EDIT - i havn't got apache going, but i have another server going :-

> python -m SimpleHTTPServer 84

---

### Post by SeijiSensei on 2014-08-19
You don't use <Directory> statements in .htaccess files because those files apply to the directory in which they are located.

However I recommend dumping any remaining .htaccess files and putting all the directives in the virtual host configurations.  The .htaccess file is a kludge for people sharing a common hosting provider.  If you have direct control over the server, you should place all the configuration data in the vhost files.  That way you only have one place to look.

So, in your case, add this specification to the virtual host configuration for /var/www/html:
```

<VirtualHost ...>
DocumentRoot /var/www/html
[stuff]

<Directory "/var/www/html">
     Options +Indexes
</Directory>

[stuff]
</VirtualHost>

```

Without Indexes enabled, Apache will only show the contents of directories with an index.html or similar file.

I recommend browsing this: [http://httpd.apache.org/docs/2.4/mod/mod_autoindex.html](http://httpd.apache.org/docs/2.4/mod/mod_autoindex.html)

---

