---
title: "deleted gnu grub partition please help"
date: 2013-11-23
forum: General Help
---

### Post by MisterBass123 on 2013-11-23
Hello everyone,

I got a laptop with dual-boot into windows 7 and ubuntu,
i use the gnu grub to make the dual booting possible.
recently i wanted to delete the gnu grub so that i thought it would boot up in windows 7 directly.
What i did was that i deleted the swap partition and another partition that i think was 1gb.
Now my pc boots up and now i see a command line interface from gnu grub and don't know what to do.
it says: Minimal BASH-like editing is supported. For the first word, TAB lists possible command completions. Anyware else TAB lists possible device or file completions.
and on the top it says: GNU GRUB version 2.00-19ubuntu2.1
I really don't know what to do now and i need my laptop for school work so any kind of help will be much appreciated.

---

### Post by fantab on 2013-11-23
What do you want to do? Remove Ubuntu or Dual-boot but want Windows to boot by default?

---

### Post by MisterBass123 on 2013-11-23
I wanted to uninstall ubuntu so i only have windows 7 as operating system and as default operating system.
(thanks for the fast reply)

---

### Post by fantab on 2013-11-23
To be able to boot Windows again you will need either a Windows Repair Disc or Windows Install Disc (Install disc should the same version of windows as installed, preferably the same disc from which you installed).
Then you will have to boot with it and 'fix Windows Boot'.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If you don't have either of the above, and if its a laptop which came ith pre-installed Windows, then try to restore windows from Laptop OEM tools. If that doesn't work then, I am afraid, you will have to re-install windows. 
OEM can also provide you with a 'repair disc', sometimes at a price. Contact them.

Once Windows boot is fixed, boot with Ubuntu DVD/USB and 'Try Ubuntu without instaling'; open Gparted, select the partition on which Ubuntu is installed and format it.

Good Luck.

---

### Post by MisterBass123 on 2013-11-23
I have a windows repair disc, but here comes another problem:
when i start my laptop it goes directly into the gnu grub command line.
I try to use those keys (f2, f8, f12) for changing the boot order but it keeps booting into gnu grub, even when the windows repair disc is in it.
if there isn't a solution for this problem, how could i reintall windows then when i cant boot into the repair disc?

---

### Post by MisterBass123 on 2013-11-23
I found a temporaly solution, i just have to type exit so it boots into windows.
Anyway a very big thanks for helping me :D

---

