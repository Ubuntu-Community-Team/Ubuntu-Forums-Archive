---
title: "New UUID and Labels"
date: 2013-10-16
forum: General Help
---

### Post by PJs Ronin on 2013-10-16
My method of upgrading is to clone my current production partition using the 'dd' command and then doing an upgrade by amending the sources.list in the new partition.   That way I can keep all the mods I've made and I retain a working environment to fall back on if the new upgrade goes south.

Unfortunately, the dd command copies everything verbatim, including the partition label and UUID.   If I try and change the new partition's UUID and label by using GParted on a bootable USB drive, the changes don't stick.   But, if I do the same process to the old partition the new UUID does stick.

Two questions.
1.   Is this expected behaviour or am I doing something wrong?
2.   Would rsync be a better way to go?

---

### Post by bab1 on 2013-10-17
> **PJs Ronin said:**
> My method of upgrading is to clone my current production partition using the 'dd' command and then doing an upgrade by amending the sources.list in the new partition.   That way I can keep all the mods I've made and I retain a working environment to fall back on if the new upgrade goes south.

Unfortunately, the dd command copies everything verbatim, including the partition label and UUID.   If I try and change the new partition's UUID and label by using GParted on a bootable USB drive, the changes don't stick.   But, if I do the same process to the old partition the new UUID does stick.

Two questions.
1.   Is this expected behaviour or am I doing something wrong?
2.   Would rsync be a better way to go?

1.  I would change the UUID on an unmounted partition only.  See [http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/]("http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/")

2.  The utility **dd** provides a* bit level copy* of everything.  The utility **rsync** is a *file level *copy of the files and directories.  In other words, they do not do the same thing.

I keep a separate partition of my /home directories and documentation of what and how I installed various tools and apps.  I don't upgrade I just install the new version of Ubuntu and preserver my home partition.  I have never had a failure from Ubuntu 6.06 (Dapper) on.

I do keep of line backups of all my data using scripted rsync routines.

---

### Post by PJs Ronin on 2013-10-17
ty for your response
> **bab1 said:**
> 1.  I would change the UUID on an unmounted partition only.  See [http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/](http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/) 

All the partitions are unmounted when I boot from a USB.   My problem is getting a label/UUID change to stick on the new partition.   Perhaps I should be looking at a bug report?

> 2.  The utility **dd** provides a* bit level copy* of everything.  The utility **rsync** is a *file level *copy of the files and directories.  In other words, they do not do the same thing.
This is my understanding also... was just wondering if rsync it would be a better option for what I am trying to achieve.

> I keep a separate partition of my /home directories and documentation of what and how I installed various tools and apps.  I don't upgrade I just install the new version of Ubuntu and preserver my home partition.  I have never had a failure from Ubuntu 6.06 (Dapper) on.
I have nothing of real consequance in /home therefore it is under root.   All my data resides elsewhere.

> I do keep of line backups of all my data using scripted rsync routines.
As do I.

---

### Post by bab1 on 2013-10-17
> **PJs Ronin said:**
> ty for your response


All the partitions are unmounted when I boot from a USB.   My problem is getting a label/UUID change to stick on the new partition.   Perhaps I should be looking at a bug report?

Have you tried setting this using the command line?  I've never had a problem either changing a UUID or creating file system (partition) with a specific UUID.
> 
[QUOTE]The utility rsync is a file level copy of the files and directories. In other words, they do not do the same thing. This is my understanding also... was just wondering if rsync it would be a better option for what I am trying to achieve.
[/QUOTE]
I personally find it a waste of time to clone anything as protection against what might happen when I install a newer version of Ubuntu.  My upgrade path is to have all of my data and all of my personal settings away from the  root directory (/).

In production servers and workstations I mount a separate device with single partition at /home.  This file system branch is separate from from the boot device and the root file system (/ (i.e. sda1)).  The notion is not just to have it on a separate partition, but to have that partition on a separate device also (i.e sdb1 = /home).  Complete separation and seamless usage.  I also mount another separate device at /srv/<mountpoint> for any exported (shared) data.  The root file system (booting) is only 10 - 20 GB at most, so an SSD will work for all of that.  I could use a flash drive but it's not reliable enough for my servers and desktops.

I've never had any problems installing the my favorite apps using my list of of installs.  It takes me about 30 minutes or less to upgrade a machine to the next version.

An interesting experience for me was when I needed to reformat a data volume.  I remembered to save the UUID from the old partition and used that UUID when reformatting the new file system for the partition.  This saved me from redoing the fstab file and multiple scripts I run for backup.
> 
I have nothing of real consequance in /home therefore it is under root.   All my data resides elsewhere.

Are you sure of that?  Data is one thing.  All of  the users personal configuration files are in their also home directories.  That is almost as important as the data.  Where are your hidden configuration files kept.  How do *you* deal with applications that store your personal configuration at ~/.config?  How do you deal with .bashrc or .bash_aliases?

---

### Post by sudodus on 2013-10-17
I use ***tune2fs*** to change the UUID and label of partitions with ext file systems and ***mkswap*** to change UUID and label of swap partitions.

They need sudo and they work (always) for me.

***rsync*** or ***tar*** or ***fsarchiver*** or ***clonezilla*** ..., there are many alternatives to ***dd***. You need to install the bootloader manually, if you are using rsync or tar. I don't know about fsarchiver.

The [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") uses ***tar*** to make, store and install [portable] systems.

---

### Post by PJs Ronin on 2013-10-17
> **sudodus said:**
> I use ***tune2fs*** to change the UUID and label of partitions with ext file systems and ***mkswap*** to change UUID and label of swap partitions.

Thank you.   I've only recently come across tune2fs and didn't really go into it as I am pretty command-line-phobic and assumed that gparted would serve my purposes for UUID/Label changes.   Looks like I need to read up on tune2fs although I have just done a test of rsync to 'duplicate' the contents of my production partition into a spare blank partition and it went as smooth as silk so I think dd (and thus the duplication of UUIDs and Labels) is now a lost cause for me.

This has been an interesting exercise for me, but I think I shall mark this thread as solved.   Thanks all for input... Ubuntu/Linux continues to amaze me with it's flexability.

---

