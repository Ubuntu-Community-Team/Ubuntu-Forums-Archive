---
title: "??  Can Grub dual boot  legacy sda  Ubuntu  and  UEFI  sdb Win7  ??"
date: 2014-07-03
forum: General Help
---

### Post by Gobugs on 2014-07-03
http:/paste.ubuntu.com/7739861

hardware is  ::   sda with MBR and Ubnutu 14
                            sdb with GUID part,  UEFI  Win 7
                            sdc  with GUID part, NTFS data drive

??  Is it possible to have Grub dual boot with legacy on drive one  and EFI on drive two  ??

Some how, I got this to work with Ubuntu 12  a couple of years ago, but unfortunately, I did not docment the "how to"   darn :(

On bootup Grub does not display and goes directly to Ubuntu on sda.  I tried update-grub with no changes.  I tried bootrepair ,  then update-grub, with no changes.
I can boot to drive one from BIOS,  but not to drive two.

Any suggestions on how to make this work?
Thanks

---

### Post by Gobugs on 2014-07-09
Dual booting with Grub2 using 2 drives, one in legacy boot mode (MBR), and the other in UEFI mode  Does Not Work.   I solved the problem by re-installing both in UEFI mode, playing around with BootRepair,  and THEN it worked.   Why?  I have no idea but I did explore lots of blind alleys in the process.

enjoy

---

### Post by oldfred on 2014-07-09
UEFI and BIOS are not compatible. So once you start booting in one mode you cannot switch to the other mode. And grub menu then can only boot systems in same boot mode.
You should have been able to dual boot from one time boot key, or UEFI/BIOS boot menus. But some systems may require turning on or off the UEFI or legacy boot mode first to correctly boot system installed in that mode.

Much better to have both installs in same boot mode as you eventually found out.

---

