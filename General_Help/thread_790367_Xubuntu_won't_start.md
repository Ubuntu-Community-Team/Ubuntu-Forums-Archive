---
title: "Xubuntu won't start"
date: 2008-05-11
forum: General Help
---

### Post by marmaladeskies on 2008-05-11
Well, I don't recall doing anything odd that might harm my system, but when I turned it on today, I saw the Toshiba logo, then grub, then it just went black.  So I tried to open it up in recovery mode.  After the normal scripts (the last one I saw was Setting the system clock), this came up:

Loading manual drivers...
[30.256000] lp: driver loaded but no devices found
[30.344000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[30.344000]apm: overrideen by ACPI
[30.384000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[30.384000] apm: disabled on user request.
*Setting kernel variables...
error:  "vm.mmap+min+addr" is an unkown key
                                  [fail]
*Activating swap...               [OK]
*Checking root file system
fsck 1.40.8 (13-Mar-2008)
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Duplicate or bad block in use!
/dev/sda1: Multiply-claimed block(s) in inode 5379389: 4300203 4300203
/dev/sda1:  UNEXPECTED INCONSISTENY; RUN fsck MANUALLY (i.e., without -a or -p options)
fsck died with exit status 4
*An automatic system check (fsck) of the root filesystem failed.  A manual fsck must be performed, then the system retstarted.  The fsck should be performed in maintenance mode with the root filsesystem mounted in read-only mode.
*The root filseystem in scurrently mounted in read=only mode.
A maintenace shell will now be started.
After performing system maintenance, press CONTROL-D to terminated the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@tosh:~#

So... what do I type here?  I suppose I have to do some kind of manual fsck, whatever that is.  Could someone please explain how to do this?  I really really appreciate any help you can lend.  Thanks.

---

### Post by metiosarius on 2008-05-11
Take a look at the second entry in this post: [http://ubuntuforums.org/showthread.php?t=546258](http://ubuntuforums.org/showthread.php?t=546258)

---

### Post by marmaladeskies on 2008-05-11
Thanks a million.  I couldn't seem to find that when I did the search.

---

### Post by metiosarius on 2008-05-11
> **marmaladeskies said:**
> Thanks a million.  I couldn't seem to find that when I did the search.

No problem :)

---

