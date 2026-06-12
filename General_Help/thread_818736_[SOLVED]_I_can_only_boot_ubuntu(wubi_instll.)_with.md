---
title: "[SOLVED] I can only boot ubuntu(wubi instll.) with grub cd."
date: 2008-06-04
forum: General Help
---

### Post by RJQ on 2008-06-04
I am having a problem to boot in to ubuntu in my machine, it has different systems and this is how they are organized and what I found:

hd0 > Windows recovery
          Windows XP Home > Ubuntu with wubi (last one installed)
hd1 > Kubuntu
          Ubuntu (default system)
          Home Partition
          Swap Partition

now with a normal boot up I select windows xp then the second grub appears for the selection of windows and ubuntu (wubi), windows boots fine but ubuntu just give me a bunch of strange symbols (line and a half) on which just the words disk error are legible, from there nothing happens and the only command that it works is ctl+alt+delete, in the first (default) grub any system boots fine. Then I try by curiosity my Grub CD to see if it could fix the second grub, did not, (actually I do not now how at all) but it can actually boot Ubuntu (wubi) one, but not windows and I can see that this options look different from those in my normal boot in this ones the windows is called XP professional (same which is totally unprofessional : P) and a option for booting also in safe mode, none of this works but ubuntu.

I know then that the wubi installation works but not the grub in windows, it seems some how that another configuration (the one that grub cd found when booting windows) has the correct path for ubuntu, but after this I do not know what to do, any help is highly appreciated.

Also I was wondering if it is possible to boot this ubuntu from the default grub this is as a option without the need of selecting windows first.

---

### Post by Dazed_75 on 2008-06-04
> **RJQ said:**
> I am having a problem to boot in to ubuntu in my machine, it has different systems and this is how they are organized and what I found:

hd0 > Windows recovery
          Windows XP Home > Ubuntu with wubi (last one installed)
hd1 > Kubuntu
          Ubuntu (default system)
          Home Partition
          Swap Partition

Is the Windows XP Home partition FAT32, NTFS converted from FAT32, or true NTFS?  It seems from MANY posts here that any of them worked with the 2.6.24-16 kernel that came with ubuntu 8.04 but do NOT work with a wubi installed 8.04 which has been updated with the 2.6.24-17 kernel offered now in updates.

If that is the issue for you keep reading the forums for notice of another update.  The posted fix to update intramfs did not work for me.  The only fix that worked was to either:
1) ESC at grub to get the menu and select the -16 kernel, or
2) Uninstall the -17 kernel and verify the grub menu list goes back to -16 (or fix it yourself).

> now with a normal boot up I select windows xp then the second grub appears for the selection of windows and ubuntu (wubi), windows boots fine but ubuntu just give me a bunch of strange symbols (line and a half) on which just the words disk error are legible, from there nothing happens and the only command that it works is ctl+alt+delete, in the first (default) grub any system boots fine. Then I try by curiosity my Grub CD to see if it could fix the second grub, did not, (actually I do not now how at all) but it can actually boot Ubuntu (wubi) one, but not windows and I can see that this options look different from those in my normal boot in this ones the windows is called XP professional (same which is totally unprofessional : P) and a option for booting also in safe mode, none of this works but ubuntu.

I know then that the wubi installation works but not the grub in windows, it seems some how that another configuration (the one that grub cd found when booting windows) has the correct path for ubuntu, but after this I do not know what to do, any help is highly appreciated.

Also I was wondering if it is possible to boot this ubuntu from the default grub this is as a option without the need of selecting windows first.

If I understand you correctly, no it cannot do this as the wubi installed ubuntu depends on windows filesystem drivers underneath the ubuntu filesystem drivers and the windows ones have not started when you use the grub installed by the non wubi-ized ubuntu.

---

### Post by RJQ on 2008-06-05
> **Dazed_75 said:**
> Is the Windows XP Home partition FAT32, NTFS converted from FAT32, or true NTFS?  It seems from MANY posts here that any of them worked with the 2.6.24-16 kernel that came with ubuntu 8.04 but do NOT work with a wubi installed 8.04 which has been updated with the 2.6.24-17 kernel offered now in updates.

Actually I have the -16 kernel on the wubi installed ubuntu, no updates yet, I  believe that in my case has something to do with the grub under windows but unlike the usual grub in this one I do not know how to manipulate it, and if the grub CD can open this ubuntu disk I think is fixable, I need to keep reading aroung I guess.


> If I understand you correctly, no it cannot do this as the wubi installed ubuntu depends on windows filesystem drivers underneath the ubuntu filesystem drivers and the windows ones have not started when you use the grub installed by the non wubi-ized ubuntu.

got it.

thanks for the info.

---

### Post by RJQ on 2008-06-11
Well in a kind of accidental way I could resolve some how this issue, I was looking the folders trying to make some sense of this, I knew that ubuntu (by wubi) was bootable I just need to find the path, when I realized that thre were to files of wubidlr and wubidlr.mbr, the first pair was on c:\ while the second was on c:\ubuntu\winboot\, in the boot file I find out that it was pointing to the first pair and just by curiosity I change it to the second one. now it boot "normally", well since the first time I try wubi just before ubuntu start booting there are some warnings still not knowing if this is "normal". Now I can boot with out supergrub cd, and that is refreshing.

Still not knowing way Ubuntu release something so buggy in a LTS edition, so far bug after bug in either installation, nothing really bad yet quite annoying, Now ubuntu under windows is working for my quite good, we hope next releases a least some technical documentation included at the wubi install.

---

