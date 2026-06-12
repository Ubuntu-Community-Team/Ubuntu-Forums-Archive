---
title: "Ubuntu 12.04 boot issue (help!)"
date: 2012-11-07
forum: General Help
---

### Post by Sophisto13 on 2012-11-07
Hello, 

New Ubuntu user here...  I started using 12.04 on its release and I simply installed it along side windows and it worked fine..  Now I have chosen to place it on its own hard drive and run as dual boot. 

After the successful installation, I rebooted and GRUB picked up Windows7 on my other drive as expected. While windows boots fine, Ubuntu starts to boot only with a solid purple screen (no logo splash screen) and I proceed to get an error.

ERROR: Couldn't read file
ERROR: You must load Kernel first

I am unable to boot into recovery due to the same error messages.  I ran a Grub repair boot disk and upon completion I saved the log which you can find here: [http://paste.debian.net/207112/](http://paste.debian.net/207112/)

Can anyone point me in the right direction to get this to load and work as it should?

Thanks,

---

### Post by Sophisto13 on 2012-11-08
TTT!

Anyone know these errors?

ERROR: Couldn't read file
ERROR: You must load Kernel first

---

### Post by pqwoerituytrueiwoq on 2012-11-08
boot a live cd and use it to run fsck, via check in the context menu (partition must be unmounted)
[[IMG]http://www.zimagez.com/miniature/screenshot-11082012-033719pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-11082012-033719pm.php")
also you have 2 bootable disk drives, be sure you are booting the correct one, it is set in your bios

---

### Post by Sophisto13 on 2012-11-08
> **pqwoerituytrueiwoq said:**
> boot a live cd and use it to run fsck, via check in the context menu (partition must be unmounted)
[[IMG]http://www.zimagez.com/miniature/screenshot-11082012-033719pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-11082012-033719pm.php")
also you have 2 bootable disk drives, be sure you are booting the correct one, it is set in your bios


ok I booted with my Live key and checked the disk.. It found a bunch of problems but didnt fix the problem.  The Kernel still wont load and it just boots me back to the Grub menu..

What else could I try?

---

### Post by pqwoerituytrueiwoq on 2012-11-08
lots of errors, i would check the gnome-disk-utility/gsmartcontrol for SMART info from the hdd

---

### Post by Sophisto13 on 2012-11-08
> **pqwoerituytrueiwoq said:**
> lots of errors, i would check the gnome-disk-utility/gsmartcontrol for SMART info from the hdd

Ran Disk Util through my live key..   It fails the smart test due to having 703 bad sectors...  Should I assume this is the problem then?

---

### Post by pqwoerituytrueiwoq on 2012-11-08
your hdd is failing, backup important files and save up for a replacement
attempt to reinstall, and hope it works

---

### Post by Sophisto13 on 2012-11-08
> **pqwoerituytrueiwoq said:**
> your hdd is failing, backup important files and save up for a replacement
attempt to reinstall, and hope it works

It was an older drive I had laying around and thought to use it..   Windows is on my primary,  I guess I could add a partition to it and run both OS off it..  just like the idea of separate disks better..  

Thanks for your help!

---

### Post by oldfred on 2012-11-09
Grub2 has created work arounds for flexnet, but you have flexnet and it hides serial number info in the same space grub likes to use for core.img in sector 32 or there abouts.

Are you using some proprietary Windows software like Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab and some others the use DRM from flexnet. 

If using the proprietary software it just may be better to leave the Windows boot loader in sda and acquire another drive for Ubuntu.

---

