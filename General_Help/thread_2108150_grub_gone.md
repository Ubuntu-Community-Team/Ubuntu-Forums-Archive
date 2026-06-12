---
title: "grub gone"
date: 2013-01-23
forum: General Help
---

### Post by DominikCZE on 2013-01-23
Hello,

I think I seriously screwed up. I reinstalled windows, because AMD drivers messed up my registry beyond repair.

When I restarted the computer after the Windows configuration was finished, I freaked out, grub is completely gone and Windows boots itself automatically. What did I do? I know that the Ubuntu partitions were untouched, so the OS must be fine, right? I really hope I didn't seriously screw something up :(

Thanks for any help. :/

---

### Post by papibe on 2013-01-23
Hi DominikCZE.

Most certainly the Windows installer wiped out grub.

However, can be reinstalled so that it scan the disk for both Ubuntu and Windows and you get back your dual boot set up.

Use the Ubuntu installer media as a 'Live media', and then follow the steps of this [guide]("https://help.ubuntu.com/community/Boot-Repair") to restore grub.

Let us know how it goes.
Regards.

---

### Post by DominikCZE on 2013-01-24
It worked perfectly, what a great and simple tool. :)

I'm happy everything is working, as I have all my program codes saved on the linux partitions along with other important work.
Only strange thing, grub sees 2 W7s...one is pointing tu sda1, that used to be a hidden recovery partition I think, but now I see it Windows as E, 99mb. It containts a system file called bootmgr, one back up file and 3 folders I don't have permission to access. Why wasn't this there the first time around?

Thanks a lot for the help.

---

### Post by oldfred on 2013-01-24
Windows 7 installs normally have the hidden 100MB boot/repair partition. I think Boot-Repair copies those boot files into the main install as a backup, but then you get two entries from grub's os-prober.

---

### Post by DominikCZE on 2013-01-24
Ah I see, thanks, so would it be unwise to format it, since it's basically a copy of the hidden partition?

---

