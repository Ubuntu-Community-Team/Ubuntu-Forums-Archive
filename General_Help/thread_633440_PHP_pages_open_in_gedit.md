---
title: "PHP pages open in gedit"
date: 2007-12-06
forum: General Help
---

### Post by CreepinJesus on 2007-12-06
Usual story it seems, after looking at the list of similar topics.  Firefox wants to save the file to disk when I try to open PHP files.  Let's try and make this the first thread that this problem actually gets solved in :).

---

### Post by tbfr on 2007-12-06
Where exactly is the problem? It's perfectly fine that PHP files are opened in gedit as far as I am concerned .

php files contain server side code which means you can not view them in a browser like you can view html files.

Even if you install a webserver with php support and have a php file in your webservers folder you cannot open this file in Firefox via the file menu. You have to enter a link to the file starting with http:// into the location bar. The webserver will respond, read and interpret the php file, execute the php commands found, make database or file operations as necessary and show you the result.

EDIT:
In order to avoid any misunderstandings, if you are reading this you are probably viewing it via the URL [http://ubuntuforums.org/showthread.php?t=633440](http://ubuntuforums.org/showthread.php?t=633440). The server shows you the php generated HTML code and not the php source code. So if you want to save this page onto your harddrive to open it in Firefox sometime later, just make sure you save this file as showthread.html not showthread.php.

---

### Post by NorthPunk on 2007-12-06
I have been using Ubuntu for a few days (great system), But i am also having the same problem with php.

I use Webmin, installed Gutsy Gibbon LAMP server, and it is suppoed to come with PHP5 installed.  It did but it isn't encoding it properly either, no matter how many times i reinstall php or apache2

---

### Post by CreepinJesus on 2007-12-06
I've also tried installing the apache2 thing and php5 but they still don't open properly.  I'm trying to install the dotproject server - it says to browse to your install directory, to the install.php page in your browser.  But with Firefox being the bad IE rip off it is, its not helping much.

---

### Post by tbfr on 2007-12-06
Did you read the guides and the help?
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[https://help.ubuntu.com/7.10/server/C/web-servers.html]("https://help.ubuntu.com/7.10/server/C/web-servers.html")

@NorthPunk
Did you install the php5 package and did you enable php support with the command 'a2enmod php5 '.  Can you find steps in the guide you didn't follow?

@CreepinJesus
I am quite sure this has nothing to do with Firefox at all. What is your install directory and what happens if you type localhost into the browsers location bar? Are you aware that browsing to your install directory means entering something like [http://localhost/myinstallationpath/install.php](http://localhost/myinstallationpath/install.php) into the location bar? Did you too read the help pages?

---

### Post by CreepinJesus on 2007-12-06
Yep - browsed the the directory.  It wasn't an install directory because its not installed yet - its just sitting in a folder in my Downloads area, mainly because it won't install.

---

### Post by CreepinJesus on 2007-12-06
Right I've followed all the instructions on that Apache page...not that I wanted an SQL Server or anything...

I enabled php5 support, restarted the apache2 service, still not working.  Just restarting the entire computer now...

The testphp.php file load up ok, so I guess its working to some extent.

---

### Post by dagnabit dang doohickey on 2007-12-06
What's the address you entered in the Firefox's location bar?
And, in what directory did you put dotproject?

---

### Post by CreepinJesus on 2007-12-06
I entered: /home/[name]/Desktop/dotproject/install/index.php

Still not working.  There's a surprise.

I just tried installing dotproject on my Windows computer instead - took about 5 minutes and working perfectly.  That'll make you all cringe.

---

### Post by tbfr on 2007-12-06
> Just restarting the entire computer now...
That's a Windows invention which isn't needed.

This is not the kind of installer you are normally using when installing an application. Installing in this case doesn't mean you can double click the install.php file and something will install. Rather you will have to start by copying the dotproject folder into your webservers root folder which usually is /var/www/.

But before you do this, i would recommend to carefully read the guides, then get familiar with starting/stopping the webserver, learn about the document root directory of your webserver and relative paths, try to create a simple php page yourself, read about mysql (you will probably need it next) and only then come back to your original problem by start reading the instructions on how to install dotproject on the projects website.

---

### Post by dagnabit dang doohickey on 2007-12-06
> I entered: /home/[name]/Desktop/dotproject/install/index.php

And, there's your problem.

You need to put the dotproject directory somewhere under your web server's root directory so the page can be *served*.

The address you enter for the dotproject installer should be something similar to: ```
http://localhost/dotproject/install/index.php
``` or ```
http://your.domain.com/dotproject/install/index.php
```

---

### Post by NorthPunk on 2007-12-06
I have a phpinfo file that is supposed to list every setting my server has (which i am sure everyone is familiar with)... it works when i used to use XP last week.  But since installing ubuntu (which i am very much in love with), it tries to saev it.  

according to all tutorials and searches my settings are done properly but it still tries to save (html itself displays so i know apache directories are set up properly)



edited : one of the links tbfr gave actually helped fix the problem.  all the modules were installed (using synaptic) but the modules weren't loaded into available.  thanks

---

