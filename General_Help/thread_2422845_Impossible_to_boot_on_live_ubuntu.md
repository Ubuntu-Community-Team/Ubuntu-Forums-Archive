---
title: "Impossible to boot on live ubuntu"
date: 2019-07-13
forum: General Help
---

### Post by roxus2 on 2019-07-13
Hi all,

I am trying to boot on Ubuntu to repair grub (after Windows 10 install) but I have the following errors :

[https://photos.app.goo.gl/WRmrEMXHT1YApqWD8](https://photos.app.goo.gl/WRmrEMXHT1YApqWD8)

With two usb... 

Someone can help me ?

---

### Post by oldfred on 2019-07-13
UEFI or BIOS installs?
Both Windows & Ubuntu need to be same, both UEFI/gpt or both the now old BIOS/MBR configuration.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

 Note that grub only boots working Windows. Or if Window need chkdsk or is hibernated then grub will not boot it, but if UEFI install, you should still be able to boot from UEFI boot menu.
Windows updates also turn fast start up back on which is just hibernation. That then grub will not boot it, or any NTFS partitions will not mount read/write in Ubuntu.

---

### Post by roxus2 on 2019-07-13
Thank you for your response !

It is a UEFI, sorry but I dont understand what I have to do ? &#128580;

---

### Post by oldfred on 2019-07-13
Using Ubuntu live installer download the Boot-Repair program. Instructions to copy & paste in link.
And then only run report, not any fixes, yet until someone can review report.
Only post link it gives to pastebin site, do not post full report, usually too large anyway.

---

### Post by roxus2 on 2019-07-14
Thx for your reponse:

Here the pastebin : [http://paste.ubuntu.com/p/B4D4h6fCvr/](http://paste.ubuntu.com/p/B4D4h6fCvr/)

I am able to live boot on a specific repair boot image (live ubuntu see my photo in my first post).

Grub2 is ok and now I can choose Ubuntu or Windows. Windows work great but ubuntu stuck on purple screen ! When I choose rescue mode I have the same issue that I have with live ubuntu (see my photo in my first post)...

---

### Post by roxus2 on 2019-07-14
I can't install another dist (arch, ubuntu) from USB, I have the same errors (Failed to start ...)

---

### Post by roxus2 on 2019-07-14
Ok I have found the issue, the new Ryzen aren't ok with last linux distribution (AMD will release a new BIOS with this patch) :

[FONT=Helvetica]https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix[/FONT]

---

### Post by oldfred on 2019-07-14
It looks like 18.04 still works, but not newer distributions.

With nVidia you will need nomodeset until you install & then add the nVidia driver from Ubuntu repository. With 19.04, if you check add proprietary drivers, it also adds the preferred nVidia driver.

With Windows you have to make sure that on updates it has not turned fast start up back on. Grub only boots working Windows or Windows that is not hibernated nor needs chkdsk.  Fast Start up turns on the hibernation flag. Usually you can directly boot Windows from UEFI boot menu and maybe f8 into repair console. But best to also have a Windows 10 repair/recovery flash drive or installer with repair console.

---

