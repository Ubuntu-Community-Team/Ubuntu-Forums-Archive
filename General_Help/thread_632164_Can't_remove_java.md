---
title: "Can't remove java"
date: 2007-12-05
forum: General Help
---

### Post by schmildo on 2007-12-05
I started havign dpenendancy issues so i wanted to remove all of the different bits of java and start again, but it wont let me, synaptic package manager returns:

E: sun-java6-bin: subprocess pre-removal script returned error exit status 2


and apt-get says:

ubuntu@ubuntu:~$ sudo apt-get remove sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-names python-twisted-core python-psyco
  libglitz-glx1 python-twisted-web python-twisted-runner python-twisted-mail
  python-twisted-lore python-twisted-conch python-twisted-news
  python-twisted-words libglitz1 python-twisted python-wxversion
  python-wxgtk2.6 python-twisted-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  sun-java6-bin
0 upgraded, 0 newly installed, 1 to remove and 36 not upgraded.
Need to get 0B of archives.
After unpacking 79.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 107605 files and directories currently installed.)
Removing sun-java6-bin ...
update-binfmts: warning: /var/lib/binfmts/sun-java6 does not exist; nothing to
do! 
update-binfmts: exiting due to previous errors 
dpkg: error processing sun-java6-bin (--remove):
 subprocess pre-removal script returned error exit status 2
No theme index file in '/usr/share/icons/sun-java6.png'.
If you really want to create an icon cache here, use --ignore-theme-index.
Errors were encountered while processing:
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

What do I do?

---

