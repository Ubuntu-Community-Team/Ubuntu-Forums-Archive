---
title: "grub rescue can't ls any file systems"
date: 2015-10-17
forum: General Help
---

### Post by edooze on 2015-10-17
Hi all,

I've just tried to restart my machine here, and for some reason it throws the following:

error: no such device: 522cd... blah blah there's a text string here.
grub rescue>

That's fine, I understand grub has some issues from time to time, the real problem I've got is that whenever I try to ls any of my partitions, it says:

error: unknown filesystem

I have 6 hdds in this machine, and I'm fairly sure that hd0,msdos1 is the hdd I want to boot from, but I can't ls it, or anything else, to find out where the boot dir is, or any of the files.

What do I do? All the forum threads I've found that have any information at all all require me to be able to list the files on the drive, so they're a total bust.

TIA,
edooze

---

### Post by grahammechanical on 2015-10-17
You can run a Ubuntu live session and a) examine the hard drives from there. b) install Boot Repair on the live session; get it to create a boot info summary and then when it provides a URL to the paste bin site where the boot info report is stored post it in your thread. c) Accept the offer of Boot Repair to repair the boot. The recommended repair is found at the bottom of the Boot Info report.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by oldos2er on 2015-10-17
You can run the [bootinfo script]("http://bootinfoscript.sourceforge.net/") from a live medium and post the results here (in code tags please) so we can see what's going on with your system.

---

### Post by yancek on 2015-10-17
The "no such device" error you report means Grub is looking for a partition with that uuid and it either can't find it or it doesn't exist.  Posting the boot repair info should provide that information and much more that would be useful.

---

### Post by edooze on 2015-10-19
I must have updated the kernel and not been diligent enough to update-grub. Doesn't often happen but I guess we all get bit sometimes.

Anyway, I managed to boot from a liveUSB, got the pastebin, and tried to fix with a Boot-Repair and it actually made it worse 'can't find operating system'.
I then was able to boot into my install from the USB Grub prompt, and performed an upgrade to the latest version of Ubuntu (which broke for other reasons - stay away from SDDM for the moment!) so I've rolled back to 14.04 LTS.
Great start to the week, I tell you.

Thanks for the help anyway, folks.

---

