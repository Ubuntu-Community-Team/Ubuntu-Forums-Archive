---
title: "ubuntu or Windows DONT see my 300 gb SATA"
date: 2008-02-23
forum: General Help
---

### Post by stonedparadox on 2008-02-23
okies

when i was running windows and ubuntu before i formatted both saw the 300 gig drive Perfectly
then i formatted and stuck windows back on
and then i installed ubuntu again

but in all those times both os's saw both drives INSIDE the pc
but for some reason they cant see the 300 gb

i was told to login to windows and go chkdsk .. but i dont remember what i was supposed to do after that ( help in a irc chan )

and now im at a loss

u have any idea's?

---

### Post by taurus on 2008-02-23
Do you have only one drive, 300GB, or do you have two drives?

Does the BIOS detect the drive at all?

Boot into Ubuntu, open a terminal, and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a upper case letter L.

---

### Post by stonedparadox on 2008-02-23
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27ec27eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+  83  Linux
/dev/sda2            6375       30401   192996877+   5  Extended
/dev/sda5            6375       30401   192996846   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f53283b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666   8e  Linux LVM

Disk /dev/sdf: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 3706 cylinders
Units = cylinders of 15810 * 512 = 8094720 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1          11       80293+   0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdf2              11        3707    29222234+   b  W95 FAT32
x@x-desktop:~$ 


it detects it there man

last time i checked it saw the 2 drives in the bios

---

### Post by taurus on 2008-02-23
Looks like you use LVM for /dev/sdb1!  See if you can use gparted in System -> Administration (if you don't have it, install it from synaptic, Add/Remove, or apt-get/aptitude) to format it to ext3 or ntfs.

---

### Post by stonedparadox on 2008-02-23
what is lvm?

i didnt think it made a difference
that being said i never looked it up

i dont wanna format 
do i have to format the drive to change it to ext3?

hmm
i opened up Gparted

im sure im able to change it to ext3 .. its just formatting sucks

btw i run windows now in Vmware

---

### Post by stonedparadox on 2008-02-24
anyone ?

---

