---
title: "backup program"
date: 2017-04-17
forum: General Help
---

### Post by rburkartjo on 2017-04-17
want to start backing up to dvd-rw what are the best programs to use. tks/

---

### Post by colin.p on 2017-04-17
I've been using Lucky Backup, well, forever and have had no issues with it. It's based on Rsync if I'm not mistaken. I, however, have not tried to back-up to DVDR, as my DVD recorder hasn't worked, well, forever either. It does back up to an infinite number of drives and do so on a regular basis (well actually only to four drives, but you get my meaning).

---

### Post by howefield on 2017-04-18
It really depends on what you want to back up and why.

I use Clonezilla to image partitions/disks and rsync to back up files/folders to other media.

---

### Post by RobGoss on 2017-04-18
+1 Howefield

I also use Clonezilla worKs well for me, if you need to restore your system here's another good application that allows you to set restore points for your system [https://launchpad.net/systemback](https://launchpad.net/systemback)

---

### Post by rburkartjo on 2017-04-18
how- i like to play too much have 7 types of distros on one partition and 5 more on another. sure i will eventually break something.

---

### Post by RobGoss on 2017-04-18
> **rburkartjo said:**
> how- i like to play too much have 7 types of distros on one partition and 5 more on another. sure i will eventually break something.

Make sure you have any important data backup just in case you do

---

### Post by howefield on 2017-04-19
> **rburkartjo said:**
> how- i like to play too much have 7 types of distros on one partition and 5 more on another. sure i will eventually break something.

In that case I'd still suggest Clonezilla which will back up individual partitions or disks. Two downsides that may or may not be important, first that you cannot (easily) browse the backups and extract files from the images and secondly the images "age" and cannot be incremented upon. With user data (which is on a separate partition) safely rsynced to several locations it takes around 4 minutes to re-image this laptops operating system so breaking the system is pretty much a non issue, getting back to the starting point is trivial enough..

I usually install a system and image it as, eg, zesty-base and re-image once there have been approx 100MB of updates, zesty-base-plus-one, ect, ect with "user" data being backed up daily with rsync.

---

### Post by rburkartjo on 2017-04-19
how thank you and everyone who made suggestions

---

### Post by oldrocker99 on 2017-04-19
I'm a fan of grsync, myself. It's a GTK front end for rsync.

---

