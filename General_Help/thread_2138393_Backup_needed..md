---
title: "Backup needed."
date: 2013-04-23
forum: General Help
---

### Post by groc60 on 2013-04-23
So I have this problem...
My windows 8 (gross, i know) laptop won't boot, it brings me to the recovery page every time i try.
customer support said i'm s.o.l. and need to restore my computer to factory settings. The problem with this is I need some files from my HD first.
My plan was to use Ubuntu to access my HD and use a data transfer cable to get the files to the PC I'm on right now; then restore the broken PC.

I made a Ubuntu 12.10 live USB and booted it up just fine (APCI=off had to be checked), the problem is it won't let me access my HD.
So i had another idea: I'll install Ubuntu onto my HD from the Live USB -- the problem is it's literally been going for 31 hours...
I have tried this same method using Ubuntu 12.04 - that just kept taking me to the black screen of death from the start.

My questions are:
a) is there a command where it can force access my HD
b) is there a faster way to install Ubuntu (and keep my files)?
c) is there a better version for what I'm trying to do?
d) is it pronounced you-boon-too or Ooo-Boon-too?

The broken PC is has 500gb, runs windows 8 (not for long...), and has and intel core i3 with 4gb ram

---

### Post by r.stiltskin on 2013-04-24
What does that mean, "it won't let me access my HD"?  When I boot my laptop using a Xubuntu 12.10 CD or a Kubuntu 12.04 CD I have no problem mounting and accessing files on the laptop's hard disk.  But my dual-boot is Windows 7.  Is there a special problem involving Windows 8 that prevents access, or is the file system on your hard disk so corrupted that it can't be opened?

---

### Post by tubbygweilo on 2013-04-24
Something like Partedmagic [http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start) [http://partedmagic.com/doku.php?id=screenshots](http://partedmagic.com/doku.php?id=screenshots) running in ram from a livecd / usb stick may well offer more options for exploring, extracting and making backups of a Windows System than Ubuntu. [Knoppix]("http://knopper.net/knoppix/knoppix705-en.html") LiveCD is another useful tool for exploring, extracting and making backups from other machines. I have used both to save data from ailing windows machines.

---

### Post by Mark Phelps on 2013-04-24
> **groc60 said:**
> So I have this problem...
My windows 8 (gross, i know) laptop won't boot, it brings me to the recovery page every time i try...
Before you completely give up on this, suggest you check in another forum -- an Windows 8 forum: eightforums.com

They may be able to tell you how to get the PC working again.

---

### Post by groc60 on 2013-04-24
> **r.stiltskin said:**
> What does that mean, "it won't let me access my HD"?  When I boot my laptop using a Xubuntu 12.10 CD or a Kubuntu 12.04 CD I have no problem mounting and accessing files on the laptop's hard disk.  But my dual-boot is Windows 7.  Is there a special problem involving Windows 8 that prevents access, or is the file system on your hard disk so corrupted that it can't be opened?

a message pops up saying " Cannot mount 475 GB Drive "

---

### Post by r.stiltskin on 2013-04-24
Is that the *exact, complete* message?

What is the output if you open a terminal window and run:
```

sudo fdisk -l

```
(That's a lower-case letter "L" at the end of the line.)

---

### Post by groc60 on 2013-04-24
> **r.stiltskin said:**
> Is that the *exact, complete* message?

What is the output if you open a terminal window and run:
```

sudo fdisk -l

```
(That's a lower-case letter "L" at the end of the line.)

The terminal says: GPD detected on '/dev/sda'! the util fdisk doesn't support GPD. use GNU parted.

I would copy/paste everything but i don't know how to highlight text from the terminal :/

---

### Post by r.stiltskin on 2013-04-24
I think you meant "GPT (GUID Partition Table)".   OK, well that tells me part of what I wanted to know anyway - it's on /dev/sda.  Unfortunately I know almost nothing about Windows 8 and UEFI.

When you boot with the cd, do you see an option to boot in EFI or UEFI mode?  And did you choose that when you booted?  I think you need that to access the drive, so if you didn't,
 try booting again in EFI mode.

---

### Post by groc60 on 2013-04-24
no, theres no UEFI or EFI mode

Here are my options:
(under f4): Normal, Use driver Update disc, OEM install (for manufacturers),
(under f6): apci=off, noapci, nolapci, edd=on, nomraid, nomodeset,free software only


In order for it to boot up apci=off needs to be activated for my computer

---

### Post by r.stiltskin on 2013-04-25
Did you download the 64-bit version of ubuntu (ubuntu-12.10-desktop-amd64.iso) or the 32-bit version (ubuntu-12.10-desktop-i386.iso)?  You should be using 64-bit.

Did you make any changes to your BIOS (EFI vs Legacy mode)?

When you begin to boot with the USB stick, do you see a screen that looks like this:
[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

or like this:
[IMG]http://pix.toile-libre.org/upload/original/1347445119.png[/IMG]

When you installed Ubuntu, did you follow instructions on this wiki page: [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

---

