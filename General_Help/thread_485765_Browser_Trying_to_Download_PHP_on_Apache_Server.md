---
title: "Browser Trying to Download PHP on Apache Server"
date: 2007-06-27
forum: General Help
---

### Post by flashinglemur on 2007-06-27
Good day.  I'm running Feisty Fawn, with Apache2, Perl, PHP, etc.  My perl scripts work fine.  When I try to access my php script from my browser, it tries to download it.  I have done the following from following forums, listservs et al...

To my httpd.conf:

AddType application/x-httpd-php .php
AddType application/x-httpd-php .php3
AddType application/x-httpd-php .phtml

LoadModule php5_module        modules/libphp5.so (by the way, it balked at this line and I had to take it out because of this message - cannnot load /usr/local/apache2/modules/libphp5.so into server: /usr/local/apache2/modules/libphp5.so cannopt open shared object file: No such file or directory)


I also ruan sudo apt-get install libapache2-mod-php5

Also compiled Apache with the switch "--with-included-apr".

Other people have had this problem and some have not had a satisfactory solution.  I really need to work this problem out as man does not live by perl alone.

Any help resolving this problem would be greatly appreciated.

Thank you.

Mark

;)

---

### Post by az on 2007-06-27
> **flashinglemur said:**
> 

Also compiled Apache with the switch "--with-included-apr".

;)

Did you install apache2 from the repos?

What versions of apache and php do you have installed?

dpkg -l|grep apache
dpkg -l|grep php

---

### Post by flashinglemur on 2007-06-27
Apache downloaded from repository and compiled.

Apache 2.2.4
PHP - 5.2.3


> **az said:**
> Did you install apache2 from the repos?

What versions of apache and php do you have installed?

dpkg -l|grep apache
dpkg -l|grep php

---

### Post by az on 2007-06-27
Well, then you're on your own.

If you install the packaged from the repos, they work out-of-the-box.  Any reason you are avoiding the repos?

---

### Post by wirelessmonkey on 2007-06-27
In your httpd.conf you need to allow *.php as a a handler...     

        AddHandler application/x-httpd-php .php
and as a directory index item...
        DirectoryIndex index.php


else it will serve a .php file as a downloadable filetype.

---

### Post by flashinglemur on 2007-06-27
(oops, this was for AZ)
I mean, that's why I love Linux is that you can compile your source code.  I originally tried from the repos and it didn't work with PHP (Perl was just fine).  So I thought - maybe I'm missing some libs, might as well uninstall, then compile it. Still no luck.  Guess I am on my own. ](*,) Thanks anyhow.

> **az said:**
> Well, then you're on your own.

If you install the packaged from the repos, they work out-of-the-box.  Any reason you are avoiding the repos?

---

### Post by flashinglemur on 2007-06-27
Thanks for your suggestions.  I added "AddHandler" and "DirectoryIndex" to conf.  Stop and Start.  D@mn thing is still trying to d/l.  I guess what I'm wondering is why AddHandler cgi-script .cgi is remmed out, yet that works fine.

> **wirelessmonkey said:**
> In your httpd.conf you need to allow *.php as a a handler...     

        AddHandler application/x-httpd-php .php
and as a directory index item...
        DirectoryIndex index.php


else it will serve a .php file as a downloadable filetype.

---

### Post by az on 2007-06-27
> **flashinglemur said:**
> (oops, this was for AZ)
I mean, that's why I love Linux is that you can compile your source code.  I originally tried from the repos and it didn't work with PHP (Perl was just fine).  So I thought - maybe I'm missing some libs, might as well uninstall, then compile it. Still no luck.  Guess I am on my own. ](*,) Thanks anyhow.

Sure you can benefit from compiling from source, but you lose a lot on security updates.  Are you ready to subscribe to the apache, php, perl and Mysql maililng lists and will recompile from source every time a security vulnerability shows up?  It is far more practical to just keep up to date with the repos.

As well, everyone is on the same page.  When you install from the repos, the default configurations are the same and pinpointing the problem is a lot easier.

---

### Post by wirelessmonkey on 2007-07-06
Which version of Apache did you compile? When running the ./configure did you include --with-php=/path/to/php5 ?  Apache doesn't compile the php5.so module by default, I believe.

---

