---
title: "special device &lt;/dev/xx&gt; does not exist"
date: 2007-07-15
forum: General Help
---

### Post by OldAlgis on 2007-07-15
Hi,
I like to have several distro's running on one PC, plus the Windoze (many people ask questions about the latter, so I do run it reluctantly).  So I setup my new amd64 box with partitions /dev/sda1 to /dev/sda15 with sda1 with win OS and sda2 with fat32.  All went smoothly with ubantu/kubantu 7.04.  

After some experience of a whipe-out of MBR, I thought of transferring the fat32 data to a logical partition in order to free sda2 for Linux.  So I did some partition rearrangement with gparted and created a sda16 fat 32 partition with Partition Magic.  All seems OK - windoze is happy, Linuxes are happy, except that in Linux (kubuntu 7.04) there is no /dev/sda16.  There sure is partition 16 with fat 32, labelled SDA16 (windoz are allergic to l.c. letters).  

How can I prod Linux to create /dev/sda16?  I think that a new installation would probably 'see' the partition 16, but how is it created?

My fstab entry is
```
 # /dev/sda16
LABEL=SDA16    /media/sda16   vfat     defaults,utf8,umask=007,gid=46 0      1 

```
If I "sudo mount /media/sda16", I get an error message: "special device /dev/disk/by-label/SDA16 does not exist."  

Inspection of /dev/disk shows that /dev/sda16 "does not exist".

Any pointers, clues, advice - please!

---

### Post by AlexenderReez on 2007-07-15
you need to specific place to boot....

let say in mnt/example


so

> sudo mkdir /mnt/example

> sudo mount /dev/** /mnt/example 

---

### Post by OldAlgis on 2007-07-15
Hi reez1015,

/media/sda16 has been created as a specific place to boot.  Makes no difference if it is /mnt/sda16, does it?

You see, the point is that /dev/sda16 is not there, though the partition is surely there! Here is a sample dialog (notice that /mnt is empty):
```

root@amd64:~# ls -l /mnt
total 0
root@amd64:~# mount /dev/sda16 /mnt
mount: special device /dev/sda16 does not exist
root@amd64:~#

```

---

### Post by Nythain on 2007-07-15
blkid will list partitions and give info such as UUID and LABEL so that you can go about editing your fstab with the correct info

---

### Post by OldAlgis on 2007-07-15
> **Nythain said:**
> blkid will list partitions and give info such as UUID and LABEL so that you can go about editing your fstab with the correct info

Nythain,  yes, blkid is a handy tool to list partition details.  Thank you - I will use it, rather than the lookup of /dev/disk etc.  However, it does not solve anything for me - the sda16 is simply not "seen" by Linux.  I think I am in a bind with windoze and Linux incompatibilities in MBR.  I will get around it by taking another partition that is "known" to Linux and format it with fat32 to facilitate data transfer between the windoze and Linux.

Thanks for your handy hint,

---

### Post by KronK0321 on 2007-12-03
> **OldAlgis said:**
> Hi,
How can I prod Linux to create /dev/sda16?  I think that a new installation would probably 'see' the partition 16, but how is it created?

My fstab entry is
```
 # /dev/sda16
LABEL=SDA16    /media/sda16   vfat     defaults,utf8,umask=007,gid=46 0      1 

```
If I "sudo mount /media/sda16", I get an error message: "special device /dev/disk/by-label/SDA16 does not exist."  

Inspection of /dev/disk shows that /dev/sda16 "does not exist".

Any pointers, clues, advice - please!

I know I'm resurrecting this thread but I had the same problem and found the answer.

Your fstab entry is correct but if you just labelled the drive and have not rebooted yet, that's the problem. the /dev/disk/disk-by-label devices do not get created until the drives are scanned on the next reboot.

---

### Post by shizzy-t on 2008-03-04
If you don't want to reboot just run partprobe

---

