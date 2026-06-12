---
title: "apt-get failed install cleanup?"
date: 2008-02-18
forum: General Help
---

### Post by fritogotlayed on 2008-02-18
Alright...  I tried to remove an irc daemon I had installed on a system oh so long ago (~3 months). I did the common "sudo apt-get remove rageircd" and it failed. After searching google for about an hour and looking around here for 30 minutes-ish I'm at my end. Is there any way to roll back a failed install? I can't exactly drop the machine and re-install as its running wiki / svn / forums / etc...

Console output : 

malline@bluenose:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up rageircd (2.0.1-5) ...
Adding system user
Warning: The home dir you specified already exists.
Allowing use of questionable username.
The user `Debian-rageircd' already exists as a system user. Exiting.
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "start" failed.
dpkg: error processing rageircd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 rageircd
E: Sub-process /usr/bin/dpkg returned an error code (1)



I also tried using "remove -f" but that had no help. Thanks much ahead of time.

---

### Post by fritogotlayed on 2008-02-18
I'm sorry... but do I have this in the wrong area?

---

### Post by fritogotlayed on 2008-02-18
Tried removing the user that the install created along with removing the "etc/rageircd" directory (-r -f). autoremove started the install configuration again. Anyone have any ideas whats up with that?

---

### Post by fritogotlayed on 2008-02-18
Pain in the rump!  

I finally found something that fixed it for me. 

[http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)

The last post on the page worked for me.  Did a "sudo rm rage*" then ran "sudo apt-get autoremove" twice and all was happy.

---

