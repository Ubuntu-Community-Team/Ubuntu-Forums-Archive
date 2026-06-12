---
title: "automount flash drive"
date: 2007-01-02
forum: General Help
---

### Post by mega on 2007-01-02
I'm using a hp printer, which has a cardreader

it was auto mounting my sd card, several months ago


now it only does this..

[17615483.992000] SCSI device sdb: 1984000 512-byte hdwr sectors (1016 MB)
[17615483.992000] sdb: Write Protect is off
[17615483.992000] sdb: Mode Sense: 17 00 00 08
[17615483.992000] sdb: assuming drive cache: write through
[17615483.992000]  sdb: sdb1


never mounts the drive

any idea's?

---

### Post by taurus on 2007-01-02
Can you mount it by hand from a terminal?

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000 0 0
df -h
```

---

### Post by mega on 2007-01-02
that mount command is rejected, gives me the help info

---

### Post by taurus on 2007-01-02
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by mega on 2007-01-02
hmm, I rebooted, inserted card, and it works, auto mounted it fine

but I cant read the contents

windows reads/writes to the card fine

guess I'll clean it and reformat it

---

### Post by taurus on 2007-01-02
Is it ntfs filesystem?  If not sure, post the output of the command that I have asked for from above!!!

---

### Post by mega on 2007-01-02
[17180305.356000] FAT: FAT read failed (blocknr 12)
[17180305.772000] sd 4:0:0:0: rejecting I/O to offline device
[17180305.772000] FAT: Directory bread(block 487) failed

---

### Post by taurus on 2007-01-02
I guess that thing automounted as root so you can't write to it!  Therefore, you can unmount it and mount it again with the right permission...

What's the output of this command then?

```
df -h
```

---

### Post by mega on 2007-01-02
sigh

did a reformat, works fine on camera, mp3 player, windows, but not linux

[17181809.600000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17181953.384000] sd 6:0:0:0: scsi: Device offlined - not ready after error recovery
[17181953.384000] sd 6:0:0:0: SCSI error: return code = 0x50000
[17181953.384000] end_request: I/O error, dev sdb, sector 736
[17181953.384000] Buffer I/O error on device sdb1, logical block 487
[17181953.384000] lost page write due to I/O error on sdb1
[17181953.384000] sd 6:0:0:0: rejecting I/O to offline device
[

---

### Post by taurus on 2007-01-02
Okay, let me explain this one more time.  The automount will mount your external drive as root so a regular like yourself cannot write to it unless you use **sudo** or **gksudo nautilus**!  Therefore, you need to unmount it first and mount it with the right permission again...

```
df -h
```

---

### Post by mega on 2007-01-02
this is friggin unusable for a normal person

---

### Post by mega on 2007-01-02
df -h locks up

it does show it's mounted, but it freezes and then I get the same read errors in dmesg

Filesystem            Size Used Avail Use% Mounted on
/dev/sda1              66G   41G   22G  66% /
varrun                505M   80K  505M   1% /var/run
varlock               505M  8.0K  505M   1% /var/lock
procbususb             10M  124K  9.9M   2% /proc/bus/usb
udev                   10M  124K  9.9M   2% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M  8.0M  497M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/sdc1             150G  107G   43G  72% /media/WD USB 2

then this in dmesg
[17183438.720000] end_request: I/O error, dev sdb, sector 251
[17183438.720000] sd 8:0:0:0: rejecting I/O to offline device
[17183438.720000] FAT: FAT read failed (blocknr 2)
[17183447.736000] sd 8:0:0:0: rejecting I/O to offline device
[17183447.736000] printk: 2977 messages suppressed.
[17183447.736000] Buffer I/O error on device sdb, logical block 0
[17183447.736000] sd 8:0:0:0: rejecting I/O to offline device
[17183447.736000] Buffer I/O error on device sdb, logical block 0




mega@mainpc:/media$ sudo fdisk -l
Password:

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8669    69633711   83  Linux
/dev/sda2            8670        9039     2972025    5  Extended
/dev/sda5            8670        9039     2971993+  82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    c  W95 FAT32 (LBA)

---

### Post by taurus on 2007-01-02
I am trying to help you to get it to work so you can write to it but somehow I get a feeling that it is not going to be the case.  

I guess you just have to wait for somebody else to help you then.

---

### Post by mega on 2007-01-02
nothing can be read or wrote to the drive in linux

but other os's work fine

it worked until about 4 kernels ago, that was the last time I tried to import pictures

---

### Post by mega on 2007-01-02
> **taurus said:**
> I am trying to help you to get it to work so you can write to it 

I'm trying to read the drive, not write, at least not yet, read would be nice first

---

