---
title: "Mount Points and fstab"
date: 2016-09-12
forum: General Help
---

### Post by Quarkrad on 2016-09-12
Running 16.04.  This is my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sdb8 :
UUID=8c70f45a-3135-455e-bce1-a56fb36f031d	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb6 :
UUID=B8D5-D2A0	/boot/efi	vfat	umask=0077	0	1
#Entry for /dev/sdb9 :
UUID=5fa872e8-bc99-40cb-a865-7eed00a039e5	/home	ext4	defaults	0	2
#Entry for /dev/sdb5 :
#UUID=56DCD364DCD33CC5	/media/Recovery	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=240244231FC9CD88	/media/backup	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb1 :
#UUID=41486E9C761FCAA7	/media/sdb1	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb11 :
UUID=423572E86D3F849D	/media/store1	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=59B8B755039E0057	/media/store2	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb4 :
#UUID=303610AF035717E1	/media/windows10	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb10 :
UUID=da513e28-4f5c-4708-83a5-634a02dcf455	none	swap	sw	0	0
```

Everything works OK - my 16.04 system is on sdb8 and I have a separate partition for /home sdb9.  I'm struggling with the attached - it shows the listing under /media. I do not know what instructs this graphic to show store_1 and store_2

---

### Post by DuckHook on 2016-09-12
The Linux convention is to mount fstab entries for permanently available media like built-in HDDs and SSDs in /mnt

/media is reserved for system automounts of detachable media like USB sticks, cards and external HDDs/SSDs.

Nothing forces you to observe this convention: it's just a convention. As you have both seen and done, you can choose to mount stuff to /media. However, this leads to the possibility of confusion, as seems to be happening in your case.

Do you have external devices connected to your computer through USB or external SATA? If so, you might expect them to show up as the "store_1" and "store_2" designations that you see. To see what block devices are hooked up to your computer, do:```
sudo blkid
```This also shows the UUIDs associated with each. You may find that "store_1" and "store_2" refer to duplicate devices.

---

### Post by TheFu on 2016-09-12
Disk labels, perhaps? I dunno.

BTW, I find that it is best to avoid putting any manually mounted storage under /media/. That area is for Linux automatic mounts that we have ZERO control over. If you go to the effort to manually mount storage in the fstab, why not put it where you want it with names you like?

Why so much NTFS storage? Ewww.

Image is too small. Can't read anything.

Thakns for the code tags! Appreciated.

---

### Post by Quarkrad on 2016-09-13
Sorry about the code tags - here is my fstab followed by Blkid

Fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sdb8 :
UUID=8c70f45a-3135-455e-bce1-a56fb36f031d	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb6 :
UUID=B8D5-D2A0	/boot/efi	vfat	umask=0077	0	1
#Entry for /dev/sdb9 :
UUID=5fa872e8-bc99-40cb-a865-7eed00a039e5	/home	ext4	defaults	0	2
#Entry for /dev/sdb5 :
#UUID=56DCD364DCD33CC5	/media/Recovery	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=240244231FC9CD88	/media/backup	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb1 :
#UUID=41486E9C761FCAA7	/media/sdb1	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb11 :
UUID=423572E86D3F849D	/media/store1	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=59B8B755039E0057	/media/store2	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb4 :
#UUID=303610AF035717E1	/media/windows10	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb10 :
UUID=da513e28-4f5c-4708-83a5-634a02dcf455	none	swap	sw	0	0


```


Blkid

```
dad@dadubuntu:~$ sudo blkid
[sudo] password for dad: 
/dev/sda1: LABEL="store 2" UUID="59B8B755039E0057" TYPE="ntfs" PARTUUID="72751ad4-01"
/dev/sdb2: SEC_TYPE="msdos" LABEL="uefi" UUID="F6E3-B05D" TYPE="vfat" PARTUUID="15d5dca7-6fa7-45bc-9153-efb0409bff3c"
/dev/sdb3: PARTUUID="67a8dfdd-cf59-47ae-ad4c-1ba03f2d8f16"
/dev/sdb4: LABEL="windows 10" UUID="303610AF035717E1" TYPE="ntfs" PARTUUID="b3505af7-5a11-4a8a-b4a0-e5c1227734cd"
/dev/sdb5: LABEL="Recovery" UUID="56DCD364DCD33CC5" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="6e850663-b8f3-48c0-a0af-4ec923adf70a"
/dev/sdb6: UUID="B8D5-D2A0" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="5c2ea1fc-e3fa-40b1-a538-333e1b0f53ec"
/dev/sdb7: PARTLABEL="Microsoft reserved partition" PARTUUID="f465c273-c96d-4760-bf43-3d50e8f0c10b"
/dev/sdb8: UUID="8c70f45a-3135-455e-bce1-a56fb36f031d" TYPE="ext4" PARTUUID="9a1b8ff8-95b0-4006-90e2-a904a9e96b0a"
/dev/sdb9: UUID="5fa872e8-bc99-40cb-a865-7eed00a039e5" TYPE="ext4" PARTUUID="f959e527-0ed5-494d-bdec-2f72bf2dc3e6"
/dev/sdb10: UUID="da513e28-4f5c-4708-83a5-634a02dcf455" TYPE="swap" PARTUUID="dacbbfce-a5d9-4d02-bec1-b35f9444ca20"
/dev/sdb11: LABEL="store 1" UUID="423572E86D3F849D" TYPE="ntfs" PARTUUID="f0466a5c-30c0-4c8c-9f0f-85479ae52db0"
/dev/sdc1: LABEL="backup" UUID="240244231FC9CD88" TYPE="ntfs" PARTUUID="0004f127-01"
```

So ...  store_1 and store_2 are not listed in Blkid

General. 

I have no external devices connected to my system
I have 3 physical HDs:
sda is a single partition hd labeled store2, ntfs just for data 
sdb is a multi partitioned hd with windows 10, /, /home, store1 and swap.  Mix ext4 and ntfs
sdc is a single partition hd labeled Backup, ntfs  (used as backup for sda and sdb)

I have used a similar setup (sometimes with only two HDs) since 8.04 and I always find the 'data' partitions and Backup partition appear automatically in /media.

The reason I configure my data and backup partitions as ntfs goes way back to my Windows days and file recovery when things go wrong.  I came across some recovery software that is really effective - recovered data even when an hd had been wiped and a new version of winxp installed on it.  I have just discovered that the manufacturer of this recovery software now supports Ext4 so perhaps I could now move into the 20th century and have all my partitions (store1, store2 and Backup) configured as Ext4.

I'm also intrigued why **dad** appears under /media - my user name is **dad** so my home directory is /home/dad.  I'm wondering whether at this point I should reconfigure store1, store2 and Backup as Ext4 rather than carry on with this thread.

---

### Post by Morbius1 on 2016-09-13
> I'm also intrigued why dad appears under /media - my user name is dad so my home directory is /home/dad.
Because removable devices no longer mount under /media. They mount under /media/$USER ( /media/dad in this case ) in Ubuntu. In other branches of Linux they mount under /run/media/$USER. So the old rule that you should never mount something directly under /media is less relevant today.

There is one peculiarity about mounting something under /media however and that is how it's displayed. Regardless of the name of the mount point it will display it's LABEL on the side panel of the file manager instead. WHat I can't explain are these underscores being displayed everywhere - at least in the absence of any external partition connected to this system with a duplicate label.

You might want to run blkid a different way to see if they match with your previous output:
```
sudo blkid -c /dev/null -o list
```

In general it's best not to have spaces in labels so you might consider using something like gparted to change the labels from something like "store 1" to "store1" if for no other reason than to have the LABEL and mount point name match.

---

### Post by Quarkrad on 2016-09-13
This is the output:

```
dad@dadubuntu:~$ sudo blkid -c /dev/null -o list
[sudo] password for dad: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    store 2  /media/store2  59B8B755039E0057
/dev/sdb2  vfat    uefi     (not mounted)  F6E3-B05D
/dev/sdb3                   (not mounted)  
/dev/sdb4  ntfs    windows 10 (not mounted) 303610AF035717E1
/dev/sdb5  ntfs    Recovery (not mounted)  56DCD364DCD33CC5
/dev/sdb6  vfat             /boot/efi      B8D5-D2A0
/dev/sdb7                   (not mounted)  
/dev/sdb8  ext4             /              8c70f45a-3135-455e-bce1-a56fb36f031d
/dev/sdb9  ext4             /home          5fa872e8-bc99-40cb-a865-7eed00a039e5
/dev/sdb10 swap             [SWAP]         da513e28-4f5c-4708-83a5-634a02dcf455
/dev/sdb11 ntfs    store 1  /media/store1  423572E86D3F849D
/dev/sdc1  ntfs    backup   /media/backup  240244231FC9CD88
dad@dadubuntu:~$ 

```

I'm going to do some testing and change the partitions to ext4 and change the labels to have no spaces - thank you all.  Will wait until I close thread.

---

### Post by Morbius1 on 2016-09-13
Though I saw something else in the output. Never mind.

---

