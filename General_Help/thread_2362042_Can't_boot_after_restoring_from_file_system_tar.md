---
title: "Can't boot after restoring from file system tar"
date: 2017-05-23
forum: General Help
---

### Post by zoidberg2 on 2017-05-23
I created a script to take a complete back up of my Ubuntu 14.04 server file system, I then attached another blank drive to the Virtual Box VM, mounted it, then extracted the backup.tar.gz file to it. 
I tried to test it by powering down the server, removing te additional drive & mounting that to a new server as it’s primary boot but I get this error on boot,** Fatal: no bootable medium found! System Halted**


Does this mean I can’t use this method to keep a back up of my system that can be quickly restored?  
 
This is the script I created for the back up of the filesystem. 
[SIZE=3][FONT=arial] 
 
> #!/bin/bash
TIME=`date +%b-%d-%y`
FILENAME=backup-$TIME.tar.gz
SRCDIR=/
DESDIR=/mnt/backup
tar -cpzf $DESDIR/$FILENAME $SRCDIR

any ideas folks? [/FONT][/SIZE]

---

### Post by ajgreeny on 2017-05-23
Using tar to create a backup will do just that; produce a backed up archive, but as you have found it is not a bootable system in the archive, just a collection of the files etc etc previously on your system, but without the grub bootloader setup to boot your OS.

The easiest way to do what you want is probably [clonezilla]("http://www.clonezilla.org/") and with that you can create a live OS image to burn to a DVD or USB.

It is available as both a server and live edition and I suspect you need the live edition, though I have never used either of them so speak without personal experience.

---

