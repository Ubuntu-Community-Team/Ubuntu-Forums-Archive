---
title: "usb key and drive won't mount in hardy"
date: 2008-05-07
forum: General Help
---

### Post by lecter255 on 2008-05-07
I am pretty new to Ubuntu so i searched up some thread on this topic but don't really understand them.
Anyways, I did a fresh install of 8.04. In gutsy, I just plug in my usb key and I can open it. In hardy, I plug it in and I try to click it open and it says

"Invalid mount option when trying to mount volume 'UBUNTU 804'" UBUNTU 804 is the name of my usb key. how do open this usb key? It's int FAT32 format.

---

### Post by hmarkg on 2008-05-07
I'm also having the same problem. Recently I just upgraded to ubuntu 8.04 LTS and i cant seem to be able to mount my external hard disk (NTFS format). I even tried to force mount it but it didnt work. HELP...!!!

---

### Post by lecter255 on 2008-05-07
yea i have an external hard drive too, NTFS, and I can't mount that either.

c'mon guys 30 views and no solution for this seemingly easy problem? am i posting in the wrong section?

---

### Post by prshah on 2008-05-07
> **lecter255 said:**
>  In gutsy, I just plug in my usb key and I can open it. In hardy, I plug it in and I try to click it open and it says

"Invalid mount option when trying to mount volume 'UBUNTU 804'

> **hmarkg said:**
> I'm also having the same problem. and i cant seem to be able to mount my external hard disk (NTFS format).

Can both of your please post the output of ```
dmesg | tail
cat /var/log/messages | tail
``` immediately _after_ plugging in the usb device?

---

### Post by lecter255 on 2008-05-07
> **prshah said:**
> Can both of your please post the output of ```
dmesg | tail
cat /var/log/messages | tail
``` immediately _after_ plugging in the usb device?


here you go

asdf@asdf-laptop:~$ dmesg | tail
[ 1414.757869] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1414.762341] sd 4:0:0:0: [sdb] 1952768 512-byte hardware sectors (1000 MB)
[ 1414.763620] sd 4:0:0:0: [sdb] Write Protect is off
[ 1414.763623] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1414.763626] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1414.763631]  sdb: sdb1
[ 1414.799161] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1414.799219] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1416.820615] UDF-fs: No partition found (1)
[ 1417.099476] ISOFS: Unable to identify CD-ROM format.
asdf@asdf-laptop:~$ cat /var/log/messages | tail
May  7 17:02:09 asdf-laptop kernel: [ 1414.748754] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
May  7 17:02:09 asdf-laptop kernel: [ 1414.756255] sd 4:0:0:0: [sdb] 1952768 512-byte hardware sectors (1000 MB)
May  7 17:02:09 asdf-laptop kernel: [ 1414.757859] sd 4:0:0:0: [sdb] Write Protect is off
May  7 17:02:09 asdf-laptop kernel: [ 1414.762341] sd 4:0:0:0: [sdb] 1952768 512-byte hardware sectors (1000 MB)
May  7 17:02:09 asdf-laptop kernel: [ 1414.763620] sd 4:0:0:0: [sdb] Write Protect is off
May  7 17:02:09 asdf-laptop kernel: [ 1414.763631]  sdb: sdb1
May  7 17:02:09 asdf-laptop kernel: [ 1414.799161] sd 4:0:0:0: [sdb] Attached SCSI removable disk
May  7 17:02:09 asdf-laptop kernel: [ 1414.799219] sd 4:0:0:0: Attached scsi generic sg2 type 0
May  7 17:02:11 asdf-laptop kernel: [ 1416.820615] UDF-fs: No partition found (1)
May  7 17:02:12 asdf-laptop kernel: [ 1417.099476] ISOFS: Unable to identify CD-ROM format.

---

### Post by Do0odz on 2008-05-08
> **prshah said:**
> Can both of your please post the output of ```
dmesg | tail
cat /var/log/messages | tail
``` immediately _after_ plugging in the usb device?

I too facing the same problem :S here's my output

May  8 22:43:57 Do0oDz kernel: [ 7798.716904] usbcore: registered new interface driver usb-storage
May  8 22:43:57 Do0oDz kernel: [ 7798.716910] USB Mass Storage support registered.
May  8 22:44:02 Do0oDz kernel: [ 7803.714664] scsi 6:0:0:0: Direct-Access     TOSHIBA  MK1246GSX             PQ: 0 ANSI: 2
May  8 22:44:02 Do0oDz kernel: [ 7803.723591] sd 6:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  8 22:44:02 Do0oDz kernel: [ 7803.726254] sd 6:0:0:0: [sdb] Write Protect is off
May  8 22:44:02 Do0oDz kernel: [ 7803.728109] sd 6:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
May  8 22:44:02 Do0oDz kernel: [ 7803.730617] sd 6:0:0:0: [sdb] Write Protect is off
May  8 22:44:02 Do0oDz kernel: [ 7803.730634]  sdb: sdb1
May  8 22:44:02 Do0oDz kernel: [ 7803.742764] sd 6:0:0:0: [sdb] Attached SCSI disk
May  8 22:44:02 Do0oDz kernel: [ 7803.742834] sd 6:0:0:0: Attached scsi generic sg2 type 0

---

### Post by Anxiety35 on 2008-05-08
Since the update I've also been having trouble getting my external and even my internal windows partition to mount.

This is my output. I don't see any errors or anything like that, but I can't access the drive at all:
> May  8 13:56:18 william-laptop kernel: [13182.395200] usb 5-5: new high speed USB device using ehci_hcd and address 14
May  8 13:56:19 william-laptop kernel: [13184.753173] usb 5-5: new high speed USB device using ehci_hcd and address 15
May  8 13:56:22 william-laptop kernel: [13188.360267] scsi 3:0:0:0: Direct-Access     WDC WD50 00AAJS-22TKA0         PQ: 0 ANSI: 2 CCS
May  8 13:56:22 william-laptop kernel: [13186.312862] sd 3:0:0:0: [sdb] 1953546336 512-byte hardware sectors (1000216 MB)
May  8 13:56:22 william-laptop kernel: [13186.313900] sd 3:0:0:0: [sdb] Write Protect is off
May  8 13:56:22 william-laptop kernel: [13186.315269] sd 3:0:0:0: [sdb] 1953546336 512-byte hardware sectors (1000216 MB)
May  8 13:56:22 william-laptop kernel: [13186.316022] sd 3:0:0:0: [sdb] Write Protect is off
May  8 13:56:22 william-laptop kernel: [13186.316037]  sdb: sdb1 sdb2
May  8 13:56:22 william-laptop kernel: [13186.324415] sd 3:0:0:0: [sdb] Attached SCSI disk
May  8 13:56:22 william-laptop kernel: [13186.324483] sd 3:0:0:0: Attached scsi generic sg2 type 0

---

### Post by prshah on 2008-05-09
> **lecter255 said:**
> here you go
asdf@asdf-laptop:~$ dmesg | tail


> **Do0odz said:**
> I too facing the same problem :S here's my output


> **Anxiety35 said:**
> This is my output. I don't see any errors or anything like that, but I can't access the drive at all:

All your outputs look fine to me, no errors... maybe ```
sudo fdisk -l
``` when the device is sitting plugged in?

---

### Post by lecter255 on 2008-05-09
i get this when I do "sudo fdisk -l"

asdf@asdf-laptop:~$ sudo fdisk -l
[sudo] password for asdf: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61ee3727

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17622   141546793    7  HPFS/NTFS
/dev/sda2           18643       19457     6546487+   7  HPFS/NTFS
/dev/sda3           18519       18642      996030   82  Linux swap / Solaris
/dev/sda4           17623       18518     7197120   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 999 MB, 999817216 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045ce4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         121      971901    b  W95 FAT32


my internal hard drive's partitions mount fine. the device with 999 MB is my USB stick

---

### Post by wabbster on 2008-05-09
Can you try this: [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

and see if that method works?

Good Luck,
Wabb.

---

### Post by lecter255 on 2008-05-09
ah something promising. it auto mounted my other internal ntfs drives but i have yet to try my external usb drive. it still won't mount my FAT32 usb key though, but that's expected, since the link is for ntfs drives

---

### Post by wabbster on 2008-05-09
Do you see the drive name in the 'Places' menu? If so, clicking it would probably mount the drive. It will probably ask for your password or something like that. Of course, all this is only if you see the drive in the menu.

Wabb.

---

### Post by wabbster on 2008-05-09
These might be of some use:

[http://ubuntuforums.org/showthread.php?t=773996](http://ubuntuforums.org/showthread.php?t=773996)

or

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


Good luck,
Wabb.

---

### Post by Anxiety35 on 2008-05-09
Those solutions didn't work. NTFS Config Tool doesn't see it, and the fix that tells you to remove a line in the config editor didn't work because that line wasn't there.

Also, it shows up in my "Places" but when I click, nothing happens.

Here's what I get from sudo fdisk -l

The external drive is the sdb at the bottom, but one of the sda's is a windows partition that won't mount either.
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1314        7607    50556555    7  HPFS/NTFS
/dev/sda4            7610       19458    95169731+   f  W95 Ext'd (LBA)
/dev/sda5           19197       19458     2096128   dd  Unknown
/dev/sda6   *        7610       19062    91996159+  83  Linux
/dev/sda7           19063       19196     1076323+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000215724032 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29f8a798

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488385536    7  HPFS/NTFS
/dev/sdb2           60802      121603   488385536    7  HPFS/NTFS


Also, when suspending my computer one time, when it shows all those [ok] checks, one of them failed. I believe it was one that I had seen referenced to hard drives. I believe it was something about mtab. Does that make sense?

edit: Neither my windows portion nor my external hard drive are listed in my fstab file. Is this my problem? If so, how do I fix this?

---

### Post by lecter255 on 2008-05-09
> **wabbster said:**
> Do you see the drive name in the 'Places' menu? If so, clicking it would probably mount the drive. It will probably ask for your password or something like that. Of course, all this is only if you see the drive in the menu.

Wabb.

i see the external drive in "places" but when i click and it will just say error with mount point or something. same thing with the usb key

---

### Post by yellowbread on 2008-05-10
This sounds like the same problem I had. Check your fstab. Here's mine:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=828119da-e674-4e58-add0-241132c4274c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=c35705e8-ef8f-4837-a303-9a7ed0048b06 /home           ext3    relatime        0       2
# /dev/sdb1
UUID=0a55c19c-cfc3-41f8-a1cd-702503a88125 /media/Gutsy    ext3    relatime        0       2
# /dev/sda4
UUID=D0DC3593DC3574B6 /media/WindowsData ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=4a48be5f-3f29-4658-b5d0-9cced5969190 /media/hardybeta ext3    relatime        0       2
# /dev/sdb2
UUID=bbef68bc-4510-4a31-a436-9c12d052181a none            swap    sw              0       0
#/dev/sdd3       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Notice the second to last line that is commented out. That was the entry put in for my usb flash drive at installation time. Until I commented it out, I had the same symptoms as you are describing.

---

### Post by vanadium on 2008-05-10
* Check the file systems on the devices where you have problems. Ubuntu won't mount file systems that are not in a good state.
* Check wether a device is mounted using the "mount" command. It is not because you do not find an icon somewhere that the device is not mounted.

---

### Post by gzevspero on 2008-05-11
Nice - I'd been having the same problem and yellowbread's fstab solution worked for me too. Thanks.

---

### Post by lecter255 on 2008-05-13
> **yellowbread said:**
> This sounds like the same problem I had. Check your fstab. Here's mine:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=828119da-e674-4e58-add0-241132c4274c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=c35705e8-ef8f-4837-a303-9a7ed0048b06 /home           ext3    relatime        0       2
# /dev/sdb1
UUID=0a55c19c-cfc3-41f8-a1cd-702503a88125 /media/Gutsy    ext3    relatime        0       2
# /dev/sda4
UUID=D0DC3593DC3574B6 /media/WindowsData ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=4a48be5f-3f29-4658-b5d0-9cced5969190 /media/hardybeta ext3    relatime        0       2
# /dev/sdb2
UUID=bbef68bc-4510-4a31-a436-9c12d052181a none            swap    sw              0       0
#/dev/sdd3       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Notice the second to last line that is commented out. That was the entry put in for my usb flash drive at installation time. Until I commented it out, I had the same symptoms as you are describing.

hi, where is this fstab and do I just use gedit to edit it?

---

### Post by lecter255 on 2008-05-13
wait i got it

fstab was in etc in home directory

ahhh finally. thanks a lot!!!

---

### Post by flat11 on 2008-06-07
yellowbread thanks for your tip, saved me a lot of headache!
Now I can access my Maxtor usb external hdd again!

---

### Post by zivley on 2008-09-23
Thanks yellowbread!!! How could I miss that one?? I had the same problem, it seems that whenever you're using the USB drive while installing (I installed FROM a USB Drive) it keeps that line in /etc/fstab , I commented it out and everything is fine now.
Thanks!
Ziv

---

### Post by bikerman2299 on 2009-03-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1cc335cc-8cfe-4ca7-b8e0-c39d79dec4e7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a8b6c509-438d-4a61-a8c3-79b07d2558f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I still cannot mount my external. I am looking at it right here, but I have no access to it. /dev/sda5 is my external. Sda1 is my internal, and the cdrom is obvious. I am still way new to Ubuntu, thanks for the help!

---

### Post by bikerman2299 on 2009-03-26
So another thing I was looking at was my system monitor. it says /dev/sda5 is my internal HD. It doesn't show sda1 at all. Is my sysmonitor and my /etc/fstab is backwards? like labeled incorrectly? I thought I almost had it, but my ntfs config tool showed up, but it still won't pull anything up. Thank you so much for the help.

---

### Post by prshah on 2009-03-27
> **bikerman2299 said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1cc335cc-8cfe-4ca7-b8e0-c39d79dec4e7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a8b6c509-438d-4a61-a8c3-79b07d2558f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I still cannot mount my external. I am looking at it right here, but I have no access to it. /dev/sda5 is my external. Sda1 is my internal, and the cdrom is obvious. I am still way new to Ubuntu, thanks for the help!

Sorry, but you've got it all wrong.

a) /dev/sda5 is not your external; it is the internal drive.
b) /dev/sda5 is not usable (directly) by you; it is a "swap" drive, and only the operating system accesses it.
c) Your external drive will not be sda; it will be sdb or sdc and so on.
d) Your external drive should automatically mount when you plug it in. (Just like in Windows)
e) If your external drive is not automatically mounting, try the following for more information:
[indent]
i. If the drive is plugged in, unplug it.
ii. Open a terminal (Applications-Accessories-Terminal)
iii. Plug in the drive, then give this command in the terminal```
sleep 15 && dmesg | tail
```
iv. Post back the result of the above command for more relevant troubleshooting.
v. I suspect that you have not safely unmounted (safely remove hardware) when you were using it in Windows.
[/indent]

Post back with the above information for a proper resolution.

---

### Post by bikerman2299 on 2009-03-27
sleep 15 && dmesg | tail
[  240.253964] sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  240.253967] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  240.255697] sd 2:0:0:0: [sdb] 3907017568 512-byte hardware sectors (2000393 MB)
[  240.256568] sd 2:0:0:0: [sdb] Write Protect is off
[  240.256574] sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  240.256577] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  240.256581]  sdb: sdb1 sdb2 sdb3
[  240.265839] sd 2:0:0:0: [sdb] Attached SCSI disk
[  240.265902] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  240.266027] scsi 2:0:0:1: Attached scsi generic sg3 type 13


Thanks you so much! I knew I was way new to Ubuntu. I really appreciate it! This external is straight out of the box. It hasn't been plugged into anything else. Thank you for your help.

---

### Post by prshah on 2009-03-30
> **bikerman2299 said:**
> 
[  240.256581]  sdb: sdb1 sdb2 sdb3


Everything looks fine; your external is recognized and assigned /dev/sdb; each partition within it (looks like 3 partitions) are assigned sdb1, sdb2 and sdb3.

If this is a new drive, it may need to be formatted. Formatting will erase any data already on the drive, so please be careful in which drive (/partition) you select.

To confirm this, or for further steps on how to use / prepare your drive, plug it in, then open the terminal, and give the commands (one after another, don't copy/paste both lines at a go)```
sleep 15 && sudo fdisk -l
mount | grep sdb
``` and post back the full information. (btw, the "-l" following the fisk command is "minus lowercase-letter-L", and not "minus one")

---

### Post by bikerman2299 on 2009-04-08
Hi, sorry it took me so long to get back to you. I was flying back to Iraq, and the military travel system is not the most efficent. Anyways this is what I got. 

 sleep 15 && sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11784    94654948+  83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris

Disk /dev/sdc (Sun disk label): 255 heads, 63 sectors, 46592 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System
/dev/sdc1             0    243194 -194027843   83  Linux native
/dev/sdc2  u     243194    243200     48195   82  Linux swap
/dev/sdc3             0    243200 -193979648    5  Whole disk

Disk /dev/sdc1 (Sun disk label): 255 heads, 63 sectors, 46592 cylinders
Units = cylinders of 16065 * 512 bytes

    Device Flag    Start       End    Blocks   Id  System
/dev/sdc1p1             0    243194 -194027843   83  Linux native
/dev/sdc1p2  u     243194    243200     48195   82  Linux swap
/dev/sdc1p3             0    243200 -193979648    5  Whole disk

Disk /dev/sdc3 (Sun disk label): 255 heads, 63 sectors, 46592 cylinders
Units = cylinders of 16065 * 512 bytes

    Device Flag    Start       End    Blocks   Id  System
/dev/sdc3p1             0    243194 -194027843   83  Linux native
/dev/sdc3p2  u     243194    243200     48195   82  Linux swap
/dev/sdc3p3             0    243200 -193979648    5  Whole disk

The other command just bumped me right back to the prompt. I didn't show anything.

---

### Post by bikerman2299 on 2009-04-09
Bump

I have been kinda over worked the last few days. My brain is mostly mush. This current now. I had a friend format the external into NTFS. Now, I can see it in my places folder. The error is this:

Unable to mount location
Can't mount file. 

This is what this sleep 15 && sudo fdisk -l  pulls up. 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11784    94654948+  83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 2000.3 GB, 2000392994816 bytes
255 heads, 63 sectors/track, 243200 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc3dd011

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243200  1953503968+   7  HPFS/NTFS

Its a two TB drive. I tried this, mount | grep sdb but it still won't mount. any help? 

This is my fstab

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1cc335cc-8cfe-4ca7-b8e0-c39d79dec4e7 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=a8b6c509-438d-4a61-a8c3-79b07d2558f7 /dev/sda5 /mnt/ntfs-sys ntfs 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Thank you for the help!

---

### Post by bikerman2299 on 2009-04-09
Ok, so I did some stuff. I have a few more questions for you though. This is my new fstab

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1cc335cc-8cfe-4ca7-b8e0-c39d79dec4e7 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=a8b6c509-438d-4a61-a8c3-79b07d2558f7 /dev/sda5 /mnt/ntfs-sys ntfs 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Entry for /dev/sdb1 :
UUID=AC5C04885C044F8E /media/usb ntfs 0 0 0

Notice the last two lines. I pulled up my UUID for the sdb1 and added it. this was the command for getting by UUID: ls /dev/disk/by-uuid -lah

Then, I made a mount point: mkdir /media/usb

after that, this command did the rest. 

 mount -t ntfs-3g /dev/sdb1 /media/usb -o force

now I have access to the the 2 TB. I am pulling some info off it right now, then I will see I am can rrw to the drive. The question I have now, is if I reboot and leave the extern plugged in, will it auto mount, since I added those last two lines to my fstab? Or, will I have to force mount it each time? I tried running ntfs config, and it doesn't do anything for me. I would rather not force mount my drive. But, this is the only way I have gotten it to work. Thanks!! 

Signed a newbie

---

### Post by choben on 2009-08-28
thanks... the fstab edit worked for me too, but I'm still curious; If it wasn't mounting before, does that mean there was an error on my usb drive's filesystem?

---

### Post by choben on 2009-08-28
> **zivley said:**
> Thanks yellowbread!!! How could I miss that one?? I had the same problem, it seems that whenever you're using the USB drive while installing (I installed FROM a USB Drive) it keeps that line in /etc/fstab , I commented it out and everything is fine now.
Thanks!
Ziv

Oh I see now... I was actually wondering if being bootable had something to do with it >.< like Ubuntu freaking out haha

---

