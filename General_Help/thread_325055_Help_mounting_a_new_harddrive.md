---
title: "Help mounting a new harddrive"
date: 2006-12-24
forum: General Help
---

### Post by fearevilleet on 2006-12-24
Hello,

I have been trying for hours to mount my second hard drive to no avail. Hopefully some one can lend me a hand. I formatted the second drive using gparted to ext3. I tried adding

 /dev/hdd   /home/evilleet/seconddrive  ext3    defaults     0 0

 /home/evilleet/seconddrive  is one of the mount points I tried, I also tried /mnt/seconddrive and changed the fstab

to my fstab, and when I do mount -a I receive the following

mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


the output of  dmesg | tail is 

[17365492.156000] NTFS volume version 3.1.
[17365946.976000] kjournald starting.  Commit interval 5 seconds
[17365946.988000] EXT3 FS on hdd1, internal journal
[17365946.988000] EXT3-fs: mounted filesystem with ordered data mode.
[17367525.444000] VFS: Can't find ext3 filesystem on dev hdd.
[17369875.156000]  hdd: hdd1
[17370924.664000] VFS: Can't find ext3 filesystem on dev hdd.
[17372468.860000] VFS: Can't find ext3 filesystem on dev hdd.
[17373009.508000] VFS: Can't find ext3 filesystem on dev hdd.
[17373148.656000] VFS: Can't find ext3 filesystem on dev hdd.



here is the fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14664   117788548+  83  Linux
/dev/hdc2           14665       14946     2265165    5  Extended
/dev/hdc5           14665       14946     2265133+  82  Linux swap / Solaris

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       14593   117218241   83  Linux


Sorry about not putting everything is a code box, I was unable to figure out how to do it.

---

### Post by meng on 2006-12-24
Instead of
/dev/hdd /home/evilleet/seconddrive ext3 defaults 0 0

try
/dev/hdd1 /home/evilleet/seconddrive ext3 defaults 0 0

---

### Post by fearevilleet on 2006-12-24
Ok, now it mounted but I am unable to write to it. How do I give myself write permissions?

---

### Post by fearevilleet on 2006-12-24
I tried  sudo chmod go+x /home/evilleet/seconddrive 

but that did not seem to work

---

### Post by bodhi.zazen on 2006-12-25
You have several options.

IMO I would, first mount the HD. Then:

```
sudo chown user_name:user_name /home/evilleet/seconddrive
sudo chmod 770 /home/evilleet/seconddrive
```

That second command likely does not need to be run as root.....

---

### Post by fearevilleet on 2006-12-25
That did not do it but it did point me in the right direction of chown!!

I did
sudo chown evilleet /home/evilleet/seconddrive

Thank god for the man command command :p

---

### Post by meng on 2006-12-25
Also, consider not go+x but go+w if you are using chmod.

---

