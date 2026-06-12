---
title: "clvm - cluster manager error on feisty!"
date: 2007-04-04
forum: General Help
---

### Post by sanothay on 2007-04-04
Hi all,
Few days ago I upgraded ubuntu 6.10 to feisty. In fact I didn't really remember what I have done after, and now everytime I tried installing new packages or even updating I would always get this error message as pasted below. If anyone used to cope with the same or similar problems please help me or instruct to a useful pointer. Thanks. :) 

----------------------------------------------------------------------------------------------------------------------------
[COLOR="Orange"]root@cookie-desktop:/home/cookie# aptitude -f install sbackup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  sbackup 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.8kB of archives. After unpacking 475kB will be used.
Writing extended state information... Done
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe sbackup 0.10.3-0.1 [60.8kB]
Fetched 60.8kB in 3s (17.4kB/s) 
Selecting previously deselected package sbackup.
(Reading database ... 196938 files and directories currently installed.)
Unpacking sbackup (from .../sbackup_0.10.3-0.1_all.deb) ...
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Setting up sbackup (0.10.3-0.1) ...

Errors were encountered while processing:
 clvm
localepurge: Disk space freed in /usr/share/locale: 68K
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/COLOR]

---

### Post by sanothay on 2007-04-06
Sorry, just found out other had this issue before. Here is the solution:

[B]sudo rm /etc/init.d/clvm
and then
sudo apt-get remove clvm[/B]

Ref: [http://ubuntuforums.org/showthread.php?t=273236&highlight=clvm]("http://ubuntuforums.org/showthread.php?t=273236&highlight=clvm")

I have just tried it, and all works well now. However, it would be nice if anybody could explain a little more why this problem occurred and why those commands solved the problem.
Thanks. :lolflag:

---

### Post by hotani on 2007-04-26
had the same problem after accidentally installing clvm. Thanks for the fix!

---

