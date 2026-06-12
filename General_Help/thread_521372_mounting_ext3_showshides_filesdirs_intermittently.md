---
title: "mounting ext3 shows/hides files/dirs intermittently"
date: 2007-08-09
forum: General Help
---

### Post by lotuseclat79 on 2007-08-09
I use Ultimate Ubuntu 1.4 (UU1.4) Live CD derived from Ubuntu 7.04 Fiesty Fawn and also the 6.0.6 Dapper Drake LTS Live CD.

I have a Fedora Core 3 (FC3) Red Hat Linux installed on an 80GB SATA drive.

I have no problems mounting and accessing the FC3 drive using Dapper Drake, however, when I use UU1.4, I intermittently run into a problem whereby after issuing the mount command, I cannot access my subdirectory (it does not show in an ls command).

I keep scripts and files on the FC3 system that I access by using the mount command:
# mount -t ext3 /dev/sdb2 /tmp/disks-conf-sdb2

Recently, while using UU1.4, after having issued the above mount command, I was not able to access the subdirectory where I keep my saves from the Live CD environment.  I have now run into this problem three times on an intermittent basis.

Upon reading the mount command, it states that "The previous contents (if any) and owner and mode of dir become invisible.  Unfortunately, the "unhide" parameter only seems to work for an iso9960 file system type.

Since, according to the man page, one can reason that the mount command is working perfectly doing what it is supposed to do, i.e. hide contents, etc, and therefore conclude that there is no problem.

Apparently, is is not working properly - when I am able to access the contents as I would like to be able to do every time I mount the FC3 drive, and working properly when I am not able to access the contents of the FC3 drive ext3 filesystem.

I am able to boot up the FC3 filesystem and verify that the contents are there, and I am able to use the Dapper Drake Live CD to access the subdirectory and its file contents.

Note: all accesses to the FC3 file system are made from the root account under UU1.4, to the /root directory on the FC3 ext3 filesystem.

Is there a solution such that I can consistently mount the FC3 ext3 filesystem and access the subdirectories and contents that are obviously there?

What causes this "problem" with UU1.4, and why does DD6.0.6 not suffer from it?

-- Tom

---

### Post by lotuseclat79 on 2007-08-10
Yesterday, after using Ubuntu 6.0.6 LTS Live CD for most of the day, I mounted my FC3 disk using the option sync:  
# mount -v -t ext3 -o sync /dev/sdb2 /tmp/disks-conf-sdb2
and noticed that the copy command of my large bzip2 files took longer to copy than  compared to not using the sync option.

Since FC3 is a journaled filesystem, and no Live CD running in RAM including the filesystem is not, it is likely the problem was facilitated by not using the sync option - I'm guessing.

I still do not know why the problem never asserted itself with Ubuntu 6.0.6 LTS and occured in Ultimate Ubuntu 1.4 Live CD environment.  Part of the problem, I assume, is that the FC3 system is not booted up, so if you don't use the sync option, the state of the journal regarding FC3's filesystem, and it contents (when FC3 is not booted up and running) gets somewhat out-of-phase what with super blocks and such implementing the filesystem architecture.

Last night, I fired up UU1.4 using the sync option on the mount command as above and it worked, as it did this AM.

I'm sure a kernel filesystem engineer with access to the source code for either version of Ubuntu described in this thread could explain more about why this problem occured from an internals (filesystem implementation) perspective in short order.  I just do not have access to any filesystem source code (using a dialup account on this end).

-- Tom

---

