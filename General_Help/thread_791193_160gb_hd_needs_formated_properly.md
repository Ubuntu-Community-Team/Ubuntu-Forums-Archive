---
title: "160gb hd needs formated properly"
date: 2008-05-11
forum: General Help
---

### Post by grimlock838 on 2008-05-11
So I have a 160 GB HD slave, but the problem is that I can only format 149.05 gib of it (according to gparted) but when I sudo fdisk -l i get this:

> brooke@booknavel:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb3c6ce1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux


SO how do I format it to get it all and then get my usr side/file manager to recognize it when I log on?

V/r
grimlock838

PS Thank Adonai for Ubuntu! :lolflag:

---

### Post by HunterThomson on 2008-05-12
If windows was ever installed on the 160GB HDD then it ate up the space with a recovery partition.

Window$ also eats up 20% of your bandwidth 24/7 for windows updates that it like never uses because micro$oft never updates there OS.

---

### Post by grimlock838 on 2008-05-12
> **HunterThomson said:**
> If windows was ever installed on the 160GB HDD then it ate up the space with a recovery partition.

Window$ also eats up 20% of your bandwidth 24/7 for windows updates that it like never uses because micro$oft never updates there OS.

I believe that is what happened. How Can I reclaim that space. I have Gparted but how do I fix it? But in any case the only M$ product I will support is Xbox360. As far as M$ is concerned it is the only product I have ever bought from 'em that I am impressed with and enjoy.

---

### Post by grimlock838 on 2008-05-12
So I have a 160 gb and 7.6 gb is used up. so that means 149 and change is free.
So that 7.6 Gb is for reserved for the root?? how do I reclaim that???

---

### Post by jim_24601 on 2008-05-13
It's got nothing to do with Windows; you've encountered one computing problem we can't blame on Microsoft. (Enjoy it; they're rare enough.) It's actually down to a bit of weaselry on the part of hard disc manufacturers. Your disc is, in fact, 149.05 x 2^30 bytes, which is the same as 160.00 x 10^9 bytes. Geeks prefer the larger power-of-two gigabyte because it's more convenient for computers. Hard disc manufacturers prefer the smaller power-of-ten gigabyte because it makes their discs look bigger. Recently there's been a push to use the unambiguous coinings "mebibyte" and "gibibyte" for powers of two, but they're not in very common use, mainly because they sound really, really stupid.

Anyway, the point is that your whole disc is actually properly formatted, it's just that the two tools are using different definitions of "gigabyte". Like "tonne" vs. "ton". It's sucky and confusing, but we're probably stuck with it for a while.

---

### Post by kirios on 2008-05-13
You seem to have Ubuntu on sda1. If you do have 7.6 GB used on sdb1, it's probably not related to Ubuntu. It would help if you could post the output of **mount** and **sudo parted /dev/sdb**. 

jim_24601 has already explained the discrepancy between the vendor's claims and the **actual** available space on a hard disk. I seem to recall hearing about a class-action suit against one of the vendors on this issue. Don't know how it eventually turned out though.

> **grimlock838 said:**
> So I have a 160 gb and 7.6 gb is used up. so that means 149 and change is free.
So that 7.6 Gb is for reserved for the root?? how do I reclaim that???

---

### Post by grimlock838 on 2008-05-13
> **kirios said:**
> You seem to have Ubuntu on sda1. If you do have 7.6 GB used on sdb1, it's probably not related to Ubuntu. It would help if you could post the output of **mount** and **sudo parted /dev/sdb**. 

jim_24601 has already explained the discrepancy between the vendor's claims and the **actual** available space on a hard disk. I seem to recall hearing about a class-action suit against one of the vendors on this issue. Don't know how it eventually turned out though.

> (parted) print all

Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  160GB  160GB  primary  ext3              



Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  78.5GB  78.5GB  primary   ext3         boot 
 2      78.5GB  80.0GB  1546MB  extended                    
 5      78.5GB  80.0GB  1546MB  logical   linux-swap        


Warning: Unable to open /dev/scd1 read-write (Read-only file system).  /dev/scd1
has been opened read-only.
Error: Unable to open /dev/scd1 - unrecognised disk label. 

> 
brooke@booknavel:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/brooke/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brooke)
/dev/scd1 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=brooke)
Here you go!

---

### Post by grimlock838 on 2008-05-13
> **jim_24601 said:**
> It's got nothing to do with Windows; you've encountered one computing problem we can't blame on Microsoft. (Enjoy it; they're rare enough.) It's actually down to a bit of weaselry on the part of hard disc manufacturers. Your disc is, in fact, 149.05 x 2^30 bytes, which is the same as 160.00 x 10^9 bytes. Geeks prefer the larger power-of-two gigabyte because it's more convenient for computers. Hard disc manufacturers prefer the smaller power-of-ten gigabyte because it makes their discs look bigger. Recently there's been a push to use the unambiguous coinings "mebibyte" and "gibibyte" for powers of two, but they're not in very common use, mainly because they sound really, really stupid.

Anyway, the point is that your whole disc is actually properly formatted, it's just that the two tools are using different definitions of "gigabyte". Like "tonne" vs. "ton". It's sucky and confusing, but we're probably stuck with it for a while.

i thought I read some where that root takes 5 percent of the hd. hence the 7.6. I wish I knew how to post a picture in this damn box. 
[IMG]http://picasaweb.google.com/grimlock838/UntitledAlbum/photo#5200022020254335538[/IMG]
any way here the link. [http://picasaweb.google.com/grimlock838/UntitledAlbum/photo#5200022020254335538](http://picasaweb.google.com/grimlock838/UntitledAlbum/photo#5200022020254335538)

---

### Post by grimlock838 on 2008-05-13
This is where I am getting the 149gb/7.6gb. RC on properties in computer on the 160gb. Hence my wanting to get every last bit.

---

### Post by kirios on 2008-05-14
Nothing to worry about there. :-) 

If you still need reassurance that Ubuntu isn't using any space on the sdb1 partition yet, run **sudo parted /dev/sdb**.

To mount the sdb1 partition:
```
sudo mkdir /mnt/sdb1 
sudo chown -r brooke /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
``` 
You should then be able to use the sdb1 partition by navigating to /mnt/sdb1 in the file manager.

> **grimlock838 said:**
> Here you go!

---

