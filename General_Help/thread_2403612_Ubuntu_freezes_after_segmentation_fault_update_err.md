---
title: "Ubuntu freezes after segmentation fault update error"
date: 2018-10-13
forum: General Help
---

### Post by petran79 on 2018-10-13
I use 16.04 MATE. I did a simple sudo apt-get update and I saw a segmentation fault error after the installation of some files. Tried restarting Ubuntu and it froze. Tried recovery mode, same thing. Can not even go to command prompt. 
Only GRUB edit menu is possible. Tried adding "Single" command to Linux line, same.

I get a message that kernel failed to synchronize before the freeze. 

Tried updating to 18.04 MATE via USB. While it detects the 16.04 partition, it refuses to install over there, even though there is enough free space. Instead it picks my external USB drive. But even so, it does not offer the option to upgrade and keep most of the installed applications. Just the user settings and documents.
Only way to install to the existing ext4 partition is to erase the data completely. 

I spent hours and hours setting up that environment and looking for PPAs and compiling apps. If all that is lost I doubt I will bother with any Linux distribution anymore.
First time I see such a situation. At least in previous versions I was able to enter recovery mode for troubleshooting.

---

### Post by TheFu on 2018-10-13
My first guess is that you ARE out of storage.
df -h
df -i

Attempting to upgrade from 1 OS to another when there are package problems **NEVER, EVER**,  turns out well.  Fix the issues first.

Before doing any OS upgrade between versions, please, please make a know-you-can-restore backup.  ALWAYS.

Compiled apps usually need to be recompiled for the new OS.  That's why using repo versions or PPA versions are better. Plus they are updated whenever security issues are uncovered and we get those updates as part of our weekly patches.
For backing up other stuff like a list of installed packages, there is apt-mark or aptik.  If you backup /etc/, and you should, then you have the PPAs.

If it isn't out of space (inodes), then boot from alternate media and check the logs. Almost always, the log files have the info to say what is causing an issue. Just have to look at them. journalctl will let you look at logs and search by time and with regex for issues.  I usually find it easier just to mount the disk with /var/logs and use egrep.  But it doesn't matter how you choose to look at the logs.

---

### Post by petran79 on 2018-10-14
I used ext2explore on Windows and managed to have access to some logs though I am not sure if that is all

here is the apt term log, about the update crash that caused the issue

[URL="https://paste.ubuntu.com/p/WxBN427PrZ/"]https://paste.ubuntu.com/p/WxBN427PrZ/
[/URL]

kern.log

[https://paste.ubuntu.com/p/s37KPch4BR/](https://paste.ubuntu.com/p/s37KPch4BR/)

syslog

[https://paste.ubuntu.com/p/zjhFZCyZZD/](https://paste.ubuntu.com/p/zjhFZCyZZD/)

---

### Post by TheFu on 2018-10-14
** boot from alternate media and check the logs.**
Also please run those commands with the necessary storage mounted.

---

### Post by petran79 on 2018-10-14
Sorry, I am clueless about many of those details.
I will but my main issue is if it can be solved or if I will have to reinstall from scratch. If it is about finding the cause but it cant be solved, then I do not want to waste my time

OK I logged from USB stick. 

I can see the 16.04 separate partition and the var/log directory. I copied etc folder though some folders could not be copied due to permission issues.

My partition is on that folder: ubuntu-mate@ubuntu-mate:/media/ubuntu-mate/f79923f6-293d-40f5-a8aa-68f10ce152a0$

All the directories are there. How do I use journalctl though? Launching it brings the logs of the USB stick. It has thousands of lines. Even so I can not understand the logs and find the issue. 

Sorry this is far too advanced for me.

---

