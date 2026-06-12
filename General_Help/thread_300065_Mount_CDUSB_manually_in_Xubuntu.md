---
title: "Mount CD/USB manually in Xubuntu"
date: 2006-11-15
forum: General Help
---

### Post by seshomaru samma on 2006-11-15
I have a bunch of Xubuntu machines with no internet connection. They do not automount  CDs and USB stick ,which is a big concern for the people who work with them , in fact they refuse to work with them. I would like to put gnome-volume-manager which will solve the problem but at the moment it requires dragging the machine (a few floors) to an internet connection and apt-getting it.
Since these are heavy machines and the distance is often quite long ,I would like to try some other way. I would like to just put the package on a CD or USB but then Xubuntu wouldn’t mount them . If I look in thunar the CDrom is always empty and there is no USB in media (once gnome-volume-manger is installed they appear). So can anyone tell me how to mount a cd manually so I can install gnome-volume-manger . Or if you can think of some other method….

---

### Post by taurus on 2006-11-15
From a terminal, try

```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
(assuming your CD-ROM in /dev/hdc and you already have the mount point of /media/cdrom0...)
```

---

### Post by takayuki on 2006-11-16
i have the exact same no mount issue with xubuntu/edgy.

when i insert an audio cd, i can play it via gxine, but i cannot "see" the cd in thunar.

the mount panel applet doesn't seem to work either.

taurus, when i try your terminal command i get this error:

mount: wrong fs type, bad option, bad superblock on /dev/hdc, missing codepage or other error.  in some cases useful is found is syslog -- try dmesg | tail

so, i do a dmesg | tail and get this:

~$ dmesg | tail
[42964459.670000] sda: Mode Sense: 00 00 00 00
[42964459.670000]  0:0:0:0: rejecting I/O to dead device
[42964459.670000] sda: asking for cache data failed
[42964459.670000] sda: assuming drive cache: write through
[42964459.720000] ata1: PIO error
[42964674.570000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[42964674.570000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[42964674.570000] ide: failed opcode was: unknown
[42964674.570000] end_request: I/O error, dev hdc, sector 64
[42964674.570000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

any thoughts greatly appreciated.

regards,

takayuki

ps. taurus, i'm in japan now, but i'm from jax. go jags.

---

### Post by Iesos on 2006-12-10
I have the same problem (I don't use xubuntu, but windowmaker on an ubuntu install).
Me and a friend has concluded that the only thing that can be wrong is that gnome-volume-management uses some other driver than mount, since (at least I) can't even mount a usb volume maually.
I don't have a solution, but interested in getting one...

> when i insert an audio cd

well... that is just destined to go wrong. An audio cd doesn't contain any filesystem (well, not the old fasion ones atleast), so you can't mount it. Trying to mount it will result in many errors and probobly that your cd/dvd-drive will lock up.

---

