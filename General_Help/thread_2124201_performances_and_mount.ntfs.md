---
title: "performances and mount.ntfs"
date: 2013-03-10
forum: General Help
---

### Post by jsabina1 on 2013-03-10
Hi,
I've installed Lubuntu on a quite old laptop (2gb ram)
It's going quite well, but Every Time that I install something via apt-get for 3 or 4 minutes I have a process mount.ntfs that takes up to 99% of CPU and I cannot do anything anymore.
I have dual boot with windows 7, but no shared directories (as far as I know :P ).

In general I am using only skype, terminal and chromium with 3 or 4 tabs until now!!!

How can I solve? It's quite boring..

---

### Post by Androzani1 on 2013-03-10
That is a strange one. What is your hard driver formatted as?

---

### Post by jsabina1 on 2013-03-10
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   205680639   102736896    7  HPFS/NTFS/exFAT
/dev/sda3       484208638   488396799     2094081    5  Extended
/dev/sda5       484208640   488396799     2094080   82  Linux swap / Solaris


mmh is it for the dual boot?

---

### Post by Impavidus on 2013-03-10
I'm missing your ext3 or ext4 partition. It should be present and in use as root file system in linux. Swap is there, so it seems a proper dual boot otherwise. Or do you have a second drive you didn't mention?

Dual booting shouldn't cause errors like this, even if you do have a shared data partition.

---

### Post by jsabina1 on 2013-03-10
I've run fdisk -l
Should I run any other command?

I don't have any other drive..

---

### Post by Impavidus on 2013-03-10
Then I wonder where your root partition is. Can you run```
mount -l
```(That's lower case L)

---

### Post by jsabina1 on 2013-03-10
[ATTACH=CONFIG]240000[/ATTACH]

---

### Post by Impavidus on 2013-03-10
So this is a wubi install with a separate swap partition and enough unallocated disk space to install as a proper dual boot.

What was your intention when you installed? A wubi install is easier to uninstall but is not independend of the windows file system and limited in disk space to 30GB, which you have fully used.

I still don't know why there is the mount.ntfs activity, but it may be related to this unusual setup.

---

### Post by jsabina1 on 2013-03-10
Uhm, to be honest I don't know what is a wubi install but I'll go to read about that.
I've installed from windows because cd rom is broken, but I want to use always ubuntu and only keep windows for some small things..

~$ mount -l
/dev/loop0 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
gvfsd-fuse on /run/user/jsabina/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=jsabina)
/dev/sda1 on /media/jsabina/System Reserved type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) [System Reserved]

---

### Post by Mark Phelps on 2013-03-10
A wubi install is used to install Ubuntu from INSIDE Windows -- primarily to avoid the problems of creating new partitions.  But as such, it is critically dependent on Windows working in order to be able to use it.  It's OK to try it this way, that's what it was designed for, but if you plan to use Ubuntu long-term, you need an install in its own partitions.

---

### Post by Impavidus on 2013-03-10
In that case you want a true dual boot. Provided your laptop supports booting from usb (most have done so for several years) you can install Ubuntu from an usb flash drive: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
You can also migrate wubi to a partition of its own: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) (never tried that myself)

And I was thinking, maybe there's a problem with your windows file system. Running chkdsk from windows or defragmenting the windows partition might help. I'm not sure, as I haven't used windows in years. But is you're moving to a true dual boot that's not very relevant any more.

---

### Post by jsabina1 on 2013-03-10
ok perfect..
so I'll try maybe to install from usb stick..

---

### Post by jsabina1 on 2013-03-10
just a super newbie question..
how have you seen it is a wubi installation?
I promise I am going to study myself... I use linux for a while but never understood mount and disks :P

---

### Post by jsabina1 on 2013-03-10
Ok understood and I did the migration following the guide..
Now I have ext4 143gb for linux and unfortunately 104gb for windozz :P
Let's see if I will have again the problem with that ntfs

---

### Post by Impavidus on 2013-03-10
> **jsabina1 said:**
> just a super newbie question..
how have you seen it is a wubi installation?
I promise I am going to study myself... I use linux for a while but never understood mount and disks :P

In your screenshot I saw the /host/ubuntu/disks/root.disk. That's the virtual partition only present in wubi installs.

---

### Post by jsabina1 on 2013-03-11
Perfect thanks.
I can confirm that since I've migrated to a standard ubuntu I don't have anymore the problem with mount.ntfs.
Thanks for the support!

---

### Post by Impavidus on 2013-03-11
I'm glad you solved your problem. If you've any more questions, just open a new thread and ask.

---

