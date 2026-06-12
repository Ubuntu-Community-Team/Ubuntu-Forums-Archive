---
title: "Unable to boot into Windows 10 or Ubuntu from GRUB"
date: 2016-10-12
forum: General Help
---

### Post by nigmac on 2016-10-12
2 nights ago, I left my dual boot machine installing some Windows Updates for Windows 10 and went to bed. It was shutdown in the morning so I assumed installation went OK. Having turned my machine back on it can't find grub.
I've followed the steps here [http://askubuntu.com/questions/654316/windows-10-and-ubuntu-dual-boot/654994#654994](http://askubuntu.com/questions/654316/windows-10-and-ubuntu-dual-boot/654994#654994)
and all partitions return unkown filesystem when I run the ls command. I have tried setting the prefix and root to the filesystem I believe to be the one I installed ubuntu in but no luck.
I've used a  UbuntuLive cd to boot from CD into Ubuntu. This shows only my Windows partitions/filesystems that can be mounted.
I've also booted my machine using gparted CD and that shows the partitions I know to be the linux and swap as unformatted. 
Any ideas or do I need to reinstall Ubuntu over the partitions that now seem to be unformatted?

Thanks

---

### Post by oldfred on 2016-10-12
Was this a system with Windows 8 or 10 pre-installed and UEFI. Or an upgrade from Windows 7 with BIOS/MBR partitioning?

If UEFI can you use UEFI one time boot key, often f10 or f12, check manual to boot ubuntu entry?

If BIOS it may have "forgotten" to write Linux partition to partition table. It is still there and can usually be easily recovered with parted rescue or testdisk.

Post this:
sudo parted -l

---

### Post by nigmac on 2016-10-13
This was a system I built myself many years ago. I used to run Win7/Ubuntu then I upgraded to Win10/Ubuntu but that was months ago and it has been running fine until a couple of nights ago. This incident occurred following a regular Windows Update (When I can get back into Windows I can find out the details of what was installed but I need to resolve this issue first). 

Any suggestions on how I remind my machine that the two partitions (hd0, msdos2) and (hd1, msdos5) that it thinks are unknown actually contain ubuntu/grub and swap space respectively?

---

### Post by oldfred on 2016-10-13
Windows in BIOS mode and if your Linux partition is a logical partition, will "forget" to rewrite the logical partitions.

 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

