---
title: "Cannot mount/unmount hard disks using GUI"
date: 2007-05-14
forum: General Help
---

### Post by Lou-Bear on 2007-05-14
I can't mount or unmount hard disks anymore (message says I don't have the privileges). I can mount and unmount them in the terminal using sudo mount/umount, but then they're read-only for my user. I've tried unmounting the drives from /media and remounting them on my desktop to see if that changes the situation, but it doesn't.

I read somewhere that it might be a bug with Gnome, or a problem with my fstab...

My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4330ba12-7071-4fbd-8ae2-977fcf41d3de /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=5AE840BCE84097E1 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=000000008BBDF0B6 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=cd618bd3-1ad4-4923-811b-f8e020375644 /media/hdb2     ext3    defaults        0       2
# /dev/hda3
UUID=d502b14c-4d82-4bec-a4f2-31016b8e488b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


hda1 is my Windows (2K) partition, so has to be NTFS, hda2 is my linux root partition, hda3 is my linux swap file.
hdb1 & 2 are both data storage.

Backed up then formated hdb2 as ext3, in the hope that the linux NTFS write drivers might have been responsible for messing things up (things went  bit weird when I started using ntfs-3g). I also wiped ubuntu and started afresh, but still I can't access them.

I may be being really stupid, but if someone can tell me what I should do that'd be great. (I'm using 7.04 at the moment-none of it seemed to be a problem in edgy, but can't put my finger on exactly when problems started)

cheers

---

### Post by scrooge_74 on 2007-05-14
You have the ntfs drive which is read only, did you follow the instructions for read/write?

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install)

Most likely you have to make changes to your fstab

---

### Post by Lou-Bear on 2007-05-15
Had NTFS read/write working fine in Edgy (it wasn't always 100% happy about remounting drives-but it was working).

Having now enabled it in Feisty, I can now read & write to the NTFS partition hdb1, but not the NTFS partition hda1 or the ext3 partition hdb2. The **Properties>Permissions** of both these drives show as:

Owner: Root 
Folder Access: Read & Write

Group: Root
Folder Access: Read

Others:
Folder Access: Read

They're blanked out, since I'm not the owner, root is. Can't change that, since if I unmount them as root in the console. I can't then mount them as myself, and I don't know how to change the permissions in the console.

I can't rename the mounts either or the links to the mounts on the desktop (assuming they are links), which is annoying. Don't know how it's ended up like this. But figure if a clean install of Feisty is doing it and a clean install of Edgy wasn't, maybe it's a Feisty problem? Might try reinstalling Edgy to see if that fixes things...

---

### Post by scrooge_74 on 2007-05-15
try the chown  and chmod commands on the terminal to change ownership

---

