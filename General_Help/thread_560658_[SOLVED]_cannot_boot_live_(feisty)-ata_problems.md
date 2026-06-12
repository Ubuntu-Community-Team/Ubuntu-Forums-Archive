---
title: "[SOLVED] cannot boot live (feisty)-ata problems"
date: 2007-09-26
forum: General Help
---

### Post by erisianmonkey on 2007-09-26
Hi all. 

I downloaded feisty last night, and cannot get the live cd to boot. I get the error message:
BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
/bin/sh: can't access tty; job control turned off

(initramfs) [ ***.******] ata2: port failed to respond (30 secs, Status 0xd0)

If I wait there are other messages, but mostly repeats of the first. The ones that are not are long strings of hex, mostly. Note that the stars represent that there are different numbers every time the message appears.

Hardware:
Intel Celeron 3.06Ghz (Prescott)
Foxconn 865G7MF-SH Motherboard
512 MB ddr2 dram
WDC 15 GB HDD (slave)
Seagate 160GB HDD (master) (both hard drives PATA)
TSST DVD+/- RW
Chaintech Geforce fx5200 vid card

Could this be related to the fact that I have SATA capability but am not using it? I've been anxious to install Linux on the smaller hard drive so I can get used to Linux as I don't foresee myself buying Vista when M$ casts XP to the wolves.

I'm hoping there is a software answer, as I am not anxious to wrestle with hardware config changes.

EDIT TO ADD:
Before the question comes up (as it should) Yes, I checked the MD5. I have tried both the 64 bit and the i386 versions.  I am now downloading the alternate disc to see if I can get more info using a text interface.

---

### Post by erisianmonkey on 2007-09-26
downloaded the alternate. It will give the same errors, a semi- complete reporting of the error being:

[ ***.******] ata2: port failed to respond (30 secs, Status 0xd0)
[ **.******] ata2.00: exception Emask 0x0 Sflct 0x0 SErr 0x0 action 0x2 frozen
[ **.******] ata2.00: cmd a0x01:00:00:00:00/00:00:00:00:00/a0 tag0 cdb 0x12 data 36in

The new development is that rather than just staying hung up, it proceeds into the installer and tells me that it cannot mount the cd-rom drive. My cd/dvd drive is a TSST H552B (Samsung) It says if I had a floppy with a driver I could get somewhere. The problem is I don't have a floppy drive installed in this machine, and I have not found drivers for this drive for any linux at all, much less specific to the Ubuntu distro. Hopefully this is enough info to see if there's some help available. 

Or am I just screwed as far as getting Ubuntu running goes?

Edit to add: I don't get it- how could I get this far if it cannot mount the drive?

---

### Post by erisianmonkey on 2007-09-28
I found a solution!!!\\:D/

I had an old NEC CD-ROM drive from my old gateway that I put in as a slave on ata2. no errors, The Live CD booted and installed. From the drive that was having trouble in the first place, believe it or not. Many and wonderous be the ways of the gods, and sporked be those that try and understand them.
:-k:-k
Seriously, I have no idea why installing an ancient cd drive as a slave would cause Ubuntu to recognize the master it wouldn't before. Oh, well.

---

