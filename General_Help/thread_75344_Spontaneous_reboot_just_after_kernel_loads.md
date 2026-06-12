---
title: "Spontaneous reboot just after kernel loads"
date: 2005-10-13
forum: General Help
---

### Post by kjkrum on 2005-10-13
I updated and rebooted my 5.04 machine before I went home from work last night.  When I came in this afternoon, it was still rebooting... over and over and over.

The BIOS prints its usual messages, then GRUB loads, then the kernel prints a few lines of text and reboots.  The last thing I see is the word 'boot' followed by a line that flashes too fast to read.

I booted Knoppix and mounted my HD.  /var/log/dmesg is an empty file.

Help!

(Good thing this didn't happen tomorrow morning, when I have to demo something for a client.  At least I can rebuild it tonight if I have to... ugh.)

---

### Post by kjkrum on 2005-10-13
I blew everything away and reinstalled Hoary from CD, then upgraded all packages from the official sites.  I'm getting the same thing again: spontaneous reboot at the point where it noramlly says 'uncompressing the kernel'.

This is not cool.

I had to cancel my demo.

Somebody toss me a bone here.  Don't make me put WinXP back on this thing.

---

### Post by kjkrum on 2005-10-14
The md5sum of the kernel image on the machine that won't boot matches the md5sum of the kernel image on the machine I'm using right now, which boots just fine.

The screwed-up machine has an Intel chip.  This one is an Athlon.

Could it be a memory defect?

[edit: not a memory defect.  memtest86 ran for 12 hours with no problems.]

---

