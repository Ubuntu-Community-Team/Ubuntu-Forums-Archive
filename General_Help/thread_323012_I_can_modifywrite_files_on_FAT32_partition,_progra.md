---
title: "I can modify/write files on FAT32 partition, programs can't"
date: 2006-12-21
forum: General Help
---

### Post by ernstblaauw on 2006-12-21
I've mounted some FAT32 partitions to /media/.... I can use them and paste files there.
However, if a program wants to save files there, it is not possible, Archive Manager says: 'operation not permitted'. Firefox just does nothing if I want to download a file to that location.
My fstab looks like
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=3aced2a5-e71e-48f3-8a47-18876db25004 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc3
UUID=41C2-17AD  /media/hdc3     vfat    defaults,utf8,umask=000,gid=46 0       0
# /dev/hdc5
/dev/hdc5	/media/hdc5     ntfs-3g defaults,utf8,locale=nl_NL.utf8 0       0
# /dev/hdc6
UUID=430A-FDE5  /media/hdc6     vfat    defaults,utf8,umask=000,gid=46 0       0
# /dev/sda1
UUID=4305-ED65  /media/sda1     vfat    defaults,utf8,umask=000,gid=46 0       0
# /dev/sda5
UUID=430B-0E69  /media/sda5     vfat    defaults,utf8,umask=000,gid=46 0       0
# /dev/sda6
UUID=4308-5B17  /media/sda6     vfat    defaults,utf8,umask=000,gid=46 0       0
# /dev/sdb1
/dev/sdb1	/media/sdb1	ntfs-3g	defaults,utf8,locale=nl_NL.utf8	0	0
# /dev/sdb2
/dev/sdb2	/media/sdb2     ntfs-3g defaults,utf8,locale=nl_NL.utf8 0       0
# /dev/sda8
UUID=7e4fb4aa-97d5-42f6-90a3-139fcc0db708 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
For example, look at 'sda5'.

Can someone help me?
With regards,
Ernst

---

### Post by ajgreeny on 2006-12-21
Can you paste files there as user or only as root, because surely /media is owned by root, and you can't save files there as user.  Have I got this wrong?  I think I may have done because a usb flash memory stick is mounted automatically as /media/sde1 on my machine and it is owned by user.  This may be something to do with the 000 in the line or perhaps where you have used *defaults,utf8*.  What happens if you use *iocharset=utf8* instead?  I'm not fully conversant with the use of all these arguments in the fstab file but these are the only differences I can see from the usual lines.

---

### Post by dannyboy79 on 2006-12-21
also, you have it being mounted with uid=46, who's id is 46?? the first user on all ubuntu machines is 1000. unless you changed this??? also, I don't like your fstab entries. i'll post mine when I get home because mine work fine, sbackup daemon can write to my fat32 partitions, so can other programs so i'll let ya know later.

---

### Post by ernstblaauw on 2006-12-21
[LIST]
[*]I can paste files as a user
[*]I did not alter 'fstab' for vfat, only the entries of ntfs-3g. 
[*]I don't know who is gid=46. How can I retrieve that?
[/LIST]
I'm going to try some different parameters. Is it enough to just restart my X-server bij pressing <ctrl>-<alt>-<backspace>? Or do I have to restart my computer?

---

### Post by dannyboy79 on 2006-12-21
well then who created the fstab for these vfat partitions? i believe you can find that out in the users and groups tab within administration under system. you don't have to restart or do ctrl alt backspace (which by the way restarts your xserver) all you have to do is unmount that partition and then remount it. so you would do sudo umount /dev/sda1 or whatever you wanteed to unmount, then before remounting it make the change, then do sudo mount -a and it'll read your fstab and mount it per that. good luck

I have posted my fstab entry tons of times, do a search on writing to fat partition or something similar. oh yeah, writable flash drive or something like that. flash drive read only or somewthing like that. or you can do a search by all the threads that I have posted, then do a search amoung them looking for fat or writable. good luck.

---

### Post by ernstblaauw on 2006-12-21
I changed all the 'gid=' entry's to '1000', which is my gid. However, Firefox can't download to those locations.
However, I discovered something:
[LIST]
[*]OpenOffice can write files on this partition
[*]Firefox can create a file, but the result is a file with length 0.
[*]Archive Manager sais: ```
tar: XnView-1.70-x86-unknown-linux2.x-static-fc4/Formats.txt: Cannot utime: Operation not permitted
```
[/LIST]
It looks like different programs use different methods to write. I don't understand the differences between Firefox and Archive Manager on one side, and OpenOffice on the other side.

---

### Post by dannyboy79 on 2006-12-21
try this in your fstab, i can write to mine using this:

/dev/sda1  /media/KINGSTON vfat  rw,uid=1000,gid=1000,iocharset=utf8 0 0

obviously change sda1 and the mount point to whatever yours are. good luck

---

### Post by ernstblaauw on 2006-12-21
I found the solution!
I have to put this as options in fstab:
```
auto,rw,user,uid=1000,gid=1000,fmask=111,dmask=000,shortname=mixed
```

I really don't know what they mean... And I really don't care atm ;) 
Thanks for your help!

---

### Post by ernstblaauw on 2006-12-21
> **dannyboy79 said:**
> try this in your fstab, i can write to mine using this:

/dev/sda1  /media/KINGSTON vfat  rw,uid=1000,gid=1000,iocharset=utf8 0 0

obviously change sda1 and the mount point to whatever yours are. good luck
This does not work for me.

If I use the option
```
auto,rw,user,uid=1000,gid=1000,fmask=111,dmask=000,shortname=mixed
```
I got another problem: all my files are not executable. I cannot change this with my right mouse -> properties: as soon as I click that executing is ok, the option is reset.
Does someone know which option in fstab is related to executing?

---

### Post by dannyboy79 on 2006-12-22
why are you adding fmask, dmask, and shortname??? I have explained that the fstab entry that I posted works for writing to it. at least using bittornado, nerolinux, and a few others I can't think of. also, make sure the folder's are owned by you otherwise yeah, they will only be able to be written by root I believe. when all else fails, read the man page for fstab, mount, and smb.conf. you'll figure it out. you could try adding the exec option, per man: exec   Permit execution of binaries. im telling ya, just read these man pages and you'll be on your way! good luck

---

### Post by ayoli on 2006-12-22
default ubuntu settings in fstab for vfat partition use defaults,gid=46,... which is plugdev group id, i had to change that to :
```
auto,user,rw,utf8,umask=000,gid=1000,uid=1000
```
and it works like a charm (but it's not usable by users that are not in my group, if you want that add users to your group with: sudo addgroup <username> <groupname>)

---

### Post by ernstblaauw on 2006-12-24
> **dannyboy79 said:**
> why are you adding fmask, dmask, and shortname??? I have explained that the fstab entry that I posted works for writing to it. at least using bittornado, nerolinux, and a few others I can't think of. also, make sure the folder's are owned by you otherwise yeah, they will only be able to be written by root I believe. when all else fails, read the man page for fstab, mount, and smb.conf. you'll figure it out. you could try adding the exec option, per man: exec   Permit execution of binaries. im telling ya, just read these man pages and you'll be on your way! good luck
I changed the entries to:
```
rw,dmask=0000,fmask=0111
```
This means, all my files can be read and written by everyone. I found out, that if they are also executable, some programs can't write to them anymore. I don't know if this is security or a bug, but using this settings, all programs can read and write and that's what I want. 
Those pages are really helpfull:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[http://slackwiki.org/Windows_Partitions](http://slackwiki.org/Windows_Partitions)

Hopefully, I will found out one day what setting I have to use to make it possible to make the drive r, w and x for all my (as a user) and the programs. I also really do not understand why there is a difference between me, and [b]some[b] other programs.

---

### Post by leep on 2007-01-02
I was running the same problem and solved changing fstab like this:

> /dev/hdc2	/media/hdc2	vfat	defaults,utf8,umask=000,gid=46	0	1  

---

