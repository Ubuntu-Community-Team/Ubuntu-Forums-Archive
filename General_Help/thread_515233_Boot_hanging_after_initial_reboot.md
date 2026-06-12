---
title: "Boot hanging after initial reboot"
date: 2007-08-01
forum: General Help
---

### Post by Moya on 2007-08-01
I successfully used to the Wubi installer, and quite naturally, I was instructed to do a reboot.  I selected Ubuntu from the boot menu, got some typical "loading" text, but after "No RAID disks" or something similar, nothing happens.  I am able to type and hit enter, but it seems to not have any effect, although I can't say for certain because I am quite the Linux "noob".

If it matters, my version of Windows is Vista Ultimate 64-Bit.

---

### Post by ago on 2007-08-02
Do you see any error messages?

There should be a couple of log files inside /tmp, you can read them with the "more" command

---

### Post by ajskhan on 2007-08-02
Uhhh, sorry having the same problem... I typed "more /tmp" into the command thing after my boot stopped and nothing happened... am I missing something? Is there a way I can look at the files through windows?
EDIT: FYI-just ran chkdsk

---

### Post by ago on 2007-08-02
more /tmp/zenigata.log
more /tmp/lupin.log

---

### Post by ajskhan on 2007-08-02
thanks, but before I had a chance to type that
it did the same no raid disks thing
but then started an Alt Inst - alternate install?

"installing base system" as we speak, errr, type

---

### Post by tuxcantfly on 2007-08-02
> "installing base system" as we speak, errr, type

In that case, it apparently worked. If it didn't, though, use Ctrl-Alt-F1, Ctrl-Alt-F2, and see the other output; you should be able to get to a console at some point for checking the logfiles. They will also be in C:\Wubi.

---

### Post by ajskhan on 2007-08-02
it did, working now! great program

---

### Post by xcapepr on 2007-09-28
After the  initial re-boot, I'm getting the No RAID Disk thing.

First it gives a warning about having an unrecognized partition table for drive 80.Then it says to rebuild it using fdisk (but wouldn't that erase it?)

ERR=22

Current C/H/S=16383/255/63 (HD1,0)

Filesystem is NTFS part. type 0x7
Linux-bzimage, setup+0x1c00 etc.
Linux initrd @ 0x1f85e000 etc

Then I get the No RAID disk thing

Check root= bootarg cat /proc/cmdline or missing modules, devices:
cat /proc/modules ls /dev

Then something called BusyBox starts. and turnes yet another error:
/bin/sh: cant access tty; job control turned off
and ends in (initramfs) and stays there

This is on a Dell Precision M4300 laptop and the drive Im trying to install to is the add-on modular bay one.

It has an NTFS partition of 15 gigs that I created with Vista's disk manager to use with Wubi, the rest of the disk holds Norton Ghost backups in another partition.

If I do the fdisk thing i should do it to the whole drive or just to the part that Wubi will use

This computer has an Intel Matrix SATA controller for the main drive (where c:\boot is). The main drive has a 71 mb part, a 2 gb recovery part, a 95 gb part for vista and the last one is for an XP dual boot.

Silly Dell partitions..

I Triboot Vista/XP/Wubi on my PC no problems... what could it be?!

---

