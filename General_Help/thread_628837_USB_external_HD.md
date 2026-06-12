---
title: "USB external HD"
date: 2007-12-01
forum: General Help
---

### Post by lift_test on 2007-12-01
Brand new install of Gutsy, plugged a USB HD in and no reaction.  How do you make it take notice?

PS Impressed, to check hardware, loaded W2k but it would only display at 800x640 whereas Gutsy displayed at full resolution straight away.

---

### Post by prodezigner on 2007-12-01
Do this before plugging it in...

sudo apt-get install ntfs-3g autofs

Then after that's done...

plug it in... open a terminal and type:

dmesg | tail

post your results (you may not hafta make it to the second part).

---

### Post by skymera on 2007-12-01
gutsy has ntfs-3g by default..

try

```
 sudo mount -a 
```

---

### Post by lift_test on 2007-12-02
Tried both, with no result except below:

vic@TIME:~$ sudo apt-get install ntfs-3g autofs
[sudo] password for vic:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
Recommended packages:
  nfs-common
The following NEW packages will be installed
  autofs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 112kB of archives.
After unpacking 483kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main autofs 4.1.4+debian-1 [112kB]
Fetched 112kB in 0s (127kB/s) 
Selecting previously deselected package autofs.
(Reading database ... 98160 files and directories currently installed.)
Unpacking autofs (from .../autofs_4.1.4+debian-1_i386.deb) ...
Setting up autofs (4.1.4+debian-1) ...

Creating config file /etc/auto.master with new version

Creating config file /etc/auto.misc with new version

Creating config file /etc/auto.net with new version

Creating config file /etc/auto.smb with new version

Creating config file /etc/default/autofs with new version
Starting automounter: loading autofs4 kernel module, no automount maps defined.

vic@TIME:~$ dmesg | tail
[88930.434374] sd 3:0:0:0: [sdb] Write Protect is off
[88930.434383] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[88930.434390] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[88930.439371] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[88930.442364] sd 3:0:0:0: [sdb] Write Protect is off
[88930.442371] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[88930.442376] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[88930.442384]  sdb: sdb1
[88938.141848] sd 3:0:0:0: [sdb] Attached SCSI disk
[88938.159539] sd 3:0:0:0: Attached scsi generic sg2 type 0
vic@TIME:~$ sudo mount -a
vic@TIME:~$ 

Also have an scsi hard disk which shows but cannot be mounted/unmounted/viewed (I think formated NFTS),  any ideas?

---

### Post by lift_test on 2007-12-02
Just tried rebooting with USB disk plugged in and it appeared on the desktop.  Thanks, only need to get SCSI disk sorted now.

---

### Post by missed her show on 2007-12-02
hi all, i have a Maxtor OneTouch III USB2 External Hard drive that i'm having difficulty mounting in Ubuntu G. 

When i first booted from the Live CD, it recognized the drive and it's contents without any prodding from me. 

But then i installed Ubuntu and now i can't Mount the drive.    I've followed the suggestions in this thread and still no dice.

Here's the error message:

> $LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sbd1': Operation not supported  Mount is denied because NTFS is marked to be in use.  Choose 1 action:  Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the windows  taskbar then shutdown windows cleanly.   Choice 2:  If you don't have windows then you can use the 'force' option for your own responsibility.  for example type on the command line:  Mount -t ntfs-3g /dev/sdb1 /media/New Volume -o force    or add the option to the relevant row in the /etc/fstab file:     /dev/sdb1 /media/New Volume ntfs-3g defaults, force 0,0

I'm new to ubuntu, decided to ditch windows, so ANY Help would be greatly appreciated.   (BTW, the external HD is filled with data....i don't want to have to reformat it.)

thanx for the help

---

### Post by matthewcraig on 2007-12-02
Just for comparison, I have two different types of external hard drives, and both automount right away upon connection to a computer running Ubuntu OS.

---

### Post by missed her show on 2007-12-02
it's really wierd, because i could access the files on the external HDD when i booted from the LIVE cd...but once i installed, it appears as the New Volume, but i'm unable to mount it.

---

### Post by missed her show on 2007-12-02
when i run a sudo fdisk -l


here's what i get (for the USB device):


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          42       40131    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdb2              42       40649    39022861    b  W95 FAT32


shoot, i'm at a loss....anyone have any ideas?

---

