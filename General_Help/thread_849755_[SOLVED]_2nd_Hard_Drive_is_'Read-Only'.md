---
title: "[SOLVED] 2nd Hard Drive is 'Read-Only'"
date: 2008-07-04
forum: General Help
---

### Post by ludatha on 2008-07-04
Hi, I have 2 Hard Drives, I want to use my second one, but it is read only.
It is: media/DATA

I have tried this command:
```
chmod a+rwx /path/to/folder
```

But that does nothing

I have also tried
```
sudo chown -R adam media/DATA
```
changed everything from read-only to read-only...

What do I do?
(right clicking on the file and changing it that way doesn't work)

---

### Post by logos34 on 2008-07-04
Shouldn't it be [COLOR=Red]**/**[/COLOR]media/DATA? (slash)

sudo chown -R adam /media/DATA

sudo chmod -R 777 /media/DATA

post your **sudo fdisk -l**, indicating which one you want to mount

---

### Post by ludatha on 2008-07-04
> Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4310    34620043+  83  Linux
/dev/sda2            4311        4500     1526175    5  Extended
/dev/sda5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS


I am asuming /dev/sdb1 , it is a 250GB HDD, and the one with linux on it is only 36 (10,000 rpm)

---

### Post by logos34 on 2008-07-04
oh, it's windows, I thought you were trying to mount an linux ext3

sudo apt-get install ntfs-config

gksudo ntfs-config

configure it there.  enable write support for 'internal' device.  it will edit /etc/fstab for you so it automounts with the ntfs-3g driver read-write

---

### Post by ludatha on 2008-07-04
OK, I did that, but I could only enable 'external' devices, 'internal' was grayed out :(

---

### Post by logos34 on 2008-07-04
ok, try this:

sudo mount -t ntfs-3g /dev/sdb1 /media/DATA

OR 

sudo mount -t ntfs /dev/sdb1 /media/DATA

If it works, add it to /etc/fstab.  But get the UUID first:

sudo vol_id /dev/sdb1

then,

gksudo gedit /etc/fstab

add:

> # /dev/sdb1
UUID=xxxx-xxxx... /media/DATA ntfs-3g defaults 0 0

---

### Post by ludatha on 2008-07-04
> adam@adam-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/DATA
Password:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
adam@adam-desktop:~$ sudo mount -t ntfs /dev/sdb1 /media/DATA
mount: /dev/sdb1 already mounted or /media/DATA busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/DATA
adam@adam-desktop:~$ sudo vol_id /dev/sdb1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=1A2EF2662EF239F9
ID_FS_LABEL=DATA
ID_FS_LABEL_SAFE=DATA
adam@adam-desktop:~$ gksudo gedit /etc/fstab


> # /dev/sdb1
UUID=UUID=1A2EF2662EF239F9 /media/DATA ntfs-3g defaults 0 0

It still doesn't work :/

but:
Mount is denied because NTFS logfile is unclean. Choose one action:
Boot Windows and shutdown it cleanly, or if you have a removable
device then click the 'Safely Remove Hardware' icon in the Windows
taskbar notification area before disconnecting it.

I would, but I formatted the drive to install ubuntu on it...

---

### Post by logos34 on 2008-07-04
it says the drive is already mounted:

>  mount: according to mtab, /dev/sdb1 is already mounted on /media/DATA??

try:

sudo umount /media/DATA

sudo mount -t ntfs-3g /dev/sdb1 /media/DATA -o force

---

### Post by ludatha on 2008-07-04
It seems that even if you uninstall windows, the problems will still come back to haunt you. If I copied all the data I needed on to a USB pen, then formatted the drive would it work?

---

### Post by logos34 on 2008-07-04
> **ludatha said:**
> It seems that even if you uninstall windows, the problems will still come back to haunt you. If I copied all the data I needed on to a USB pen, then formatted the drive would it work?

yeah, the 'unclean shutdown' syndrome can be a real pain to fix if you no longer have a bootable windows...if you copied it to usb stick it should be accessible.

But try unmounting and remounting first

---

### Post by ludatha on 2008-07-04
Hey, I found this thread:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

I followed it just now and it has enabled:
'Enable write support for internal device'

So I checked the box and clicked on ok and I get this:

> ** (ntfs-config:31012): WARNING **: Can't find device with uuid = UUID=1A2EF2662EF239F9

***
Remounting doesn't make it work...

---

### Post by logos34 on 2008-07-04
as far as the uuid goes, what do these commands show

sudo blkid

ls -l /dev/disk/by-uuid

EDIT: delete entry in fstab for sdb1, then try ntfs-config again

---

### Post by ludatha on 2008-07-04
Deleted entry in fstab, in ntfs-config, internal is grayed out again.

> adam@adam-desktop:~$ sudo blkid
Password:
/dev/sda1: UUID="d543342c-f100-4ad9-b6ad-cb1e8d4ac86d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="c53230d5-d543-4afd-8f9e-a16499ea4d8b" TYPE="swap" 
/dev/sdb1: TYPE="ntfs" 
adam@adam-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-07-05 00:11 1A2EF2662EF239F9 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-07-05 00:11 c53230d5-d543-4afd-8f9e-a16499ea4d8b -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-07-05 00:11 d543342c-f100-4ad9-b6ad-cb1e8d4ac86d -> ../../sda1
adam@adam-desktop:~$ 


---

### Post by ludatha on 2008-07-04
Do you want to do remote desktop?

---

### Post by logos34 on 2008-07-04
sorry for delay...

I see the second command reports same uuid (blkid is blank for some reason)...

umm, lets back up a bit: what about unmounting it, then remounting read-only ('-t ntfs')?  Copy off the files to your linux partition, reformat sdb1 (as ext3 unless you want ntfs for some reason), then copy it all back?

---

### Post by unutbu on 2008-07-04
I just happened to notice that way back when you posted your /etc/fstab entry that it said
> 
# /dev/sdb1
UUID=UUID=1A2EF2662EF239F9 /media/DATA ntfs-3g defaults 0 0

There shouldn't be UUID=UUID there. It should look more like

```
# /dev/sdb1
UUID=1A2EF2662EF239F9 /media/DATA ntfs-3g defaults 0 0
```

Perhaps try that if you haven't already.

---

### Post by ludatha on 2008-07-05
Ok,  I will do that, then post the outcome back...

---

### Post by ludatha on 2008-07-05
I have fixed my problem, thankyou for you help :)

---

