---
title: "[SOLVED]how to remove chntpw:i386 (0.99.5-0+nmu1, 0.99.6-2)"
date: 2013-07-11
forum: General Help
---

### Post by rohit modee on 2013-07-11
hello,

i am a newbie to Linux. i am using ubuntu 12.04. i want to remove **chntpw**:i386 (0.99.5-0+nmu1, 0.99.6-2). 
i had installed it from other source but it was installed through ubuntu software center(i mean i got installer from a site and when double-clicked it it showed in ubuntu software center). 
i dont know how it got updated to its latest version which has a bug. 
now i cant remove it from ubuntu software center bcoz it wont allow me to. 
so now i checked log file to remove it but them it was installed (got updated) along with Commandline: aptdaemon role='role-commit-packages'.

so what should i do to remove chntpw or atleast downgrade chntpw to a stable version.

---

### Post by Bucky Ball on 2013-07-11
Welcome to the forums. It might help if you provide a link to the 'other source'.

---

### Post by rohit modee on 2013-07-11
[http://launchpadlibrarian.net/15221455/chntpw_0.99.5-0%2Bnmu1_i386.deb](http://launchpadlibrarian.net/15221455/chntpw_0.99.5-0%2Bnmu1_i386.deb)

this is the source from where i downloaded chntpw

---

### Post by Bucky Ball on 2013-07-11
Please provide exactly what you are attempting to do and why, along with any error messages you are getting when you try to uninstall. You say you can't uninstall but don't say what's happening. Try and be specific. ;)

---

### Post by rohit modee on 2013-07-11
i want to remove chntpw. ubuntu software center is not allowing to remove

[IMG]http://i43.tinypic.com/2aep0k5.png[/IMG]

---

### Post by uRock on 2013-07-11
In a terminal try the remove command.```
sudo apt-get remove chntpw
``` Copy and paste the output here.

---

### Post by rohit modee on 2013-07-11
rohit@rohit-VPCEB44EN:~$ sudo apt-get remove chntpw
[sudo] password for rohit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  chntpw
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 147 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 185318 files and directories currently installed.)
Removing chntpw ...
Processing triggers for man-db ...
rohit@rohit-VPCEB44EN:~$

---

### Post by uRock on 2013-07-11
Is that what you got when you ran my command?

---

### Post by rohit modee on 2013-07-11
yes

---

### Post by uRock on 2013-07-11
Looks to be uninstalled correctly now.

---

### Post by rohit modee on 2013-07-11
what is processing triggers to man-db....

---

### Post by uRock on 2013-07-11
That is the package manager updating the database. It does that with the installation and removal of software's.

---

### Post by Bucky Ball on 2013-07-11
Good you got it solved. Please mark thread as solved by following the link in my signature and post a new thread for any further questions/issues/problems (the title of this thread won't relate). Thanks and good luck.

---

### Post by rohit modee on 2013-07-12
**&#8203;**

---

