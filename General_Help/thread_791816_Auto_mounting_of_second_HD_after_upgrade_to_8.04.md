---
title: "Auto mounting of second HD after upgrade to 8.04"
date: 2008-05-12
forum: General Help
---

### Post by JonC_6.06 on 2008-05-12
Hi guys,

I recently upgraded from Gutsy to Hardy and since then my second hard disk does not mount automatically. Originally (in Gutsy) I added it to /etc/fstab as the following

/dev/hdb1	/media/disk	ext3	defaults	0	1

which is now producing an error on start up. Something to do with it not being a valid ext3 partition and that it needed to be repaired manually. However, when I mount it I can navigate through it with no problems and as far as I can see it is working fine. I read somewhere that the last field in the fstab file tells the OS whether to check the file system on boot up so I thought that changing this to a 0 would solve my auto-mounting problem. I no longer get the error but the drive still isn't mounting until I try to access it.

Then I have a vague recollection of a command that tells you what the system recognises the partition as (the/dev/hdb1 part). Can I remember the command? No. Can I find it on the net anywhere? No. I'm maybe be completely wrong here but I am sure I checked this first and then decided it should be /dev/hdb1.

I'm a complete novice when it comes to Linux so I would appreciate any help! Sorry for the unnecessarily long post!

Jon

---

### Post by TeoBigusGeekus on 2008-05-12
Try
```
/dev/hdb1 /media/disk ext3 relatime 0 2
```

---

### Post by JonC_6.06 on 2008-05-12
Thanks for the reply. That change seems to bring up the same problem though. I wrote it down this time!

fschk.ext3: No such file of directory while trying to open /dev/hdb1

/dev/hdb1:

THe superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 file system (and not swap or ufs or something else0, then the superblock is corrupt, and you might try running e2fsck with an alternate super block:
    e2fsck -b 8193 <device>

fsck died with exit status 8

File system check failed

Log saved to /var/log/fsck/checkfs if location is writable.


The Log contains the following:

Log of fsck -C3 -R -A -a 
Mon May 12 18:48:16 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/hdb1
/dev/hdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Mon May 12 18:48:16 2008
----------------
cat: if: No such file or directory
cat: location: No such file or directory
cat: is: No such file or directory
cat: writable: No such file or directory


Any idea's?

---

### Post by TeoBigusGeekus on 2008-05-12
Could you post us the outputs of 
```
sudo fdisk -l
```
(-L)

and
```
sudo nano /etc/fstab
```

---

### Post by JonC_6.06 on 2008-05-12
fdisk -l gives

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02c802c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7288    58540828+  83  Linux
/dev/sda2            7289        7476     1510110    5  Extended
/dev/sda5            7289        7476     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f5c0f5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30514   245103673+   7  HPFS/NTFS
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 912 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           3       96264    0  Empty
/dev/sdc2               4         912    29206170    b  W95 FAT32




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d3df73fc-1a3c-4607-a9b3-5fe4acd5d890 /               ext3    defaults,erro$
# /dev/hda5
UUID=849cf299-20af-4253-b8d3-8d6ec70924f4 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb1       /media/disk     ext3    relatime        0       2



My second disk (the one i want to mount) is the 251GB one.

---

### Post by TeoBigusGeekus on 2008-05-12
What happens if you change the last line to
```
/dev/[COLOR="Red"]s[/COLOR]db1 /media/disk ext3 relatime 0 2
```

---

### Post by JonC_6.06 on 2008-05-12
No errors this time but the disk isn't mounting either. When I try manually it says "You are not privileged to mount this volume."

---

### Post by TeoBigusGeekus on 2008-05-12
Hey, wait a moment!!!
The 251gb drive is ntfs...
Change it to 
```
/dev/sdb1 /media/disk ntfs relatime 0 2
```

---

### Post by JonC_6.06 on 2008-05-12
still getting the permissions problem??? I am not sure why it is now showing as NTFS either.

---

### Post by JonC_6.06 on 2008-05-12
i changed fstab reference to the drive back to hdb1 and was able to mount it manually. When I check the drive once its mounted it says its ext3 not NTFS as an earlier command says. Im confused

---

### Post by JonC_6.06 on 2008-05-12
Anybody? It still not mounting automatically

---

### Post by TeoBigusGeekus on 2008-05-12
Ok then... 
Plan B:
Install ntfs-config through synaptic. Then go to applications->system tools->ntfs configuration tools, choose the volume and check all button.

If Ubuntu thinks it's ntfs, just roll with it...

I really hope this one works cause I'am running out of ideas...:confused:

---

### Post by JonC_6.06 on 2008-05-13
Can anybody help? This is really doing my head in now!!! I've toyed with the idea of a clean install but I don't have the time at the moment and not sure I can be bothered either!

---

### Post by JonC_6.06 on 2008-05-13
Can anybody help? Its really starting to annoy me now!

---

### Post by JonC_6.06 on 2008-05-13
TeoBigusGeekus

It just occurred to me I haven't thanked you for your help so far so thanks for your help so far!

It still isn't working though. I don't understand how it could be fine and then not so fine after an upgrade!

---

### Post by JonC_6.06 on 2008-05-14
How silly do I feel now? It seems that upgrading to 8.04 deleted the mount point from /media. After re-creating this and applying the permissions again the drive mounts on start up with no problem. Not sure why it thouhgt it was ntfs. it isn't. I don't care though. ITS FINALLY WORKING!!!

Thanks for your help.

---

### Post by Lrdwilliams on 2008-05-14
> **JonC_6.06 said:**
> How silly do I feel now? It seems that upgrading to 8.04 deleted the mount point from /media. After re-creating this and applying the permissions again the drive mounts on start up with no problem. Not sure why it thouhgt it was ntfs. it isn't. I don't care though. ITS FINALLY WORKING!!!

Thanks for your help.

I've been reading through your posts on this thread and I'm glad to hear it's finally working!!
Best of Luck ... Les ... [data recovery software]("http://www.mediarecover.com/")

---

