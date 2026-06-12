---
title: "[SOLVED] Please help me remove slim"
date: 2007-03-19
forum: General Help
---

### Post by DougieFresh4U on 2007-03-19
I need to remove Slim as it keeps causing system crash. I have tried to remove from Synaptic but it comes back with error, so I tried terminal and get the following::[B]dougie@DougiesToyBox:~$ sudo apt-get remove slim
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  slim
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 496kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 145497 files and directories currently installed.)
Removing slim ...
Terminated
invoke-rc.d: initscript slim, action "stop" failed.
dpkg: error processing slim (--remove):
 subprocess pre-removal script returned error exit status 143
slim: Stale lockfile found, removing it
Errors were encountered while processing:
 slim
E: Sub-process /usr/bin/dpkg returned an error code (1)
dougie@DougiesToyBox:~$[/B]

---

### Post by Kateikyoushi on 2007-03-19
I guess you stopped the process already, seems it tries to stop it and if can't won't proceed with the uninstall.

---

### Post by DougieFresh4U on 2007-03-19
> **Kateikyoushi said:**
> I guess you stopped the process already, seems it tries to stop it and if can't won't proceed with the uninstall.[B]
dougie@DougiesToyBox:~$ sudo apt-get install slim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
slim is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dougie@DougiesToyBox:~$ sudo apt-get remove slim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  slim
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 496kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 145497 files and directories currently installed.)
Removing slim ...
Terminated
invoke-rc.d: initscript slim, action "stop" failed.
dpkg: error processing slim (--remove):
 subprocess pre-removal script returned error exit status 143
slim: Stale lockfile found, removing it
Errors were encountered while processing:
 slim
E: Sub-process /usr/bin/dpkg returned an error code (1)
dougie@DougiesToyBox:~$[/B] 


I don't understand as already this evening system has crashed with crash report coming up saying caused by slim. So how do I get rid of slim? Also Synaptic still shows  Slim box checked in green

---

### Post by DougieFresh4U on 2007-03-20
I'm still trying to remove slim as crash report keeps popping up and same out put from terminal as posted above  :mad: :mad:

---

### Post by DougieFresh4U on 2007-03-26
Please, some one help me get rid of Slim. Terminal won't let me and Synaptic won't let me. Please help:mad: :mad: :mad: :mad: :mad:

---

### Post by DougieFresh4U on 2007-03-27
Please, any one out there?                                                                                                                                       dougie@DougiesToyBox:~$ sudo apt-get remove slim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  slim
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 496kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 147587 files and directories currently installed.)
Removing slim ...
Terminated
invoke-rc.d: initscript slim, action "stop" failed.
dpkg: error processing slim (--remove):
 subprocess pre-removal script returned error exit status 143
slim: Invalid theme in config: green_glass
slim: Invalid theme in config: orange_glass
slim: Stale lockfile found, removing it
Errors were encountered while processing:
 slim
E: Sub-process /usr/bin/dpkg returned an error code (1)
dougie@DougiesToyBox:~$

---

### Post by DougieFresh4U on 2007-03-27
Help!!!!

---

### Post by sudhansh on 2007-07-14
do ctr-alt+f6 -> kill slim (by sudo killall slim or sudo /etc/init.d/slim stop). now remove by sudo apt-get remove --purge slim.

---

### Post by picpak on 2007-09-22
> **sudhansh said:**
> do ctr-alt+f6 -> kill slim (by sudo killall slim or sudo /etc/init.d/slim stop). now remove by sudo apt-get remove --purge slim.

Didn't work. :(

Is there any way to properly remove slim?

---

### Post by picpak on 2007-09-22
I FIGURED IT OUT!

First, open up a terminal and enter in the following:

```
sudo rm -r /var/lib/dpkg/info/slim.prerm
```

This removes that pesky pre-removal script.

Then enter in

```
sudo apt-get --purge slim
```

to remove slim off the system.

Hope that helps!

---

### Post by atlfalcons866 on 2007-10-17
THANK YOU:KS this helped me with a problem with the annoying virtualbox problem i had.

---

### Post by bodhi.zazen on 2007-10-17
> **picpak said:**
> I FIGURED IT OUT!!

Did you file a bug report ? If not, please consider it :

[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

