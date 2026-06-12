---
title: "USB Flash Drive Problems"
date: 2007-03-12
forum: General Help
---

### Post by overkillm on 2007-03-12
I'm a recent Ubuntu convert (Edgy, no custom kernel or anything fun like that)... please forgive my noobishness.  I know that questions regarding USB Flash drives and issues with hotplugging them exist in various threads here, and many of them touch upon the problem(s) I'm having, but none really seem to have directly solved them.  Sorry if I'm retreading old ground here. 

Here's the thing: When I plug in either of my two USB Flash drives (one 1-Gig, one 2-Gig), the device will show up in my Places->Computer window.  My Cruzer even goes so far as to show up as "SanDisk U3 Cruzer Micro" ... nice, that.  However, when I double-click the device icon, I get this:

Unable to mount the selected volume.
error: could not execute pmount

Now, I know that with pmount, the removable drives must not be in /etc/fstab, and they aren't.  I also know I need to be in the plugdev group for hotplugging/automounting to work properly, and according to the output of id, I am:

```

marcos@marcos-dell-ubuntu:~$ id
uid=1000(marcos) gid=114(admin) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),100(users),109(lpadmin),111(scanner),114(admin),1000(marcos)

```

Clearly I don't have the permissions to run pmount in my user account (is this all I need to correct, and if so, how?), but I thought the idea of pmount was to allow user-level mounts of devices not listed in fstab.  Maybe I misunderstood? Wouldn't be the first time.

I can do:
```
sudo mount /dev/sde1 /mnt/flash
```
and the Label of the drive will append itself to the device icon's text in the Computer window, and I will then be able to double-click the icon normally, and see the glorious contents.  (If I mount it to /media/whatever, though, the device icon disappears, although I can still access it through a filesystem window, or the terminal -- why is that?)  This work-around is fine, although I would like the drive to just pop up and work right without me having to open a Terminal.  

Also, when the drive is mounted (manually), it is always read-only.  It's formatted as FAT32, according to fdisk:

```

marcos@marcos-dell-ubuntu:~$ fdisk -l

Disk /dev/sda: 2055 MB, 2055021056 bytes
16 heads, 63 sectors/track, 3981 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3982     2006825    b  W95 FAT32


```

So the issue isn't that the flash drive is NTFS.  I could reformat the flash drive if needed, the contents have been backed up.  Should it be FAT16 instead of FAT32?

I want to be able to mount the flash drives as rw.  I tried chmod and chown on /dev/sde1, to no avail.  I didn't really think that would work, it was just an "I'm curious to see if something this dumb will work" kind of thing.  

I suppose I could sudo my way through writing any data to the drives, but I want to be able to do it via good ol' drag-and-drop in GNOME/Nautilus/other GUI.  It's not that I have any real aversion to the CLI (I cut my geek-teeth on DOS), I just want it to work the way I think it was meant to.  

"Mount removable drives when hot-plugged" and "Mount removable media when inserted" are both checked in System->Preferences->Removable Drives and Media Preferences.
"Access external storage devices automatically" is checked in System->Administration->Users settings. (that's just the GUI version of saying I'm in plugdev, right?)

Here's the output to some commands that seem to be asked of people with similar issues.  I'll post whatever other info may be required:

First, a tail of my /var/log/messages when I plug in my Flash drive:
```

marcos@marcos-dell-ubuntu:~$ tail -f /var/log/messages
Mar 11 23:53:05 marcos-dell-ubuntu kernel: [17216499.760000] sdc : status=0, message=00, host=1, driver=00 
Mar 11 23:53:05 marcos-dell-ubuntu kernel: [17216499.760000] sdc : sense not available. 
Mar 11 23:53:05 marcos-dell-ubuntu kernel: [17216499.760000] sdc: Write Protect is off
Mar 11 23:53:05 marcos-dell-ubuntu kernel: [17216499.760000] sdc : READ CAPACITY failed.
Mar 11 23:53:05 marcos-dell-ubuntu kernel: [17216499.760000] sdc : status=0, message=00, host=1, driver=00 
Mar 11 23:53:05 marcos-dell-ubuntu kernel: [17216499.760000] sdc : sense not available. 
Mar 11 23:53:05 marcos-dell-ubuntu kernel: [17216499.760000] sdc: Write Protect is off
Mar 11 23:53:05 marcos-dell-ubuntu kernel: [17216499.760000]  sdc:<3> 0:0:0:2: rejecting I/O to dead device
Mar 11 23:53:05 marcos-dell-ubuntu kernel: [17216499.760000]  unable to read partition table
Mar 12 00:02:49 marcos-dell-ubuntu kernel: [17217083.448000] usb 4-4: USB disconnect, address 9
Mar 12 00:05:53 marcos-dell-ubuntu kernel: [17217267.404000] usb 4-4: new high speed USB device using ehci_hcd and address 10
Mar 12 00:05:53 marcos-dell-ubuntu kernel: [17217267.536000] usb 4-4: configuration #1 chosen from 1 choice
Mar 12 00:05:53 marcos-dell-ubuntu kernel: [17217267.536000] scsi7 : SCSI emulation for USB Mass Storage devices
Mar 12 00:05:58 marcos-dell-ubuntu kernel: [17217272.540000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 3.21
Mar 12 00:05:58 marcos-dell-ubuntu kernel: [17217272.540000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Mar 12 00:05:58 marcos-dell-ubuntu kernel: [17217272.544000] SCSI device sda: 4013713 512-byte hdwr sectors (2055 MB)
Mar 12 00:05:58 marcos-dell-ubuntu kernel: [17217272.544000] sda: Write Protect is off
Mar 12 00:05:58 marcos-dell-ubuntu kernel: [17217272.548000] SCSI device sda: 4013713 512-byte hdwr sectors (2055 MB)
Mar 12 00:05:58 marcos-dell-ubuntu kernel: [17217272.548000] sda: Write Protect is off
Mar 12 00:05:58 marcos-dell-ubuntu kernel: [17217272.548000]  sda: sda1
Mar 12 00:05:58 marcos-dell-ubuntu kernel: [17217272.552000] sd 7:0:0:0: Attached scsi removable disk sda
Mar 12 00:05:58 marcos-dell-ubuntu kernel: [17217272.552000] sd 7:0:0:0: Attached scsi generic sg0 type 0

```

A df -h immediately afterward:

```

marcos@marcos-dell-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              48G  3.6G   42G   8% /
varrun                506M  132K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  152K  9.9M   2% /proc/bus/usb
udev                   10M  152K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/hda2              82G   47G   35G  58% /windows
/dev/hdb2             296G  161G  135G  55% /fattony
/dev/hda5              20G 1020M   19G   5% /shared

```

Here's my /etc/fstab:

```

marcos@marcos-dell-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3  ** Linux Root
UUID=12557214-b6b3-48ac-b964-8c2d3154b254 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2  ** Slartibartfast (Drive 1 - Windows Root) 
UUID=EC0CF4B90CF4803E /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2 ** Fat Tony
UUID=5AB6F65867650E26 /fattony        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5 ** Shared Partition on Drive 1
UUID=0A5F-92FB  /shared         vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1 ** Dell Utility Partition on Drive 1
UUID=07D3-011D  /dellutil1      vfat    defaults,utf8,noauto,umask=007,gid=46 0       1
# /dev/hdb3 ** Dell Utility Partition (copy) on Drive 2
UUID=4591-8C99  /dellutil2      vfat    defaults,utf8,noauto,umask=007,gid=46 0       1
# /dev/sde2 ** Wowbagger (FireWire Drive)
UUID=45D9-D9B9  /wowbagger      vfat    defaults,utf8,noauto,umask=007,gid=46   0       0
# /dev/hdb5 ** Linux Swap Space on Drive 2
UUID=5a7b187d-9413-4380-bb55-db73171fd8d3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0           /media/floppy0  auto    rw,user,noauto  0       0


```

My full, sudo'd fdisk -l:

```

marcos@marcos-dell-ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           6       48163+  16  Hidden FAT16
/dev/hda2   *           7       10602    85112370    7  HPFS/NTFS
/dev/hda3           13214       19457    50154930   83  Linux
/dev/hda4           10603       13213    20972857+   f  W95 Ext'd (LBA)
/dev/hda5           10603       13213    20972826    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1           38522       38913     3148740    f  W95 Ext'd (LBA)
/dev/hdb2               6       38521   309379770    7  HPFS/NTFS
/dev/hdb3               1           5       40131   16  Hidden FAT16
/dev/hdb5           38522       38913     3148708+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 2055 MB, 2055021056 bytes
16 heads, 63 sectors/track, 3981 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3982     2006825    b  W95 FAT32


```

And a lsusb just for fun:

```

marcos@marcos-dell-ubuntu:~$ lsusb
Bus 004 Device 010: ID 0781:5406 SanDisk Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:0405 Hewlett-Packard ScanJet 3400cse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Any help with the "cannot execute pmount" issue, and the read-only issue, would be greatly appreciated.  I have similar issues with my 40-in-1 or whatever-it-is card reader, although since I rarely have need to write to my camera's memory card the read-only thing isn't such a big deal there.

Sorry for the long post, I just wanted to cover the bases so I wouldn't look like I was just blindly asking questions without doing any independent research first.

Thanks again, in advance!  :D

---

### Post by colo on 2007-03-12
What's the output of `ls -l $(which pmount)`?

---

### Post by overkillm on 2007-03-12
Here's the output:

```

marcos@marcos-dell-ubuntu:~$ ls -l $(which pmount)
total 344
-r--r--r-- 1 marcos admin  174163 2006-07-02 12:29 Axialis Librarian
drwxr-xr-x 2 marcos marcos   4096 2007-03-01 22:04 Desktop
drwxr-xr-x 2 marcos marcos   4096 2007-02-16 15:17 Documents
drwxr-xr-x 6 marcos marcos   4096 2007-03-08 21:04 downloads
lrwxrwxrwx 1 marcos marcos     26 2007-02-05 16:57 Examples -> /usr/share/example-content
drwxr-xr-x 4 marcos admin    4096 2007-03-12 00:45 flashbackup
drwxr-xr-x 2 marcos admin    4096 2007-03-02 21:43 fonts
drwxr-xr-x 6 marcos admin    4096 2007-03-02 00:13 icons
-rw-r--r-- 1 marcos admin   99803 2007-03-11 13:52 my_bookmarks.html
drwxr-xr-x 2 marcos admin    4096 2007-03-11 17:04 Pictures
drwxr-xr-x 2 marcos admin    4096 2007-03-11 13:41 Templates
drwxr-xr-x 2 marcos admin    4096 2007-03-12 00:25 tmp
drwxr-xr-x 2 marcos marcos   4096 2007-02-19 11:15 torrents
-rw-r--r-- 1 root   root     4176 2007-02-27 21:18 xorg.conf.orig
-rw-r--r-- 1 marcos admin    6255 2007-02-27 21:29 xorg.conf.two
-rw-r--r-- 1 marcos admin    6255 2007-03-01 20:08 xorg.conf.works

```

Also... right after I made my initial post here I used gparted to reformat my 1-Gig Flash drive (not the Cruzer) as FAT32, in the hopes that a reformat would be all that was needed.  I still had the same problem afterward, had to manually mount the drive, and when I unmounted it, it took an excruciatingly long time to do.  Hoping someone can let me know what I screwed up, or if that was just a fluke.  Fortunately, this drive was a spare, so if I damaged it, no major harm done.

Gracias once again.

---

### Post by colo on 2007-03-12
Awkward - are you sure pmount is even installed/executeable?

```
find / -xdev -type f -a -name "pmount"
``` gives you what?

---

### Post by overkillm on 2007-03-12
I'm pretty sure I was able to run pmount via the terminal (I had to do sudo pmount, though) and it worked.  The icon in Nautilus disappeared when I did that, just as it did when I executed sudo mount /dev/sda1 /media/whatever 

I'm not at my home computer at the moment, but I will post the output of that command just as soon as I get home this evening.

A thought occurred to me earlier today... is this something that could be worked around by editing the sudoers file?  Should I even have to? Grr I'm itching to get home so I can mess with this some more...

Thanks! :D

---

### Post by overkillm on 2007-03-12
All right, here's the output:

```

marcos@marcos-dell-ubuntu:~$ sudo find / -xdev -type f -a -name "pmount"
Password:
/usr/bin/pmount

```

So it's there... it just doesn't like me.  :(

---

### Post by colo on 2007-03-13
Strange that it wasn't found by which, though...

What does ```
ls -l /usr/bin/pmount
``` give you?

---

### Post by overkillm on 2007-03-13
Shoot ... you know, looking back, I didn't sudo the command with the 'which' in it.  The output would probably have been different if I had.

Will post that, along with the output of the ls -l /usr/bin/pmount, as soon as I get home.

I did play around with the permissions of pmount last night, though... Originally they were set to 754. I chmod'd them to 755 and got "program must be setuid root" in addition to "could not execute pmount" when I double-clicked the Flash Drive icon in Nautilus.  So I flipped it back to 754 and was back down to getting just one error message.  Not sure if that's a clue to anything else...

Then I read somewhere that pmount permissions should be set to 4754 (this was in response to a similar issue but with a different sort of device... a PSP, I think?) ... so I chmod'd pmount to that, and still got the same error message.

I'm thinking now I want to toy around with udev rules files, see if that gets me anywhere.  Anyway, as soon as I get home I'll run those commands and post the outputs here.

Thanks for your help!

---

### Post by overkillm on 2007-03-13
Okay, well using sudo with 'ls -l $(which pmount)' didn't give me different output after all:

```

marcos@marcos-dell-ubuntu:~$ sudo ls -l $(which pmount)
total 676
-r--r--r-- 1 marcos admin  174163 2006-07-02 12:29 Axialis Librarian
drwxr-xr-x 2 marcos marcos   4096 2007-03-01 22:04 Desktop
drwxr-xr-x 2 marcos marcos   4096 2007-02-16 15:17 Documents
drwxr-xr-x 6 marcos marcos   4096 2007-03-08 21:04 downloads
lrwxrwxrwx 1 marcos marcos     26 2007-02-05 16:57 Examples -> /usr/share/example-content
drwxr-xr-x 4 marcos admin    4096 2007-03-12 00:45 flashbackup
drwxr-xr-x 2 marcos admin    4096 2007-03-02 21:43 fonts
drwxr-xr-x 6 marcos admin    4096 2007-03-02 00:13 icons
-rw-r--r-- 1 marcos users  333993 2007-03-12 22:04 my_bookmarks_2.html
-rw-r--r-- 1 marcos admin   99803 2007-03-11 13:52 my_bookmarks.html
drwxr-xr-x 2 marcos admin    4096 2007-03-11 17:04 Pictures
drwxr-xr-x 2 marcos admin    4096 2007-03-11 13:41 Templates
drwxr-xr-x 2 marcos admin    4096 2007-03-12 23:46 tmp
drwxr-xr-x 2 marcos marcos   4096 2007-02-19 11:15 torrents
-rw-r--r-- 1 root   root     4176 2007-02-27 21:18 xorg.conf.orig
-rw-r--r-- 1 marcos admin    6255 2007-02-27 21:29 xorg.conf.two
-rw-r--r-- 1 marcos admin    6255 2007-03-01 20:08 xorg.conf.works

```

... my mistake.

The output of 'ls -l /usr/bin/pmount':

```

marcos@marcos-dell-ubuntu:~$ ls -l /usr/bin/pmount
-rwsr-xr-- 1 root root 29860 2006-08-30 08:46 /usr/bin/pmount

```

:?

---

### Post by colo on 2007-03-13
Yeah well, no wonder it does not work for you.
Try ```
chown root:plugdev /usr/bin/pmount && chmod 4710 /usr/bin/pmount
```, and everything should be fine.

---

### Post by overkillm on 2007-03-13
Well okay, now I just feel stupid.

Of course the owner group was supposed to be plugdev...

I wonder why this wasn't the default of my Ubuntu install?  I backed up my original pmount file before I started mucking around with its permissions, and the backup also has the groupid set to root.

No matter... this worked perfectly.  Thank you very much for your help.

Now I'll just be over here, feeling dumb.

#-o

---

### Post by thommo on 2007-03-14
well I've just tried the same fix (as I have the exact same error) but it has not made a lick of difference for me.
Anyone with further ideas?

---

### Post by thommo on 2007-03-14
and interestingley I also have a similar error when trying to read from an SD card in my PCMCIA card reader:

mount: wrong fs type, bad option, bad superblock on /dev/sdb,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



mount: wrong fs type, bad option, bad superblock on /dev/sdb,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



error: could not execute pmount

---

### Post by ojthecat on 2007-03-14
I had the same problems and here is what I did that fixed it.

I was using the mount point /media/cdrom0 for mounting the drive 

I issued the following commands as root:

chmod 777 /media
chmod 777 /media/cdrom0
chmod 777 /media/cdrom1   

once I did this I inserted the drive and it automounted read-write. ---- yea!!!!

Hope this helps.

---

### Post by thommo on 2007-03-15
okay that didn't help.
I still get the following when I try and doubleclick the icon for the usb drive:
mount: no medium found

mount: no medium found

error: could not execute pmount

and running your code produced:
root@ibm-t21-ubuntu:~# chmod 777 /media
root@ibm-t21-ubuntu:~# chmod 777 /media/cdrom0
chmod: changing permissions of `/media/cdrom0': Read-only file system
root@ibm-t21-ubuntu:~# chmod 777 /media/cdrom1
chmod: cannot access `/media/cdrom1': No such file or directory

---

### Post by francesco44 on 2007-03-16
I have had the same kind of problems. Almost no answers in forum, as others have experienced if you follow the usb thread.

The only clue for me is that a usb key with a partition in the linux file system is recognized and mounted for that partition, the other partition is recognized but not mounted.

thanks to all

---

### Post by overkillm on 2007-03-16
This thread:

[http://www.linuxquestions.org/questions/showthread.php?t=373428]("http://www.linuxquestions.org/questions/showthread.php?t=373428")

shows similar issues, and someone suggests that corrupt partition tables may be the cuprit, and using fsck on the problem devices may help.  No idea if this would apply here, but I thought I'd share.

Running tail -f dmesg and then plugging in the problem device is usually suggested too... personally this often results in more head-scratching for me, but it does occasionally yield clues as well.

Now here is the standard disclaimer that I really don't know what I'm talking about, I'm as much a noob as anyone, and I'm just parroting what I've read elsewhere in the hopes that it may help.  :)      My lame version of taking part in the community...

---

