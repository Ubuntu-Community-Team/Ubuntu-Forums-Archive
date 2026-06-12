---
title: "Upgrade"
date: 2012-11-11
forum: General Help
---

### Post by smaxton on 2012-11-11
Hi all

Just some quick help with one small question.
i have a laptop still running 11.04 and i was planning on doing the upgrade, but...
wondering whether it will erase my emails and other documents like a new operating system install would do or will it just upgrade and keep all those vital things.
and i'm also guessing i should expect a complete settings default restore in the process.

Cheers Smaxton

---

### Post by zombifier25 on 2012-11-11
All of your personal settings (e.g. emails) are in your home folder. Back it up, reinstall and restore your home folder.

---

### Post by Topsiho on 2012-11-11
An upgrade will preserve your settings, and other personal stuff (but you MUST make a backup, just to be sure). An upgrade is similar to a massive update, during which all your system and applications (if from the Ubuntu repositories) get updated.

You can only upgrade to 11.10 (from 11.04), and if you want, to 12.04 in a next step (2 upgrades). Before you start an upgrade, you should update your system.

If you mean to do a fresh install (downloading an ubuntu .iso file, burning an image on a CD or creating a bootable disk (USB-stick) from it, then things depend on whether you have /home in a separate partition. If you have, then things will be preserved during install when you choose NOT to format the partition in which your /home sits.
In that case you need not to step from 11.04 to 11.10 (and to 12.04 to 12.10). After a fresh install you must do an update, and install all your applications that you need, and that are not included in the fresh install.

In any case you should backup the files that you do not want to loose.

Topsiho

---

### Post by pakopako on 2012-11-11
> **Topsiho said:**
> ...then things depend on whether you have /home in a separate partition. If you have, then things will be preserved during install when you choose NOT to format the partition in which your /home sits.
Wait, we can specify Ubuntu to place /home on another partition? (I presume it has to be an ext partition somewhere else.)

That said, can't compressing the /home directory preserve a majority of your settings and saved files (bar some scripts dumped into /etc or such)?

---

### Post by Topsiho on 2012-11-11
During the install you can specify in which partitions you want to install Ubuntu (choosing to preserve any partitions you want to keep, such as those of Windows if you want to install Ubuntu alongside Windows (dual boot), and of course your /home partition).

You can create and resize partitions any way you want, but should know what you do, such an install is more difficult than letting Ubuntu do this itself.

The thing is that you'll have to choose the mount points and filetype (such as ext4) (for /, /home, swap, for the partitions you want to use), and choose NOT to format /home, and partitions for the other operating system(s), for otherwise you'll loose their contents.

If you use Windows, and want to keep it, and want to change the partition table, maybe you'd better let the repartitioning be executed by Windows. If not, next time you boot Windows, it finds a partition table that is changed, and may refuse to boot.


Topsiho

---

### Post by smaxton on 2012-11-12
Hey thanks heaps everyone. will do

---

