---
title: "grub error 17"
date: 2008-04-03
forum: General Help
---

### Post by jonathanvb123 on 2008-04-03
i had winblows vista and ubuntu installed on separate partitions on the same hdd. then i removed the partition that had ubuntu on it (dont ask why; complicated story) in windows, and when i rebooted, grub started up but then it said "error 17" and froze there. i figured that grub would have gone away if i removed ubuntu, but i guess not. and ive been searching the internet for hours now, and everyone says to boot a live cd or a windows cd and go from there a number of ways to remove grub. problem is, i cant boot from a cd (and yes, ive checked the boot order in my bios, but it starts spinning up the cd when i boot and then continues to the "error 17" menu in grub without opening the disk, still). please help!!! i have a lot of important files on my vista drive. :confused:

---

### Post by erginemr on 2008-04-03
This is really strange. The computer should have booted form Windows Install CD, when you have adjusted the boot order accordingly form BIOS so that it looks for the CD-ROM drive first and save the settings. Anyway, could you please give a try to Super Grub Live CD too, which has an option to restore your Windows MBR:
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

If you could make your computer boot from the Windows Install CD, you could also issue "fixmbr" from the recovery console to restore the master boot record and flush Grub from there.

---

