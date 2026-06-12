---
title: "Mounting Problems"
date: 2008-05-21
forum: General Help
---

### Post by matt2175 on 2008-05-21
I'm having problems mounting my ntfs drive. It use to automatically mount but I think one of the updates I installed corrupted something because It does not even show up anymore under places nor can i get alot of things to work like clicking on the cd/dvd creator, Computer, cdrom0, and floppy0 under places. All return erros

Nautilus cannot handle computer: locations.
Nautilus cannot handle burn: locations
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

here was my tail of the dmseg

[19239.872170] attempt to access beyond end of device
[19239.872181] sr0: rw=0, want=68, limit=4
[19240.337132] attempt to access beyond end of device
[19240.337143] sr0: rw=0, want=1252, limit=4
[19240.338650] attempt to access beyond end of device
[19240.338656] sr0: rw=0, want=1028, limit=4
[19240.340028] UDF-fs: No partition found (1)
[19240.362807] attempt to access beyond end of device
[19240.362814] sr0: rw=0, want=68, limit=4
[19240.364186] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16



I then decided to try to manually mount the drive. I brought up Fdisk -l to get its location dev/sdb tried to mount it and it returns the error

can't find /dev/sdb in /etc/fstab or /etc/mtab

Which i then decided to try to add it in manually under fstab but I came up to the UUID number for the hard drive I tried to use 

sudo vol_id /dev/sdb

and got

/dev/sdb: unknown volume type


I basically just want to be able to drag important files over to that drive so that i can format and reinstall Ubuntu. I want to do this anyways regardless of this bug I have.

Any suggestions or help would be apprecaited.

I have seen a few others having the same problem I am having but I have not seen a fix to it. But the dates varies on these people that are having the problems so I'm not sure what caused it. I hadn't logged onto Linux for a month and needed to get back to using it and had some updated. I updated then 5 days later i noticed these problems.

---

### Post by drao on 2008-05-21
It happend for me too...but its not as severe like ...i used 7.10 for a month ..i made changes in fstab file..then i was able to mount the drives automatically whenever it reboots..but once i updated to 8.04 ...it was not doing as supposed to do....but later i found out that they rename hdb* to sdb*. So i made changes in  fstab file to sdb's instead hdb..it worked for me. can you compare ur fdisk and fstab file.....it gives u some idea..

---

### Post by danwood76 on 2008-05-21
Your ntfs partition will not be /dev/sdb, that is the block device.
You need to specify a partition number to the mount command otherwise it will give the errors you described above.

The partition will be something like this:
/dev/sdb1

so for this example to mount to /media/foo
```

sudo mkdir /media/foo
sudo mount -t ntfs-3g /dev/sdb1 /media/foo

```
That will mount the drive and should stick an item on your desktop.

---

### Post by matt2175 on 2008-05-21
Ah that worked, thanks to both of you. Its always good to learn new things :)

---

### Post by danwood76 on 2008-05-21
If you want it to automount then add it to your fstab ;)

---

### Post by strabes on 2008-05-21
Here's a line in /etc/fstab that should work for you.> /dev/sdb1 /media/windows  ntfs    defaults,umask=007,gid=46 0       1

---

### Post by fmonjaraz on 2008-05-21
I am having the "Nautilus cannot handle..." problem..is there a fix for this or do I have to manually mount my external hard drives everytime??

---

