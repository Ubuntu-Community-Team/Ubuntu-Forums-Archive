---
title: "No default file in /etc/apache2/sites-available"
date: 2015-01-07
forum: General Help
---

### Post by cearlp on 2015-01-07
While trying to install mod_python following the instructions found in another post in this forum, everything seems okay until I try to edit the file /etc/apache2/sites-available/default.
There is no such file, only 000-default.conf and default-ssl.conf
Editing both of these files to have the AddHandler, PythonHandler and PythonDebug statements cause nothing 'bad' to happen, but Apache will still not process .py files in /var/www/html. The files types html and php are okay. 
Is there something I missed when first installing Apache2? It was done months ago and things have been fine until I started to use python.

---

### Post by Doug S on 2015-01-07
I assume you are using a recent version of Ubuntu, I think 14.04 or later. And yes, what used to be called default is now called 000-default.conf.
I'm not sure about your actual problem though.

Edit: perhaps give us the link to what you are using as a reference.

---

### Post by cearlp on 2015-01-08
You assume correctly. I am using 14.04 (with updates). I am trying to get .py files to work using Firefox as the browser and read in posts that mod_python is needed to be installed in Apache.
As I stated, I was following a post about installing mod_python and made changes to 000-default instead of the default file listed in the installation post but still .py files would not be processed.
The error states that it doesn't know what application to use and suggests using gedit to open the file.
The mod_python install post was started by superpink99 in July 2009 in Programming Talk forum.

---

### Post by Doug S on 2015-01-08
> **cearlp said:**
> The mod_python install post was started by superpink99 in July 2009 in Programming Talk forum.For other readers. I suspect the referral is to [this thread]("http://ubuntuforums.org/showthread.php?t=1193983").

---

### Post by dragonfly41 on 2015-01-09
If you are still having problems running python on apache2 then here are some notes.

I suggest that you create a virtualhost site specifically for your python development DocumentRoot.

Let's name it "python.dev.conf" so that [http://python.dev/hello.py](http://python.dev/hello.py) should work.

You will need to understand the basics of virtualhosts and their configuration.

Here is one blog to help ...

[https://bhou.wordpress.com/2011/11/28/how-to-install-and-configure-mod_python-in-apache-2-server/](https://bhou.wordpress.com/2011/11/28/how-to-install-and-configure-mod_python-in-apache-2-server/)

...

In /etc/apache2/sites-available folder create a new file python.dev.conf.

This assumes that your DocumentRoot is ..
/var/www/html/virtualhosts/python.dev

but if you only have one virtual host configured it can be simplified to ...

/var/www/html/python.dev

I have multiple virtualhosts and I place them in /var/www/html/virtualhosts/.

```

<VirtualHost *:80>
ServerName python.dev
DocumentRoot "/var/www/html/virtualhosts/python.dev"
DirectoryIndex index.html index.php index.py

<Directory  "/var/www/html/virtualhosts/python.dev">
    Options +Indexes +FollowSymLinks -MultiViews +ExecCGI
    AllowOverride None       
    Require all granted
    
    AddHandler mod_python .py
    PythonHandler mod_python.publisher
    PythonDebug On
</Directory>

   ErrorLog ${APACHE_LOG_DIR}/error-python.dev.log
    # Possible values include: debug, info, notice, warn, error, crit, alert, emerg.    
    LogLevel debug
    
</VirtualHost>

```

Now note that this uses directive "Require all granted" which applies for apache 2.4x.

Having created this virtualhost config file you must enable it and load it so that it appears as symlink in /etc/sites-enabled.

Use the command ... sudo a2ensite python.dev

The disable site command is ... sudo a2dissite python.dev ... should you wish to disable any site.

sudo a2dissite 000-default will disable the 000-default site.

After editing any config files you must reload using this command.

sudo service apache2 reload

and you can restart apache with this command

sudo service apache2 restart

...

In /var/www/html/virtualhosts/python.dev folder (DocumentRoot for the virtualhost) you can place your python files.

Create a test file ... hello.py ... in pure python as follows.

```

def index(req):
    return "Hello World! This is a python script!";

```

save this file and ensure that it has apache2 ownership ... www-data .. not root.

Now if testing your python apps in localhost (127.0.0.1) add your virtualhost servername (python.dev) to /etc/hosts file

127.0.0.1       python.dev

With luck you should now be able to run ...

[http://python.dev/hello.py](http://python.dev/hello.py)

---

### Post by cearlp on 2015-01-09
Thanks dragonfly41, things went exactly as you outlined. A question though -- why doesn't adding the AddHandler, PythonHandler and PythonDebug statements to the 000-default.conf file allow localhost to display the same .py file  when it is located in the localhost DocumentRoot /var/www/html?

---

### Post by dragonfly41 on 2015-01-09
000-default.conf is usually reserved for localhost usage and as a template for other config files to customise virtualhosts in /etc/sites-available.

If you retain python.dev.conf as suggested then you can disable 000-default.conf by

sudo a2dissite 000-default.

If you prefer to run your python in the default config then remove python.dev.conf just edit the 000-default.conf file as below ...

```

<VirtualHost *:80>
ServerName localhost
DocumentRoot "/var/www/html"
DirectoryIndex index.html index.php index.py

<Directory  "/var/www/html">
    Options +Indexes +FollowSymLinks -MultiViews +ExecCGI
    AllowOverride None       
    Require all granted
    
    AddHandler mod_python .py
    PythonHandler mod_python.publisher
    PythonDebug On
</Directory>

   ErrorLog ${APACHE_LOG_DIR}/error-python.log
    # Possible values include: debug, info, notice, warn, error, crit, alert, emerg.    
    LogLevel debug
    
</VirtualHost>

```


and include 127.0.0.1    localhost in /etc/hosts

---

### Post by cearlp on 2015-01-09
Thanks again dragonfly41. After getting a python.dev site to work I disabled it and enabled the 000-default site after editing the default.conf file to have a 'Require all granted' statement in it but I failed to insert the Directory block.
This doesn't work because the 'Require ...' statement in invalid in a VirtualHost block.
I edited the 000-default.conf file to have the statements you indicated in your previous reply but I still get the window that wants to know which app I want to use to open it.
After enabling both site conf files, using the virtual host python.dev as the URL still works.

---

### Post by dragonfly41 on 2015-01-10
Here are some ideas for troubleshooting.

(1) check version of apache2 installed .. is it version 2.4?
[INDENT]apache2 -v
[/INDENT]

(2) check virtualhost(s) configuration[INDENT]apachectl -S     
[/INDENT]

(3) check virtualhost(s) config files syntax[INDENT]apachectl -t 
[/INDENT]

(4) after any changes to virtualhosts sites-enabled config files run[INDENT]sudo service apache2 reload
sudo service apache2 restart
probably both are not necessary
[/INDENT]

(5) inspect ls /etc/apache2/sites-available[INDENT]ls /etc/apache2/sites-available
ls /etc/apache2/sites-enabled
[/INDENT]

(6) inspect and edit /etc/hosts[INDENT]sudo gedit /etc/hosts
[/INDENT]

```

127.0.0.1        localhost
127.0.0.1        python.dev

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

(7) check ownership of files recursively under /var/www/html are www-data

(8) for good measure to reload browser cache use Cntrl+F5

(9) inspect virtualhost(s) log files after running sites[INDENT]sudo gedit /var/apache2/error-python.log
sudo gedit /var/apache2/error-python.dev.log
[/INDENT]


Refer to further notes here

[http://superuser.com/questions/627441/recent-apache2-update-broke-virtual-host-and-new-error-on-restart-or-starting](http://superuser.com/questions/627441/recent-apache2-update-broke-virtual-host-and-new-error-on-restart-or-starting)

---

### Post by cearlp on 2015-01-10
Ok, I found an error in the default.conf file,,,(a - instead of an _).
However, I now get a Mod_Python Error.  A synopsis of the error is:
 ProcessorId:  3628
 Interpreter:   '127.0.1.1'
 ServerName: '127.0.1.1'
 .
 .
 .
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch
    default=default_handler, arg=req, silent=hlist.silent)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1229, in _process_target
    result = _execute_target(config, req, object, arg)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1128, in _execute_target
    result = object(arg)

  File "/usr/lib/python2.7/dist-packages/mod_python/publisher.py", line 213, in handler
    published = publish_object(req, object)

  File "/usr/lib/python2.7/dist-packages/mod_python/publisher.py", line 425, in publish_object
    return publish_object(req,util.apply_fs_data(object, req.form, req=req))

  File "/usr/lib/python2.7/dist-packages/mod_python/util.py", line 554, in apply_fs_data
    return object(**args)

TypeError: index() takes exactly 1 argument (0 given)


The error log shows no apparent error.
Other suggestions now?

---

### Post by dragonfly41 on 2015-01-10
Re: ServerName 127.0.1.1

Check that in /etc/apache2/apache2.conf

you have[INDENT]ServerName localhost
[/INDENT]

...

Have you used 127.0.1.1 instead of 127.0.0.1 in any of your configuration files in sites-available?

Can you run your python script from command line?

[later edit]

Place a hello.html file in the Document Root (next to hello.py) and test if that renders.

[later correction]

According to these docs

[http://www.debian.org/doc/manuals/debian-reference/ch05.en.html#_the_hostname_resolution](http://www.debian.org/doc/manuals/debian-reference/ch05.en.html#_the_hostname_resolution)

[http://serverfault.com/questions/363095/why-does-my-hostname-appear-with-the-address-127-0-1-1-rather-than-127-0-0-1-in](http://serverfault.com/questions/363095/why-does-my-hostname-appear-with-the-address-127-0-1-1-rather-than-127-0-0-1-in)

in fact you should have in /etc/hosts

127.0.0.1   localhost
127.0.1.1   python.dev

etc.

---

