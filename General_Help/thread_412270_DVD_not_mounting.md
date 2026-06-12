---
title: "DVD not mounting"
date: 2007-04-17
forum: General Help
---

### Post by winkerbean on 2007-04-17
I tried to mount my DVD drive and got the following messages:
Could not mount device.
The reported error was:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

My /etc/fstab looks like so:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs-fuse auto,gid=1002,umask=0002 0 0
/dev/hdb5 /nuetralzone vfat defaults 0 0
/dev/hdb6 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 rw,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda1 /media/usb0 auto rw,user,noauto 0 0

Any ideas? Thanks in advance.

---

### Post by leibowitz on 2007-04-18
> /dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 rw,user,noauto 0 0

First please edit those two lines in the /etc/fstab file, remove the "noauto" if you don't explicitly want this. And remove the rw aswell. 

You should have this as a result.
> /dev/hdd /media/cdrom0 udf,iso9660 user 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user 0 0

Now tell me if you are mounting using the mount command, or just clicking (in the GUI) on the dvd drive ?

---

### Post by RedSquirrel on 2007-04-18
> **winkerbean said:**
> I tried to mount my DVD drive and got the following messages:
Could not mount device.
The reported error was:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

My /etc/fstab looks like so:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs-fuse auto,gid=1002,umask=0002 0 0
/dev/hdb5 /nuetralzone vfat defaults 0 0
/dev/hdb6 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 rw,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda1 /media/usb0 auto rw,user,noauto 0 0

Any ideas? Thanks in advance.


After you try to mount, what is the output of (in a terminal):

```
dmseg | tail
```??

>  **mount: wrong fs type, bad option, bad superblock on /dev/hdc**
What is in your DVD drive? You can't mount an audio CD, for example...

---

### Post by winkerbean on 2007-04-18
Hi, Red Squirrel.
    I did as you suggested.  Also did a sudo mount -a afterwards.  Got the same answer.  From dmesg, I get (truncated to just the last few lines):
[INDENT][4376260.652000] ohci_hcd 0000:00:02.3: wakeup
[4376260.982000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[4376261.200000] usb 2-1: configuration #1 chosen from 1 choice
[4376261.954000] SCSI subsystem initialized
[4376261.957000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer de
v 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4911
[4376261.959000] usbcore: registered new driver usblp
[4376261.959000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driv                                                                            er
[4376261.996000] Initializing USB Mass Storage driver...
[4376261.999000] scsi0 : SCSI emulation for USB Mass Storage devices
[4376262.000000] usb-storage: device found at 2
[4376262.000000] usb-storage: waiting for device to settle before scanning
[4376262.001000] usbcore: registered new driver usb-storage
[4376262.001000] USB Mass Storage support registered.
[4376267.009000]   Vendor: HP        Model: PSC 2350          Rev: 1.00
[4376267.009000]   Type:   Direct-Access                      ANSI SCSI revision                                                                            : 02
[4376267.011000] usb-storage: device scan complete
[4376267.087000] sd 0:0:0:0: Attached scsi removable disk sda
[4376267.201000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4376389.967000] usb 2-1: USB disconnect, address 2
[4376389.970000] drivers/usb/class/usblp.c: usblp0: removed
[4380157.293000] cdrom: hdc: mrw address space DMA selected
[4380157.358000] cdrom: hdc: mrw address space DMA selected
[4380157.397000] attempt to access beyond end of device
[4380157.397000] hdc: rw=0, want=68, limit=4
[4380157.398000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=1[/INDENT]

Looking forward to anything you can offer,
Winkerbean

---

### Post by RedSquirrel on 2007-04-19
> attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
Interesting. I had not seen that before, so I did a bit (OK, a *lot*) of research and there are a number of threads with that problem, both here (ubuntuforums) and elsewhere on the web (using Google).

However, I have found nothing that will definitely help. All of the threads seem to die with one of the following responses:

- *Nobody has any suggestions and the OP is left hanging.*
- "Your drive is toast."
- "That specific DVD is bad." (even though it can be read in the same drive under a different OS)
- "The software you used to burn the DVD has bugs."

You might have to do some more digging yourself (searching these forums, Google, etc.). Sorry. :(

I searched the launchpad site for Ubuntu, but didn't see much there either. Darn. [This one]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/58018") is similar, but the OP decided it was his drive that caused the issue.

---

