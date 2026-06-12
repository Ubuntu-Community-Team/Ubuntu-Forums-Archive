---
title: "Apache and user directory for web files"
date: 2015-01-31
forum: General Help
---

### Post by cosine2 on 2015-01-31
Hi. I've been working on this for a couple of days, and can't seem to find a complete answer. I have a Ubuntu server set up, running Apache, and want to use my user directory for housing my web files. I've read a thousand articles, and I either can't get them to work or it says that it's a security issue. I don't want a massive security problem because of this. I would like the files to be in my user directory because of how easy it is to move files to and from and things of that sort. I do NOT want to enable the userdir mod, because I do not want my username to be in the URL.

If I change the conf file in the available-sites directory, so that the DocumentRoot is to the appropriate directory (home/username/public_html), when I attempt to view the files I get the "You don't have permission to access / on this server" error. How do I allow access so that the web files are accessible but not create a security issue?

I found a tutorial on how to handle this by using links ([http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file)). If I have the DocumentRoot to the appropriate directory in the conf file, and then use these links:

```
sudo ln -s ../mods-available/userdir.conf userdir.conf
sudo ln -s ../mods-available/userdir.load userdir.load
```

Then I can access the files properly. He admits that there may be security issues with this (he doesn't seem to be sure), but this is by far the easiest way to get this to work.

Is this a security risk? Is there a better way? Thanks for any help.

Ubuntu Server 64 v 14.10
Apache/2.4.10

---

### Post by nerdtron on 2015-01-31
So in summary you don't want to put your web page files on the standard /var/www/html folder? The reason for this is that you are having problems uploading to that directory. So instead you want all the webpage files to be on your home folder for easy uploading.

Well it's a fair reason but not very much recommended.
1. I believe AppArmor prevents a certain application from accessing folders not designated for them. In your case, AppArmor will block apache from accessing your web page files in your home folder since Apache is only allowed to access /var/www/html. Same is true for other programs like mysql  which defaults to /var/lib/mysql.
2. I really recommend that you still use the /var/www/html to save you web page files. Just upload the files on your home directory, then SSH to the server, then manually move the files to /var/www/html folder. There are other ways on uploading files to a server, this is just one (lazy) way of them.
3. Don't use 14.10 as this ubuntu version will only be supported for 9 months. Use the LTS version which are supported for 5 years. Ubuntu 12.04 or Ubuntu 14.04 LTS.

---

### Post by yancek on 2015-01-31
What are the owner:group and permissions on your public_html directory?  You should have the apache user for the group (in Ubuntu www-data) and your user in the www-data group.

---

### Post by Lars Noodén on 2015-01-31
> **yancek said:**
> What are the owner:group and permissions on your public_html directory?  You should have the apache user for the group (in Ubuntu www-data) and your user in the www-data group.

That would be inadvisable to give the web server write access, so directories should not be owned by www-data except in special circumstances.  The purpose of www-data is to provide an unprivileged user for the web server to run as, so no other users should be in that group.  If a group is needed for *shared* directories then a custom group must be created instead.  

> **cosine2 said:**
> If I change the conf file in the available-sites directory, so that the DocumentRoot is to the appropriate directory (home/username/public_html), when I attempt to view the files I get the "You don't have permission to access / on this server" error. How do I allow access so that the web files are accessible but not create a security issue?

About the permissions for the DocumentRoot, from a filesystem perspective the folder and its contents only need to be readable by the web server.  What are the permissions for the /home, /home/username and /home/username/public_html directories?  755, 701 and 755 ?

Then from the web server perspective, you have to have permissions set for that [Directory](http://httpd.apache.org/docs/2.4/mod/core.html#directory)

```

<Directory /home/username/public_html/>
       [Require](http://httpd.apache.org/docs/2.4/mod/mod_authz_core.html#require) all granted
       Options Indexes FollowSymLinks
</Directory>

```

---

### Post by cosine2 on 2015-01-31
> **nerdtron said:**
> So in summary you don't want to put your web page files on the standard /var/www/html folder? The reason for this is that you are having problems uploading to that directory. So instead you want all the webpage files to be on your home folder for easy uploading.
That is exactly why, convenience only when using sftp clients etc., but I don't want to sacrifice security for not having to type in sudo.

> **nerdtron said:**
> Well it's a fair reason but not very much recommended.
1. I believe AppArmor prevents a certain application from accessing folders not designated for them. In your case, AppArmor will block apache from accessing your web page files in your home folder since Apache is only allowed to access /var/www/html. Same is true for other programs like mysql  which defaults to /var/lib/mysql.
2. I really recommend that you still use the /var/www/html to save you web page files. Just upload the files on your home directory, then SSH to the server, then manually move the files to /var/www/html folder. There are other ways on uploading files to a server, this is just one (lazy) way of them.
So basically moving things from this designated directory is a bad idea from a security standpoint. What about adding myself to the www-data group so that I can at least sftp files into the directory, but not delete them? Does setting up things in this way compromise security in any way?

> **nerdtron said:**
> 3. Don't use 14.10 as this ubuntu version will only be supported for 9 months. Use the LTS version which are supported for 5 years. Ubuntu 12.04 or Ubuntu 14.04 LTS.
Is it specifically bad to use 14.10, or is this just from a pure support perspective?

Thank you very much for your help.

---

### Post by cosine2 on 2015-01-31
> **Lars Noodén said:**
> About the permissions for the DocumentRoot, from a filesystem perspective the folder and its contents only need to be readable by the web server.  What are the permissions for the /home, /home/username and /home/username/public_html directories?  755, 701 and 755 ?

Then from the web server perspective, you have to have permissions set for that [Directory]("http://httpd.apache.org/docs/2.4/mod/core.html#directory")

```

<Directory /home/username/public_html/>
       [Require]("http://httpd.apache.org/docs/2.4/mod/mod_authz_core.html#require") all granted
       Options Indexes FollowSymLinks
</Directory>

```

The permissions are /home 755, /home/username/ 755, and home/username/public_html 775. The <Directory> code goes in the available-sites .conf file correct? I tried about a dozen variations on this code and options, including this version(which I tried again just to make sure), and I still get the "don't have permission" message.

Thank you very much for your help.

---

### Post by dragonfly41 on 2015-01-31
Here are a few extra points I've taken note of myself when recently configuring apache2 ...

(a) learn from apache docs how to use these commands

sudo a2ensite <config file in sites-available>
sudo a2dissite

since you must *enable* any site defined in sites-available

(b) inspect ls /etc/apache2/sites-available
sudo ls /etc/apache2/sites-available
sudo ls /etc/apache2/sites-enabled

(c) If you are testing apache in localhost 
 inspect and edit /etc/hosts
sudo gedit /etc/hosts

and ensure that you have
127.0.0.1 localhost
in /etc/hosts

(d) check your apache2 config files syntax
apachectl -t 

(e) check apache2 configuration
apachectl -S 

(f) after any changes to  sites-enabled config files (and other files) run
sudo service apache2 reload
sudo service apache2 restart
.. but probably both commands are not necessary
.. reload just reloads config files

(g) reload browser cache use Cntrl+F5

...

I would also enable error log .. using DEBUG mode for now.

---

### Post by nerdtron on 2015-01-31
> What about adding myself to the www-data group so that I can at least sftp files into the directory, but not delete them? Does setting up things in this way compromise security in any way?
Sure you can add your user to the www-data group and make the web folder permission writable for group users. It will be a bit of compromise. But just lock down ssh port on your network firewall to prevent any unauthorized ssh access. And as long as you are updated apache, I think running remote codes/exploit on your apache install will be very hard.

> 
Is it specifically bad to use 14.10, or is this just from a pure support perspective?
After 9 months, you won't be able to update the server or install any apps. And also people here won't be very willing to help on "end-of-life" versions.

---

### Post by Lars Noodén on 2015-02-01
> **cosine2 said:**
> The permissions are /home 755, /home/username/ 755, and home/username/public_html 775. The <Directory> code goes in the available-sites .conf file correct? I tried about a dozen variations on this code and options, including this version(which I tried again just to make sure), and I still get the "don't have permission" message.


Yes, it should go in the vhost configuration file found in  /etc/apache2/sites-available/ where the default vhost would be 000-default.conf

```

<VirtualHost *:80>
 ...
  <Directory /home/username/public_html>
    ...
  </Directory>
  ...
</VirtualHost>

```

From there, reload the configuration to see the changes.

```

sudo service apache2 restart

```

No changes in the web server actually take effect until the configuration is reloaded and that is mainly done by restarting Apache2.  


Since you mention that not wanting to use sudo to edit as your motivation.  It might have been easier to just take ownership of the web server's original DocumentRoot instead.  If you are the only users, then it would have been like this:

```

chown -R cosine2:cosine2 /var/www/html/

```

If you are sharing write access, then it is done with groups and would have been something like this:

```

sudo addgroup webmasters

sudo gpasswd --add cosine2 webmasters

sudo chgrp -R webmasters /var/www/html

sudo find /var/www/html -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www/html -type f -exec chmod g=rws "{}" \;

```

---

