---
title: "Transcend IDE Flash DMESG errors - unusable"
date: 2007-09-04
forum: General Help
---

### Post by Mikealcl on 2007-09-04
DMESG:

[    4.764617] ata2.00: ATA-0: TRANSCEND    064M, 1.1, max PIO2
[    4.764621] ata2.00: 125184 sectors, multi 1: LBA 
[    4.764872] ata2.00: failed to set xfermode (err_mask=0x1)
[    4.764877] ata2: failed to recover some devices, retrying in 5 secs
[    9.928292] ata2.00: failed to set xfermode (err_mask=0x1)
[    9.928298] ata2.00: limiting speed to PIO1
[    9.928301] ata2: failed to recover some devices, retrying in 5 secs
[   15.091753] ata2.00: failed to set xfermode (err_mask=0x1)
[   15.091757] ata2.00: disabled

Drive:

Transcend 40-pin IDE Flash Module

I've tried to look on google, havent found much but similar problems with people and pcmcia with CF cards.  I tried asking on IRC and no one seems to have any answers.  I would think this has to be something reasonably easy.

---

### Post by Mikealcl on 2007-09-04
> **Mikealcl said:**
> DMESG:

[    4.764617] ata2.00: ATA-0: TRANSCEND    064M, 1.1, max PIO2
[    4.764621] ata2.00: 125184 sectors, multi 1: LBA 
[    4.764872] ata2.00: failed to set xfermode (err_mask=0x1)
[    4.764877] ata2: failed to recover some devices, retrying in 5 secs
[    9.928292] ata2.00: failed to set xfermode (err_mask=0x1)
[    9.928298] ata2.00: limiting speed to PIO1
[    9.928301] ata2: failed to recover some devices, retrying in 5 secs
[   15.091753] ata2.00: failed to set xfermode (err_mask=0x1)
[   15.091757] ata2.00: disabled

Drive:

Transcend 40-pin IDE Flash Module

I've tried to look on google, havent found much but similar problems with people and pcmcia with CF cards.  I tried asking on IRC and no one seems to have any answers.  I would think this has to be something reasonably easy.

This link seems to be the same thing.

[http://lkml.org/lkml/2007/8/2/92]("http://lkml.org/lkml/2007/8/2/92")

---

### Post by Mikealcl on 2007-09-05
> **Mikealcl said:**
> This link seems to be the same thing.

[http://lkml.org/lkml/2007/8/2/92]("http://lkml.org/lkml/2007/8/2/92")

Still stuck on this.

---

### Post by tgalati4 on 2007-09-05
I've been flashing 4GB Emphase IDE modules.  I had a defective one with similar errors.  These are strange devices.  They have a processor on board that virtualizes the memory space and writes the data in such a way to get 4 million read/write cycles out of flash.  Timing issues, bad flash, a sticky Master/Slave switch, can all contribute to problems.

I would only use them for embedded applications where the entire OS is loaded into RAM (like Damn Small Linux) so that rewrites to flash is minimized during operation.

If they are used for regular Linux installs, with all of the /proc and /var/log writes, who knows how long they will last.

---

### Post by Mikealcl on 2007-09-05
> **tgalati4 said:**
> I've been flashing 4GB Emphase IDE modules.  I had a defective one with similar errors.  These are strange devices.  They have a processor on board that virtualizes the memory space and writes the data in such a way to get 4 million read/write cycles out of flash.  Timing issues, bad flash, a sticky Master/Slave switch, can all contribute to problems.

I would only use them for embedded applications where the entire OS is loaded into RAM (like Damn Small Linux) so that rewrites to flash is minimized during operation.

If they are used for regular Linux installs, with all of the /proc and /var/log writes, who knows how long they will last.

I am using them for a small linux install that loads into RAM.  But I am building the distro on ubuntu and need a way to install it with syslinux, which is why I need to mount them.

I had no problems using them in the past, but I never used ubuntu to build before.  I have about 20 of them so I am pretty sure its not a failed device as I tried several.

I will try flipping the master/slave and see if that makes a difference. It is the only thing on the IDE so I set it to master.

---

### Post by Mikealcl on 2007-09-05
> **Mikealcl said:**
> I am using them for a small linux install that loads into RAM.  But I am building the distro on ubuntu and need a way to install it with syslinux, which is why I need to mount them.

I had no problems using them in the past, but I never used ubuntu to build before.  I have about 20 of them so I am pretty sure its not a failed device as I tried several.

I will try flipping the master/slave and see if that makes a difference. It is the only thing on the IDE so I set it to master.

Master/Slave setting doesn't seem to make a difference.
Tried 3 different IDE modules now.

---

### Post by tgalati4 on 2007-09-06
One thing to try:

Go into BIOS and detect the hard disk and set the Ultra DMA Mode (2 perhaps?).  It looks like the kernel is trying the PIO modes (old school) and the drive doesn't support it.

Damn Small Linux uses the 2.4.26 kernel and it seems to work fine--I don't recall which bootloader it uses: isolinux or syslinux.  Whatever the 3.4.1 version of DSL uses, it works with Emphase 4GB flash drives.

I didn't want to go through the pain of slimming down an Ubuntu system for these embedded devices, so I develop on a full Ubuntu machine, and move the binary over to the embedded computers.  The neat thing is that the binary (compiled on 2.6.15-28) runs on DSL with 2.4.26 kernel!

After stress-testing (48 hours, 10 instances of the program, 100% CPU usage) there were  no memory leaks and no swap usage.  Good enough for me.

---

