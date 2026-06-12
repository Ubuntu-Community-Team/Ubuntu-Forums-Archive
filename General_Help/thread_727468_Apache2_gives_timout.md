---
title: "Apache2 gives timout"
date: 2008-03-17
forum: General Help
---

### Post by Stom on 2008-03-17
I've installed apache2 but can't get a page to display when trying to connect to [http://localhost/](http://localhost/), Firefox gives a timeout error instead.

I've added [FONT="Courier New"]ServerName localhost[/FONT] to /etc/apache2/httpd.conf.

I've run[FONT="Courier New"] sudo netstat -plant[/FONT] and the apache entry is bound to 0.0.0.0:80 - is this correct?

Any help is appreciated, I've been battling with this for a while!

---

### Post by Stom on 2008-03-17
*bump*

is there a more suitable category for this post?

---

### Post by Cyanic420 on 2008-03-17
Can you connect to [http://your](http://your) ip address/  ?

---

### Post by fragos on 2008-03-17
Installing apache2 from the repository will give you an http.conf of 0 length.  It works with the address "localhost."  I had to do a little configuration to get PHP to work but HTML, javascript and CSS were fine.  It appears you have configured yourself into a corner.  0.0.0.0 is an illeagal IP address.  The IP of localhost is 127.0.0.1

---

### Post by Stom on 2008-03-18
Cyanic,

No, i cannot connect to either [http://127.0.0.1](http://127.0.0.1), [http://127.0.1.1](http://127.0.1.1) or [http://192.168.0.9](http://192.168.0.9). I just get timeout errors :(

Fragos,

I've tied with the http.conf at its default value and neither html nor php pages work. Do you have any suggestions as to how i might go about troubleshotting this?

Many thanks in advance,

Stom

---

### Post by Stom on 2008-03-18
Update:

I've changed somethign with my tinkering, sudo netstat -plant gives the following:

```
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     5148/mysqld         
tcp        0      0 127.0.1.1:80            0.0.0.0:*               LISTEN     5719/apache2        
tcp        0      0 127.0.0.1:80            0.0.0.0:*               LISTEN     5719/apache2        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5048/cupsd          
tcp        1      0 192.168.0.9:33050       72.14.253.83:80         CLOSE_WAIT 6350/npviewer.bin   
tcp        0      0 192.168.0.9:57645       66.249.93.19:80         ESTABLISHED6290/firefox-bin    
tcp        0      0 192.168.0.9:40285       64.4.36.56:1863         TIME_WAIT  -                   
tcp        1      0 192.168.0.9:47315       74.208.9.80:80          CLOSE_WAIT 6350/npviewer.bin   
tcp        0      1 192.168.0.9:41778       127.0.1.1:80            SYN_SENT   6290/firefox-bin    
tcp        0      1 192.168.0.9:56816       127.0.0.1:80            SYN_SENT   6290/firefox-bin    
tcp        1      0 192.168.0.9:41538       66.249.93.83:80         CLOSE_WAIT 6350/npviewer.bin   
tcp        0      0 192.168.0.9:52170       207.46.111.94:1863      ESTABLISHED6238/pidgin         
tcp        0      1 192.168.0.9:50669       192.168.0.9:80          SYN_SENT   6290/firefox-bin    
tcp        1      0 192.168.0.9:34735       74.208.13.210:80        CLOSE_WAIT 6350/npviewer.bin   
tcp        1      0 192.168.0.9:41537       66.249.93.83:80         CLOSE_WAIT 6350/npviewer.bin   
tcp        0      0 192.168.0.9:56742       66.249.93.18:80         ESTABLISHED6290/firefox-bin    
tcp        0      0 192.168.0.9:46436       72.14.253.125:5222      ESTABLISHED6238/pidgin         
tcp        0      0 192.168.0.9:57646       66.249.93.19:80         ESTABLISHED6290/firefox-bin 
```

---

### Post by acidsolution on 2008-03-18
have you startarted your apache ?

```
sudo /etc/init.d/apache2 restart
```

if apache is already started than try checking for document root in 

```
/etc/apache2/sites-available$ vi default
```
Time out in apache means that your server is not running check if the server is installed properly or not

---

### Post by Stom on 2008-03-18
When trying to do a restart i get the following problem:
```

stom@igorina:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                httpd (no pid file) not running
(99)Cannot assign requested address: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]


```

Now when i do netstat -plant i see that the entries that were previously there for apache2 on 127.0.0.1:80 are no longer there. So after attempting a resart, apache2 doesn't work, but does on boot?

My sites-available default file contains the following:

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.1/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by Stom on 2008-03-18
Hmm, apache still wont restart, only work son fresh boot. I'm still getting the following when trying sudo /etc/init.d/apache2 restart

```
 * Restarting web server apache2                                                                                                        httpd (no pid file) not running
(99)Cannot assign requested address: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

```

Does anyone have any clues? Literally pulling my hair out! I dont need this to be accessible to the outside world, it's only to be used for development purposes.

---

### Post by Stom on 2008-03-18
*bump*

Anyone? Please?

---

### Post by acidsolution on 2008-03-21
Do you have any other services running on the same port 
why dont you make your apache listen to any other port 
this can be done by 

open the file named ports.conf with superuser and than change the Listen 80 to any other port probably not enganged port
```
sudo vi /etc/apache2/ports.conf
```than try restarting the server 
if successfully restarted than type address in browser as 
```
http://localhost:portnumber
```

---

### Post by fragos on 2008-03-21
> **Stom said:**
> *bump*

Anyone? Please?

Your sites-available/default is the same as mine.  I've never touched this file so it's as installed.  Configuring apache is still black magic to me.  I only change those things that are required to get my stuff running.  Sorry I can't be more helpful.

The only config I've done was to get PHP working.  I placed the following three lines in httpd.conf which is otherwise empty.

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

Your problem in all likely hood is in something you did configure yourself.  Review all the changes to conf that you've made.

---

