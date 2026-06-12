---
title: "Can't Burn DVD's"
date: 2007-11-24
forum: General Help
---

### Post by kendalc on 2007-11-24
I'm using this command (yes the image does exist):

growisofs -dvd-compat -speed=2 -Z /dev/dvdrw=PULP_FICTION.img

And get this error:

Executing 'builtin_dd if=PULP_FICTION.img of=/dev/dvdrw obs=32k seek=0'
:-( /dev/dvdrw: 2295104 blocks are free, 3843483 to be written!

I get the same error when I try "/dev/hda".  I checked, there is no /dev/hdc.  I'm in the right folder and everything, and /dev/dvd works fine.  It's a LITE-ON DVDRW...

I tried 'mount /dev/hdc, and got this:

mount /dev/hdc
mount: can't find /dev/hdc in /etc/fstab or /etc/mtab

I did recently remove a spare CDROM from my computer, could that have something to do with it?  Please help.

---

### Post by scxtt on 2007-11-24
> /dev/dvdrw: 2295104 blocks are free, 3843483 to be written!looks like you're trying to write 1548379 more blocks than are available ...

---

### Post by ijason on 2007-11-24
i highly recommend gnomebaker, if your heart isn't set on doing it command-line style. 

plus, i think you may be getting problems from referencing /dev/cdrom... i've always seen them listed as /dev/hdc (or whatever appropriate letter for your set up)

---

### Post by kendalc on 2007-11-24
> **scxtt said:**
> looks like you're trying to write 1548379 more blocks than are available ...

Oh.  Good point.  Still, shouldn't I have a /dev/hdc?  I have no /dev/hdb either...

Also, I ripped it from a DVD, why is it larger than a dvd!?

---

### Post by scxtt on 2007-11-24
lshw should be able to tell you a lot about your system, here's an example:
```
sudo lshw -class disk
  *-cdrom
       description: DVD-RAM writer
       product: DVDRRW GSA-4166B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@4:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       serial: [HL-DT-STDVDRRW GSA-4166B1.0005/09/09
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
```also, the newer versions of ubuntu use the sata driver for parallel devices ... so what was once /dev/hdb for a cdrom would be put in the /dev/sd* chain since feisty (maybe earlier) ... my dvdrw is an IDE device, but you can see its logical names above ...

---

