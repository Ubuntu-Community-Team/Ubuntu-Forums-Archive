---
title: "Help Installing Apache"
date: 2007-07-22
forum: General Help
---

### Post by pc_michael on 2007-07-22
Hi!  I'm a n00b so this is probably a stupid question.

I can't seem to install Apache on Ubuntu Feisty.  I type sudo apt-get install apache and it downloads the packages and begins to install them, but then gives all sorts of error messages.  I tried this with Apache2 as well, and get similar problems.  Here's the full output.

```
mjordan@ubuntu:~$ sudo apt-get install apache
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
apache is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up apache (1.3.34-4.1) ...
Not replacing deleted config file /etc/apache/httpd.conf
Not replacing deleted config file /etc/apache/srm.conf
Not replacing deleted config file /etc/apache/access.conf
Not replacing deleted config file /etc/apache/modules.conf
Can't open config file /etc/apache/httpd.conf.
No such file or directory
Can't open config file /etc/apache/httpd.conf.
No such file or directory
/usr/share/apache/postinst.common: line 12: /etc/apache/httpd.conf: No such file or directory
/usr/share/apache/postinst.common: line 12: /etc/apache/httpd.conf: No such file or directory
/usr/share/apache/postinst.common: line 12: /etc/apache/httpd.conf: No such file or directory
/usr/share/apache/postinst.common: line 12: /etc/apache/httpd.conf: No such file or directory
grep: /etc/apache/httpd.conf: No such file or directory
 * Configuration syntax error detected, not starting/reloading...
fopen: No such file or directory
apache: could not open document config file /etc/apache/httpd.conf
                                                                         [fail]
invoke-rc.d: initscript apache, action "start" failed.
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I must be doing something wrong, but what?

---

### Post by zanglang on 2007-07-22
Your previous Apache install might have been a little messed up, try removing and reinstalling again? Make sure you remove any leftover packages as well if apt-get doesn't.
> sudo apt-get remove apache
sudo apt-get autoremove
sudo aptitude install apache
(Using Aptitude because it manages dependencies a little better than apt-get)

---

### Post by pc_michael on 2007-07-22
Thank you for the reply!

I followed your instructions, in the order you provided, but when it got to the last step, installing with aptitude, I still got the same set of error messages. :(

---

### Post by zanglang on 2007-07-22
Odd. After the 2nd step, is there still any files left in '/etc/apache'? (Or /etc/apache2)

---

### Post by pc_michael on 2007-07-22
apt-get remove *does* leave behind a few files in those directories.  I used to delete them before attempting to reinstall (I've been at this for a couple days), but no matter if I leave them or delete them, I still get the error messages.

---

### Post by zanglang on 2007-07-22
Try this:
> aptitude search apache
Remove any packages that has an 'i' in the left column with
> sudo aptitude purge <names of all listed packages>
Now reinstall with
> sudo aptitude reinstall apache
If it fails with the same error, try this first before installing
> sudo touch /etc/apache/httpd.conf /etc/apache/srm.conf /etc/apache/access.conf /etc/apache/modules.conf

---

### Post by pc_michael on 2007-07-22
Thank you for the continued help!  The search showed **apache-common** and **apache2-utils** with an i next to them, so I purged them and tried the **aptitude reinstall** command.  It said apache wasn't installed, so it wouldn't be reinstalled.  So I used the normal install command and this time got a different set of errors:

```
mjordan@ubuntu:/etc/apache$ sudo aptitude install apache
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  apache-common apache2-utils
The following packages have been kept back:
  mt-daapd
The following NEW packages will be installed:
  apache apache-common apache2-utils
0 packages upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/1583kB of archives. After unpacking 4452kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package apache2-utils.
(Reading database ... 133488 files and directories currently installed.)
Unpacking apache2-utils (from .../apache2-utils_2.2.3-3.2build1_i386.deb) ...
Selecting previously deselected package apache-common.
Unpacking apache-common (from .../apache-common_1.3.34-4.1_i386.deb) ...
Selecting previously deselected package apache.
Unpacking apache (from .../apache_1.3.34-4.1_i386.deb) ...
 * Stopping apache 1.3 web server...                                            No process in pidfile `/var/run/apache.pid' found running; none killed.
                                                                         [ OK ]
Setting up apache2-utils (2.2.3-3.2build1) ...
Setting up apache-common (1.3.34-4.1) ...

Setting up apache (1.3.34-4.1) ...
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up apache (1.3.34-4.1) ...
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 apache
```

So I tried starting over, touching those files first, but I still get those new errors.

---

### Post by zanglang on 2007-07-22
Might be something wrong with its packaging. At least there's no scary error messages now? ;) Now try
> sudo apt-get install -f

---

### Post by pc_michael on 2007-07-22
Holy moley, I don't know what happened there, but **sudo apt-get install -f** somehow trashed KDE (which I was running) and I lost a bunch of my preferences. :/

I think I'm just going to do the "Windows thing" and wipe my system and start over with a clean Ubuntu install.  Thank you for all the help, I really appreciate it. :)

---

### Post by zanglang on 2007-07-23
Ouch! How did that happen? Sorry to hear that. :(

---

