---
title: "Backup - What to Exclude."
date: 2013-12-12
forum: General Help
---

### Post by hashky on 2013-12-12
I am using CrashPlan to backup Ubuntu 12.04.  CrashPlan is a file backup.  I am most concerned about my configuration files and packages that I have installed over the last year and one-half.

I know that I should be able to exclude cache and temporary files.  I have an exclude option in my configuration of Crash Plan.  Where are they? How would I go about excluding the tmp, temp, and cache files, without deleting the good files (i.e. template), etc.

---

### Post by Kirboosy on 2013-12-13
Is there a GUI install on your system for CrashPlan? There are two modes that it can run in. Headless and GUI. Headless would be for a server that doesn't have a traditional desktop and command line only access. GUI on the other hand should provide you a point and click interface to set everything up.

[Configuring a Headless Client]("http://support.code42.com/CrashPlan/Latest/Configuring/Configuring_A_Headless_Client")
[Crashplan GUI Menu]("http://support.code42.com/CrashPlan/Latest/Getting_Started/General")

Hope that helps!
~Caboose

---

### Post by hashky on 2013-12-13
I am using the GUI.

Under
Settings
Backup
Filename Exclusions -> Configure

This opens a Tab
Backup Exclusions:
It has "Regular Expression" that is unchecked and blank.

In the Windows version is has 
.log
.bak
as files to exclude.

I would like to exclude files that I will not need when I upgrade to Ubuntu 14.04.

I backup 2 computers; Ubuntu 12.04 and Windows 7 to a Linux Mint 16 computer.  I also backup the Windows computer to the CrashPlan Cloud.

hashky

---

### Post by oldfred on 2013-12-14
I use rsync and backup primarily /home. But I manually copy any /etc files I edit into /home to have those customize files, run a new dpkg export of installed apps and a bootinfo script to document system.

I assume I will do a new install so I do not back up Ubuntu system. Where with Windows you may need a full image as reinstalls may not be so easy. I have updated my exclude & includes based on the additional links.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

            Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by SeijiSensei on 2013-12-15
Here's my standard list of exclusions when running rsync ("rsync --exclude-from=/path/to/exclude/file"):

```

proc/
sys/
dev/
tmp/
/old/
bak
Temp
backup
pgsql/data/base
lib/mysql
quarantine/
SpamAssassin-Temp
usr/share/doc
usr/man/
usr/local/man
usr/share/man
usr/share/doc
var/spool/squid

```

A couple of these are related to software I run; the "quarantine/" directory is created by [MailScanner](http://www.mailscanner.info) and "var/spool/squid" belongs to the Squid proxy cache.  I don't back up the binary images of SQL servers like Postgres or MySQL; I run those programs' "dump" routines each night to create plain-text backups of the databases.

---

### Post by hashky on 2013-12-15
Many thanks to all.  I have attached a file that contains a screen shot from CrashPlan.  I didn't include the hidden files because I don't know how to get the long list into this forum.  My backup went from 6.3GB to 5.9GB.  This is very small compared to the image backups I did by booting into Windows and using Acronis.
I am sure if I worked at it, I could reduce the size even further.  Better safe that sorry.  

The hard drive on this computer failed about a month ago.  I bought a new one.  It took a while but I was able to restore all partitions, including ext4.  I had to work on the grub configuration little bit.  I plan to upgrade to 14.04 LTS next year.  So I will need a file backup.

One day when I have a lot of time, I will get SAMBA and all the permissions set on my computers (Ubuntu 12.04, Linux Mint 16, and Windows 7).  Then I can learn how to use rsync.  Until then, I have found CrashPlan to be the easiest method.

---

