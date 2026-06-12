---
title: "Any progress on the NTFS trash problem in Hardy Heron?"
date: 2008-04-27
forum: General Help
---

### Post by mb_webguy on 2008-04-27
If there's another thread on this specific topic, I apologize, but the only one I saw was in the (closed) Development board...

For those unfamiliar with the problem, Hardy Heron does not allow files or folders on NTFS or FAT32 filesystems to be moved to a trash folder -- not even the ".Trash-username" folder used in previous releases.  Instead, if a file or folder is deleted, it is deleted permanently with no possibility of recovery.

For me (and I would think many other users) this is a significant problem.  I work with a mix of Windows and Linux computers, and have several external drives formatted as NTFS OR FAT32 since both OSes can read/write to those filesystems.  My primary computer is a dual-boot system with a shared NTFS partition for my data.  I understand the problems associated with implementing a Trash folder for these non-native filesystems, but I could deal with a separate ".Trash-username" folder for each volume.  At least I could recover files if I later decided I needed them.  With Hardy's current lack of any form of file recovery for these filesystems, my drives are getting horribly cluttered as I don't feel I can delete any file if there is any doubt whatsoever that I might need it at some later point.

So... does anyone know if there has been any progress resolving this issue?

---

### Post by NightwishFan on 2008-04-27
Not that I know of, although it does go both ways some users were confused why when they deleted files they did not gain any space back.

---

### Post by russo.mic on 2008-04-27
> **mb_webguy said:**
> If there's another thread on this specific topic, I apologize, but the only one I saw was in the (closed) Development board...

For those unfamiliar with the problem, Hardy Heron does not allow files or folders on NTFS or FAT32 filesystems to be moved to a trash folder -- not even the ".Trash-username" folder used in previous releases.  Instead, if a file or folder is deleted, it is deleted permanently with no possibility of recovery.

For me (and I would think many other users) this is a significant problem.  I work with a mix of Windows and Linux computers, and have several external drives formatted as NTFS OR FAT32 since both OSes can read/write to those filesystems.  My primary computer is a dual-boot system with a shared NTFS partition for my data.  I understand the problems associated with implementing a Trash folder for these non-native filesystems, but I could deal with a separate ".Trash-username" folder for each volume.  At least I could recover files if I later decided I needed them.  With Hardy's current lack of any form of file recovery for these filesystems, my drives are getting horribly cluttered as I don't feel I can delete any file if there is any doubt whatsoever that I might need it at some later point.

So... does anyone know if there has been any progress resolving this issue?

I think what needs to be realized is that the ntfs-3g driver to read NTFS partitions is NOT recomended as a solution for filesystem sharing or anything like that.  In fact, writing to an NTFS partition with that driver could potentially damage it.  This is due to Microsoft's closed filesystem, and unfortunality, until they decide to tell all (hold your breath), a safe and reliable solution for that problem is not in sight.

The recommended way (at least, from what I can tell on these forums) to share files between a vista/xp install and a linux install is a FAT32 partition, or install of XP, which would solve all of your problems.

Russo

---

### Post by jhnphm on 2008-04-27
As far as I know, the NTFS-3g driver will err on the side of caution and disable write access if there is a chance of corrupting data. Data corruption is a risk w/ the old in-kernel driver, not really 3g.

Obviously there's a risk w/ anything that's reverse engineered, but lots of things are reversed engineered on Linux, like RAID/NIC drivers.

Using FAT has its problems, namely maximum filesizes of only 4GiB, and the fact that it's not really robust due to lack of journaling. If you're really paranoid, just have a temporary partition to transfer files and move stuff off of it when you're done. 

Anyway, that isn't his problem. His problem may be related to bugs in nautilus or gvfs, since I believe this problem affects any FUSE filesystem (for some reason these bugs are marked closed). It's affecting sshfs and encfs too (not really a problem for me, since I do most file management using the CLI which doesn't have a trash anyway).

---

### Post by mb_webguy on 2008-04-27
> The recommended way (at least, from what I can tell on these forums) to share files between a vista/xp install and a linux install is a FAT32 partition, or install of XP, which would solve all of your problems.

Russo

Yeah, I know.  Unfortunately, my dual-boot system is Vista/Ubuntu, and Vista doesn't like FAT32 for certain directories.  While I have a copy or two of XP I could install, downgrading is fairly invasive surgery.  Even if I did, as jhnphm said, FAT32 has its limitations.  

Ideally, I'd switch everything over to ext3, but I need to keep Windows for now.  While Windows can technically work with ext3, it's a bit like drying your socks in a microwave.  It might work, but that's not really what it was made for, and you risk setting your socks on fire if you're not careful...

Right now, NTFS is the only modern, full-featured filesystem with  fairly reliable read/write functionality in both Windows and Linux.  I'd just like to have some file recovery ability.

---

### Post by mb_webguy on 2008-04-28
I just had another issue dealing with NTFS.

I was deleting some files (permanently, of course) from my NTFS partition, and one of the directories wouldn't delete, saying it wasn't empty or something to that extent.  Nautilus didn't show any contents in the directory, so I switched to CL.  When I used "ls" on the directory, it showed a file, but when I tried to "rm" it, I was given the error "cannot delete <file>: Input/output error".

"ls -lsa" on the directory showed a string of question marks for the permissions, user, and group.  I couldn't delete, rename, or move the file.  I finally had to reboot into Windows, which had no problem detecting and deleting the file (first to the Recycle bin, and then permanently).

It seems to me that there are a few kinks in Hardy when it comes to NTFS.  In the year and a half I've been running Ubuntu on this computer, I've never encountered this problem, but it pops up the second day I'm running Hardy...

---

### Post by Endolith on 2008-04-30
As far as I know, NTFS-3G is very safe.  I've been using it consistently since it came out and have had no problems.  It's the best way to share files between Linux and Windows.

---

### Post by Arless on 2008-05-01
Mounting a vfat or ntfs partition using uid=1000 option solve this problem, when you delete any file the message "cannot move to trash" will not appear again and a new dir "Trash-1000" will be created in your partion.

---

### Post by mb_webguy on 2008-05-02
Wow...  not only does mounting the drive using the current user's uid (which is 1000 for the default user) create a trash folder on the drive for that uid, it's compatible with Nautilus' Trash folder!  No more setting bookmarks in nautilus for the .Trash-*username* folders!

Does anyone know if there's a way to alter fstab so that the drives mount using the current user's uid?  If so, this minor edit to fstab completely solves the NTFS trash problem.  If not, it's still only a band-aid solution, and not really applicable to a multi-user system.

But thanks, Arless, that definitely solves my current problem.  I'll just have to keep this issue in mind when setting up dual-boot, multi-user systems...

---

### Post by konungursvia on 2008-05-04
> **Endolith said:**
> As far as I know, NTFS-3G is very safe.  I've been using it consistently since it came out and have had no problems.  It's the best way to share files between Linux and Windows.

I've been using an ntfs drive with windows and linux for almost a year, and had one major issue, not when writing per se, but when resizing the fat32 and ntfs partitions on that external drive using gparted. It seems that due to writing from linux, I had 3 files all referencing the same block of ntfs data, and after it was "discovered" by gparted, the partition was marked "in use", gparted froze, and neither windows nor linux could mount the ntfs partition ever again. Had to reformat it. Luckily I had most of the important stuff backed up on the fat32 partition, just to test a sync software package. But those who say ntfs-3g is completely safe are just.... lucky. That said, I'm still using it, esp. for movies.

---

### Post by Endolith on 2008-05-04
> **konungursvia said:**
> I've been using an ntfs drive with windows and linux for almost a year, and had one major issue, not when writing per se, but when resizing the fat32 and ntfs partitions on that external drive using gparted. It seems that due to writing from linux, I had 3 files all referencing the same block of ntfs data, and after it was "discovered" by gparted, the partition was marked "in use", gparted froze, and neither windows nor linux could mount the ntfs partition ever again. Had to reformat it. Luckily I had most of the important stuff backed up on the fat32 partition, just to test a sync software package. But those who say ntfs-3g is completely safe are just.... lucky. That said, I'm still using it, esp. for movies.

Is that a problem with NTFS-3G or a problem with ntfsresize?  When did this happen?

---

### Post by pistachepastis on 2008-06-25
> **mb_webguy said:**
> 
Does anyone know if there's a way to alter fstab so that the drives mount using the current user's uid?  If so, this minor edit to fstab completely solves the NTFS trash problem.  If not, it's still only a band-aid solution, and not really applicable to a multi-user system.


do a gksudo gedit /etc/fstab
then simply set the mount options of your ntfs partition to uid=1000

e.g. /dev/sda2    /media/data   ntfs    uid=1000     0        0

this mounts my sda2 to /media/data, with the uid=1000 option
(if you didn't have this kind of line added to your fstab yet, just do so)

---

### Post by ulysses222 on 2008-06-28
The solution proposed works for internal partitions, but doesn't apply for externable media, which are hot-pluggable and don't appear in fstab.

Has anyone a solution for changing default mount options for removable media?

One way to achieve this is to write a udev rule. 

Good information to achieve this can be found here:

[http://ubuntuforums.org/showthread.php?t=168221&page=1](http://ubuntuforums.org/showthread.php?t=168221&page=1)

Maybe someone knows another way?

---

### Post by piemonkey on 2008-08-10
> **ulysses222 said:**
> The solution proposed works for internal partitions, but doesn't apply for externable media, which are hot-pluggable and don't appear in fstab.

Has anyone a solution for changing default mount options for removable media?


I have an ntfs external hard-drive, and I get around this by putting the UUID of the drive in fstab, instead of /dev/sdb1, this way it always mounts to the same point, and I can change the owner to uid=1000. It does have the downside that I have to mount it from terminal if I don't boot with it plugged in, but I figure it's a small price to pay.

Anyone know a way to get it to mount when plugged in?

---

### Post by all2ez on 2008-08-20
> **pistachepastis said:**
> do a gksudo gedit /etc/fstab
then simply set the mount options of your ntfs partition to uid=1000

Thanks!

BTW I did uid=username and that seems to work too

---

### Post by NJC on 2008-08-26
After much gnashing of teeth I also solved the "cannot delete to trash" hades. Comment 10 on this thread: [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/192629](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/192629)

Fstab: 

UUID=480E-9F10  /mnt vfat defaults,utf8,umask=007,uid=1000,gid=1000 0 1

Oddly, when Nautilus wasn't allowing me to delete to Trash, Thunar was. :confused::confused::confused:

---

### Post by krippa on 2010-06-09
Did anyone ever manage to find a solution to this problem in a multi-user environment? I can´t use the uid flag because it only takes one username/uid!

---

### Post by irpsit on 2010-12-04
Hi, I still have this problem. Every file I try to delete, cannot be moved to Trash, so Nautilus asks me to delete permanently.
I am a beginner with Linux.

I have installed Ubuntu lucid, from Wubi, so dual-boot with Windows XP.

Windows on /dev/sda1 (NTFS)
Linux on /dev/sda2 (NTFS, mounted on /host)

I didn't edit anything on FSTAB file. The file shows these lines:

proc       /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /     ext4  loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none     swap    loop,sw  0       0

I didn't understand very well where to add the uid=1000 line
What shall I do? Could someone help me with this please?
Grateful,

---

### Post by Rubicon421 on 2011-01-28
anybody ever find a solution to this?

---

