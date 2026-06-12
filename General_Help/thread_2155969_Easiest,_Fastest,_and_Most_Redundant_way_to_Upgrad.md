---
title: "Easiest, Fastest, and Most Redundant way to Upgrade?"
date: 2013-06-20
forum: General Help
---

### Post by ksaul on 2013-06-20
The question that has been asked, im sure, a billion times:

Currently on Ubuntu 12.04 LTS 64bit, and have been since it came out. Well now that there have been a handful of upgrades since than, I think its time to upgrade too (pretty much out of boredom). 

I was wondering if there is a way to copy/backup certain things on my system, so once I **FRESH** install, all I have to do is drag/drop the backups, and everything would be as if, nothing ever changed.

The items/programs that I am most concerned about (really, only concerned about) are:
 - my LAMP stack/setup which includes phpMyAdmin, ISPConfig, WebMin & UserMin, Drupal, Dovecot, and some others [of course Apache2, PHP5, mySQL]
 - Twonky Media Server
 - rTorrent server
 - VNC/Remote Desktop/SSH/File Sharing
 - FTP Server

Truthfully, everything else I could care less about, and if i "need" them, ill just install them later. I just want to backup the list about, wipe the partition and start from scratch - then restore the list. I have tried to do this before, by just creating an .ISO of the folders and files for the necessary items throughout the file-system, and then extracting them into the "fresh" file-system after install - but I dont know if I was missing items or what, but never had any success.

The LAMP stack and everything related/circled around it is just such a pain to re-build/install/configure/test/debug/launch.

---

### Post by nerdtron on 2013-06-20
I have tried it once with the Tomcat, Apache, PostgreSQL, and JAVA along with some other programs installed. It was a test server (nothing important to lose anyway, but some database were there). I was time for an upgrade from 10.04 so I just booted it up with 12.04 and started the installation.
The key here (on server and desktop install) is not to format the partition where the OS will reside. The only way to do this is to manual partitioning and assign the correct partition during the installation process. You'll recieve some warning about files being overwritten etc. but on my test server, all databases are still good.
Once you installed the base system, you just need to reinstall you applications. If you're lucky, just a few config files will be lost in the process but most data will be intact.

---

### Post by ksaul on 2013-06-20
maybe i didnt describe myself better.

I want to fresh install, like delete the entire partition. I have already created backups of my SQL databases; but I do not know how to properly backup my LAMP structure so that all I have to do is copy/paste them into the fresh-upgraded-filesystem and everything work as it does currently.

---

### Post by Habitual on 2013-06-20
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Check [http://kevinsaul.dyndns-at-home.com/](http://kevinsaul.dyndns-at-home.com/) for typos!

---

