---
title: "Setting up a basic home server."
date: 2013-05-06
forum: General Help
---

### Post by chetanmadaan on 2013-05-06
Hi -

I for the first time in my life installed ubuntu on one of my local computers and i am lovin it already... i mean from a development point of view... till now i have been using Xampp on my windows which is really really slow when it comes to processing stuff... but ubuntu is like really a ferari so far.

I have some questions that may be really simple and dump for you guys...

- what is the best recommendation for setting up PHP, Mysql and Apache (I have already installed lampp and it's working great... but this will be more like a home shared server where i want to be able to provide access to other people over the workgroup in the same LAN connection and i don't think lampp has that good support for multiple users... atleast not for creating FTP accounts). we normally use cpanel/WHM on our servers and our client's server... but i don't think cpanel is good at ubuntu.
- How would **Webmin **work for us?
- shall i manually install PHP, Mysql & Apache and combine them togther??? if so, what FTP software shall i use?
- Also, lampp(Xampp) Doesn't come with a mail server like Exim or something... how do we go about setting that up?

Thanks to anyone responding :)

---

### Post by lykwydchykyn on 2013-05-06
**1:**
Just install the built-in Apache, PHP, and Mysql packages; they're very well maintained and almost any PHP library you need is available.  The easiest way to install it is to run: 
```

sudo tasksel

```

and select LAMP server from the selections.  I don't know about cpanel type options, though.

**2:**
Webmin works pretty well IME, but I don't know what you specifically want to use it for.  It's got a decent apache admin interface.

**3:**
Install Apache et al as above; if you activate the "userdirs" module in apache, everyone's ~/public_html folder will automatically map to [http://yourserver/~username/](http://yourserver/~username/).  You can also create symlinks to /var/www in everyone's folder if you don't like having the ~ in the URL.

As for FTP, the general consensus is **Just Don't**.  Your server should have openssh-server installed, which automatically provides SFTP access for any users on the system.  FileZilla or WinSCP or any FTP client worth its bits should be able to connect to SFTP, and this will be much more secure.  If you just must have old-school insecure FTP, go with ProFTPd.

**4:**
Easiest mail server to configure in Ubuntu (IMHO) is Postfix.  Install it, configure an SMTP relay, and you're pretty much ready to roll.

---

### Post by chetanmadaan on 2013-05-06
Sounds like it... never really thought about setting up system users and having them access to a specific folder.

one more thing... how about setting up SUPHP??

Because... there are issues with CMS system like Wordpress or Joomla. They need the file/folder owner to be apache to be able to write to directories and files... but, if Apache is owner and group... the ftp users won't be able to write the files?? any tips on this?

---

### Post by chetanmadaan on 2013-05-06
One more questions... i am hoping a simple one.
Now, this installed apache, php and mysql into /etc directory.

Can you tell me if this install phpmyadmin too?

if, so what directory.

---

### Post by lykwydchykyn on 2013-05-07
> **chetanmadaan said:**
> Sounds like it... never really thought about setting up system users and having them access to a specific folder.

one more thing... how about setting up SUPHP??

Because... there are issues with CMS system like Wordpress or Joomla. They need the file/folder owner to be apache to be able to write to directories and files... but, if Apache is owner and group... the ftp users won't be able to write the files?? any tips on this?

Have never needed SUPHP.  You can set the group ownership of these files to a made-up group like "webadmins", add write permissions to the group, then put everyone in the webadmins group.  SUPHP is overkill.

I can't remember if the LAMP server installs phpmyadmin, but that's as easy as:
```

sudo apt-get install phpmyadmin

```

Typicall it sets it up as [http://servername/phpmyadmin](http://servername/phpmyadmin)

---

### Post by chetanmadaan on 2013-05-07
worked like a Charm. 
# 1 I feel really great about this sudo apt-get thing... is there a directory that list everything that is avaliable and can be installed using apt-get??
# 2 I feel really really stupid on why i have been using windows all this time. I should have started using ubuntu/linux a long long time ago.

Thanks a bunch!

---

### Post by lykwydchykyn on 2013-05-07
> **chetanmadaan said:**
> worked like a Charm. 
# 1 I feel really great about this sudo apt-get thing... is there a directory that list everything that is avaliable and can be installed using apt-get??

You can use the apt-cache command to search through the package list for things; there's also "aptitude", which is an alternative front-end for APT.  It's got an interactive interface that lets you browse packages.

EDIT: I should warn, though, that you need to be careful mixing the use of apt-get and aptitude.  They don't track things quite the same way, and sometimes if you've been using the one, the other will want to uninstall or reinstall things you've added/removed with the other.  It's not a problem if you consistently use one or the other, though.

> 
# 2 I feel really really stupid on why i have been using windows all this time. I should have started using ubuntu/linux a long long time ago.


Well, you know what they say: the best time to plant a tree is 20 years ago.  The next best time is right now.

---

### Post by chetanmadaan on 2013-05-09
Thanks for your reply.

I was able to solve the user permission and apache not able to write files issue by simply adding the particular user to "www-data" group and that gives apache all the write permissions in that user directory.

Bottom line, this is really great apache and even though it's a local server for our inhouse development. i was able to configure Our Router to route port 80 to the ip address for the ubuntu marchine and it worked like a charm.

I was able to access everything outside the our network on an ip address (a dream come true for me).  

One more thing, i think  already know this... but this make this thing live on a domain name... only thing i would have to do would be add a A record to the domain to point to our external ip and than edit the httpd.conf file to accept connections from that domain name... right?

---

### Post by lykwydchykyn on 2013-05-09
> **chetanmadaan said:**
> 
One more thing, i think  already know this... but this make this thing live on a domain name... only thing i would have to do would be add a A record to the domain to point to our external ip and than edit the httpd.conf file to accept connections from that domain name... right?

Sounds right to me.

---

