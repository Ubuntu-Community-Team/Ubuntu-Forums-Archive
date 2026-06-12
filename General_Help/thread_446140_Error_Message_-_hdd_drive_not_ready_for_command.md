---
title: "Error Message - hdd: drive not ready for command"
date: 2007-05-16
forum: General Help
---

### Post by gwinston99 on 2007-05-16
I was troubleshooting system sluggishness, especially with Win XP running as a guest inside vmware server, and checked the out put on tty#1.

What I see is reported error messages of the type:

18310, 22547 hdd: drive not ready for command

The strangest thing is that I have no /dev/hdd on my system.  I am also experiencing high iowait values, and wonder if the two might be connected.

Any help in getting to the bottom of this would be greatly appreciated.  

I am running Kubuntu Feisty on a reasonably recent pc.

Thanks,

Gregg

---

### Post by skralljt on 2007-07-02
I had this problem also, it occurred when I was using rubyripper.  For me the problem was solved by ejecting the cd (mind you, software wasn't responding.  I had to get up and push the eject button).  So, I don't know how knowledgeable you are about linux but maybe it is your cdrom device having trouble reading a cd?

---

### Post by lisati on 2007-07-02
I've had a similar error message, but referring to hdc instead of hdd. Hasn't worried me since I've normally only noticed it on shutdown on my laptop....my best guess is that something is making some things get ahead of others and the drive is having trouble keeping up.....

---

### Post by lisati on 2007-07-03
I haven't had any further ideas on this one - anyone else?

---

### Post by WI_Mike on 2007-08-08
I have the same problem, but my screen is flooded with this message

hdc: drive not ready for command.

Please, how do I fix this because it floods the screen and it also causes my hda to keep thrashing...

What can I do?

---

### Post by kurakusan on 2007-08-16
me too, its killing my installation of xubuntu on this old dell latirtude laptop.

---

### Post by Epimetheus on 2007-08-17
I am also experiencing this problem with hdb (only have one ide harddrive the other ide device is a cd-rom with no cd).

I get really spammed with this error, even with a fresh installation.

---

### Post by BraveSirRobin on 2007-08-19
I'm also seeing this on my kubuntu installation. I inserted an audio CD and X/KDE started running very slowly, so I ctrl+alt+F2'd to a tty and got this message over and over. No matter what tty I switched to, it was getting hit with this message over and over. This makes it really hard to do anything in a tty. Even after removing the CD and shutting down Amarok, I'm still getting this error over and over.

here's some info on my CD drive, in case it's helpful:

desktop:/proc/ide/ide1/hdd$ cat model
TSSTcorp CD-ROM TS-H192C
desktop:/proc/ide/ide1/hdd$ cat driver
ide-cdrom version 4.61

FWIW, the 'eject' command also doesn't appear to be working on that drive, despite telling me it succeeded.

desktop:/proc/ide/ide1/hdd$ eject -v /dev/hdd
eject: device name is `/dev/hdd'
eject: expanded name is `/dev/hdd'
eject: `/dev/hdd' is not mounted
eject: `/dev/hdd' is not a mount point
eject: `/dev/hdd' is a multipartition device
eject: trying to eject `/dev/hdd' using CD-ROM eject command
eject: CD-ROM eject command succeeded

The eject command works just fine on my other CD drive (hdc), which is a CD/DVD RW rather than a regular CD-ROM drive, and appears to be configured at a SCSI drive. Could it be more strangeness from the Linux ATAPI driver?

---

### Post by BraveSirRobin on 2007-08-20
Not sure if anyone cares but, as a folow-up, the message went away after a reboot. The CD that appeared to have caused the problem is also playing just fine, without the error message, as I type, so the CD itself doesn't appear to have been the cause of the problem.

---

### Post by shadowhywind on 2007-08-29
I am also getting this error, with hda (my cd drive). Also there are times where kubuntu will say that my cd drive has mounted the cd, regardless if I have a cd or not in the drive. The way that i have found to stop those stupid messages, is to to mount the drive (mount /dev/hda) It will spit back that it has the wrong FS  type but it stops the messages from appearing. Its a temp fix, but its something.

---

### Post by linux-junkie on 2007-08-30
I received the about same error only difference was I was using VNC with the Ubuntu 7.04 64-bit desktop. The error that appeared with me was this: **[71807.121833] hdc: drive not ready for command**
When I went to shell or outside of GUI through (ctrl+alt+F4) this was the error the was running. But inside the GUI, I was receiving freezing, no mouse control, 256 colors in video display. I can't figure out off hand what it was that was causing the errors, but I do know that my system load was 100%.
The number sequence was always changing, not allowing me in login or logout. I had to use ctrl+alt+del 3 times before the system rebooted. After that it was fine and I booted properly.

Now with having  over a gig of memory running on a 64-bit processor with plenty of hard drive space, it seems a little strange. Unless they is one weird bug in this version that affects VNC and Ubuntu. I'll have to run further tests to see if it happens again.

---

### Post by racoon97 on 2007-09-21
Hi,
I have the same also but with /dev/hda   [xyzxyz.xyzxyz]  hda: drive not ready for command. (in fact this is on /dev/ sda) . I use a  Dell Inspiron 1501 (with Feisty).
I can use my tty's because I have a lot flood with this messages.

---

### Post by Epimetheus on 2007-09-23
Ok, i've done some probing and found the first time the message appears in my dmesg.

```
[    6.408000] Probing IDE interface ide0...
[    6.696000] hda: ST360014A, ATA DISK drive
[    7.144000] hdb: LILITE-ON DVD SOHD-16P6P9S, ATAPI CD/DVD-ROM drive
[    7.200000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.204000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[    7.204000] ide: failed opcode was: 0xa1
[    7.204000] hdb: drive not ready for command
[    7.208000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[    7.208000] ide: failed opcode was: unknown
[    7.208000] hdb: drive not ready for command
[    7.208000] hdb: ATAPI CD-ROM drive, 0kB Cache
[    7.208000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[    7.208000] ide: failed opcode was: unknown
[    7.208000] hdb: drive not ready for command
```

So it seems my dvd-drive is failing with opcode 0xa1 which, as far as i know, is unknown. I also get the same problems mentioned eariler in this thread with not being able to eject from command line and such.

Could this possibly be a problem with me having my hda (drive) and hdb (dvd) on the same ide port?

---

### Post by gnumantsc on 2007-09-30
I've been noticing the same thing I thought it was a memory issue as I upgraded my HP Pavillion DV6000 series laptop to 2GB of ram from 1GB,

The funny thing is I notice KDE slows down to a crawl but unlike everyone elses' posts, I am using everything off the HD. I thought it was FireFox causing the issue but it does not seem like it.

I was using FF and OO with Kmail open and issue pops up after having my laptop on for about 2-3 hours, and no it is not an overheating issue.

I am using KUbuntu 7.04.

---

### Post by elenothar on 2007-11-14
i get these messages first thing on boot before the system even starts booting. after which the dvd drive led is stuck on and i cannot eject it.

[edit] this guys hdparm command fixed me.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107952/comments/4](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107952/comments/4)

---

### Post by BraveSirRobin on 2007-12-02
> **elenothar said:**
> i get these messages first thing on boot before the system even starts booting. after which the dvd drive led is stuck on and i cannot eject it.

[edit] this guys hdparm command fixed me.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107952/comments/4](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107952/comments/4)

Thanks for the tip. I've edited my hdparm.conf, so we'll see if it happens again.

---

### Post by BraveSirRobin on 2008-01-06
> **BraveSirRobin said:**
> Thanks for the tip. I've edited my hdparm.conf, so we'll see if it happens again.

Still seeing this :(

---

### Post by flipkick on 2008-01-18
Yeah. I'm getting this error as well. It only occurs when VirtualBox is open an when I'm running Win XP inside it.
The only solution for me is to reboot :(

---

### Post by BraveSirRobin on 2008-01-19
> **flipkick said:**
> Yeah. I'm getting this error as well. It only occurs when VirtualBox is open an when I'm running Win XP inside it.
The only solution for me is to reboot :(

Happens seemingly at random for me (although it often seems to happen when I have one or more PDF files open, but that's probably unrelated). It all starts when I insert an audio CD and don't get the KDE menu asking me what to do with it. I can usually do a manual eject on the CD, which causes the menu to appear, but after that everything's fubar. It just happened a few minutes ago and I tried running hdparm -w on my drive, but got a Segmentation fault, followed by the system hanging. Even after rebooting, I can't play audio CDs. I just get a bunch of static. I'll try rebooting again.

---

### Post by BraveSirRobin on 2008-02-13
First of all, my CD drive is a "TSSTcorp CD-ROM TS-H192C." Does anyone else who's posted in this thread have the same make/model?

I did some tinkering over the weekend and am going to tentatively conclude that this was a problem with the kernel driver for my CDROM that's been fixed in 2.6.24.

I started out by upgrading from Feisty to Gutsy (kernel 2.6.22, I think), which didn't fix the problem. I then switched from KDE/Amarok to Enlightenment 0.16/gnome-cd in case KDE's automount daemon was to blame, but was still having the problem. What finally seems to have fixed the problem was installing Debian etch (4.0r2) and immediately doing a dist-upgrade to unstable (kernel 2.6.24-1-486). There now seems to be a new bug that causes audio CD playback to be interrupted frequently at times while the drive spins up for a seek (as close as I can tell, it happens during playback of the last few tracks of a longer than average CD), but at least I don't have to reboot my computer after every couple of CDs (I'm now running Gnome, which automatically plays audio CDs with Sound Juicer).

---

### Post by BraveSirRobin on 2008-02-13
P.S. My dmesg is now full of these errors (presumably related to the playback interruption I mentioned in my last post).

> ATAPI device hdd:
  Error: Illegal request -- (Sense key=0x05)
  Illegal mode for this track or incompatible medium -- (asc=0x64, ascq=0x00)
  The failed "Read 10" packet command was: 
  "28 00 00 03 1c a0 00 00 02 00 00 00 00 00 00 00 "
end_request: I/O error, dev hdd, sector 815744
Buffer I/O error on device hdd, logical block 101968
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
ide: failed opcode was: unknown


---

### Post by nikkkko on 2008-02-16
Hi,

I just upgraded to Gutsy and have been hit by this problem - I see this thread has been going for a while, has anyone got a solution?  Here's my relevant part of dmesg. 

```
[   25.971368] hda: SONY CD-RW CRX195E1, ATAPI CD/DVD-ROM drive
[   26.923128] hdb: HITACHI DVD-ROM GD-2500, ATAPI CD/DVD-ROM drive
[   26.980208] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
[   26.980225] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
[   27.040884] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.042066] Probing IDE interface ide1...
[   27.459007] hdc: WDC WD205AA, ATA DISK drive
[   27.738947] hdd: WDC WD205AA, ATA DISK drive
[   27.797735] ide1 at 0x170-0x177,0x376 on irq 15
[   27.799317] PCI: setting IRQ 9 as level-triggered
[   27.799329] PCI: Found IRQ 9 for device 0000:00:07.2
[   27.799370] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   27.800272] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   27.800320] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000d400
[   27.801697] usb usb1: configuration #1 chosen from 1 choice
[   27.802247] hub 1-0:1.0: USB hub found
[   27.802276] hub 1-0:1.0: 2 ports detected
[   28.142778] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   28.309458] usb 1-1: configuration #1 chosen from 1 choice
[   28.438779] usbcore: registered new interface driver hiddev
[   28.453277] input: USB Mouse as /class/input/input2
[   28.453792] input: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:07.2-1
[   28.453831] usbcore: registered new interface driver usbhid
[   28.453843] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   34.825265] ide-cd: cmd 0x5a timed out
[   34.825287] hda: irq timeout: status=0xd0 { Busy }
[   34.825295] ide: failed opcode was: unknown
[   34.825329] hda: ATAPI CD-ROM drive, 0kB Cache
[   34.825343] Uniform CD-ROM driver Revision: 3.20
[   39.828136] hda: status timeout: status=0xd0 { Busy }
[   39.828144] ide: failed opcode was: unknown
[   39.828152] hda: drive not ready for command
[   44.831013] hda: status timeout: status=0xd0 { Busy }
[   44.831021] ide: failed opcode was: unknown
[   44.831028] hda: drive not ready for command

```

---

