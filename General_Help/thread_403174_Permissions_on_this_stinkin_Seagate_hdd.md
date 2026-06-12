---
title: "Permissions on this stinkin Seagate hdd"
date: 2007-04-06
forum: General Help
---

### Post by lonelypauly on 2007-04-06
I have a Seagate 500GB External hdd that I was using just fine for several weeks,  (and yes, i formatted it wth FAT32) and now I need root permissions for this directory...the only problem is that I have tried changing them or accessing this drive and it doesn't work!  The name of my drive shows up in /media as "FreeAgent Drive"...but when i open the folder it does not show any of my files and when i try to copy n' paste it says that i dont have write permission...like WTF, over?  I never changed permissions as far as I can remember.  i can access the files in XP with no problem...can someone help me with this?  i would greatly appreciate it.

---

### Post by MoLE on 2007-04-16
I'm not an Ubuntu guru, but this should happen automagically with the Dapper, Edgy and Feisty.  Can you plug the drive in and give us the output of dmesg, /etc/mtab and ls -la /media/ ??

---

### Post by Sherlock Holmboy on 2007-04-19
I'm having this problem too. I can't write to the drive even as root:confused:

---

### Post by byorgey on 2007-04-20
I seem to be having the same problem.  Here's the output from the relevant commands:

```
[07:04:55 bj@homer:~]$ dmesg | tail -22
[21690563.292000] usb 1-1: new full speed USB device using uhci_hcd and address 19
[21690563.468000] usb 1-1: configuration #1 chosen from 1 choice
[21690563.476000] scsi11 : SCSI emulation for USB Mass Storage devices
[21690563.476000] usb-storage: device found at 19
[21690563.476000] usb-storage: waiting for device to settle before scanning
[21690568.476000] usb-storage: device scan complete
[21690568.480000]   Vendor: Seagate   Model: FreeAgentDesktop  Rev: 100D
[21690568.480000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[21690568.488000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[21690568.492000] sda: Write Protect is off
[21690568.492000] sda: Mode Sense: 1c 00 00 00
[21690568.492000] sda: assuming drive cache: write through
[21690568.496000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[21690568.500000] sda: Write Protect is off
[21690568.500000] sda: Mode Sense: 1c 00 00 00
[21690568.500000] sda: assuming drive cache: write through
[21690568.500000]  sda: sda1
[21690568.516000] sd 11:0:0:0: Attached scsi disk sda
[21690568.516000] sd 11:0:0:0: Attached scsi generic sg0 type 0
[21690570.296000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[21690570.300000] NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[21690570.548000] NTFS volume version 3.1.
[07:05:08 bj@homer:~]$ ls -la /media
total 20
drwxr-xr-x  5 root root 4096 2007-04-20 18:16 .
drwxr-xr-x 21 root root 4096 2007-02-11 07:58 ..
lrwxrwxrwx  1 root root    6 2005-11-19 07:19 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2005-11-19 07:19 cdrom0
lrwxrwxrwx  1 root root    7 2005-11-19 07:19 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2005-11-19 07:19 floppy0
dr-x------  1 bj   bj   4096 2007-03-02 00:18 FreeAgent Drive
[07:05:52 bj@homer:~]$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
tmpfs /lib/modules/2.6.17-11-386/volatile tmpfs rw,mode=0755 0 0
/dev/sda1 /media/FreeAgent\040Drive ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```

When I try to change the permissions:

```

[07:06:11 bj@homer:~]$ sudo chmod 700 /media/FreeAgent\ Drive/
Password:
chmod: changing permissions of `/media/FreeAgent Drive/': Read-only file system

```

Any ideas?  I'm running Edgy.

---

### Post by MoLE on 2007-04-20
> **byorgey said:**
> I seem to be having the same problem.  Here's the output from the relevant commands:

```

[21690570.296000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[07:05:08 bj@homer:~]$ ls -la /media
dr-x------  1 bj   bj   4096 2007-03-02 00:18 FreeAgent Drive
[07:05:52 bj@homer:~]$ cat /etc/mtab
/dev/sda1 /media/FreeAgent\040Drive ntfs 

```


Here's your problem:  the drive is formatted in NTFS.  Ubuntu doesn't include NTFS read-write support out-of-the-box just yet, although ntfs support is getting much better.

The giveaway is above: Flags: R/O MODULE. - read-only module.


> **byorgey said:**
> 
When I try to change the permissions:

```

[07:06:11 bj@homer:~]$ sudo chmod 700 /media/FreeAgent\ Drive/
Password:
chmod: changing permissions of `/media/FreeAgent Drive/': Read-only file system

```


chmod is just doing it's job - reminding you that the kernel has mounted this filesystem as read-only.

The simplest way around this is to back up your data, then refomat the drive using a different filesystem, such as FAT32.  
Alternatively you can enable read-write ntfs support, but it requires some work.  I'm pretty sure there's a howto on the [Ubuntu document storage facility]("http://doc.gwos.org/index.php/Main_Page").

Share and enjoy!

---

### Post by byorgey on 2007-04-20
ah, got it!  thanks.  Fortunately, this is a brand-new drive with no data on it, and I don't particularly care about interoperability with a certain other operating system, so I used gparted to reformat it as ext3.  Works like a charm!

---

### Post by Beefeater on 2007-06-11
> **byorgey said:**
> ah, got it!  thanks.  Fortunately, this is a brand-new drive with no data on it, and I don't particularly care about interoperability with a certain other operating system, so I used gparted to reformat it as ext3.  Works like a charm!

Which kernel do you use?

---

