---
title: "can't boot from Xubuntu 12.10 live CD"
date: 2013-01-01
forum: General Help
---

### Post by goodbye-windows(tm) on 2013-01-01
I want to install 12.10 (overwriting the old 11.10). The disk is the right size, 692MB. There were no errors when burning the image.

I have an old sata hard drive used for bulk storage and a newish 32 GB SSD. I disconnected the power and data cable from the hard drive as I want to make sure the data doesn't get corrupted, I wish to install Xubuntu 12.10 on the SSD.

When I press the F8 key during bootup, the dialog to change the bootup disk to the cd goes normally and the punchbox activates the CD drive activity light right away and it appears the machine is booting via the live cd.

But, it comes up into the standard log in window from the SSD instead....while the CD continues to run. The CD runs for an additional 30 seconds or so, but it eventually stops. The only option I am left with is to boot normally after selecting which user I want and after entering the proper password. 

I can't see any other way to boot using the live CD.

I tried to boot via the Xubuntu 12.04 CD, it works fine.

Is there some other procedure for starting a fresh install from a live CD?

ty.

Art

---

### Post by Cheesemill on 2013-01-01
Perhaps the iso file that you downloaded is corrupted, did you check the md5sum before burning the image to a disc?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by coldraven on 2013-01-01
I find it easier to create a bootable SD card, no wasted CDs and a 1GB card is cheap!
Unetbootin seems to be reliable or use "Startup Disc Creator".
But as Cheesmil says, check the MD5sum of the .ISO first.

---

### Post by goodbye-windows(tm) on 2013-01-03
I haven't found a reasonably priced card reader, but might convert to SD cards at some point.

I notice the release notes say 12.10 is incompatible with some hardware, and trying to boot to Xubuntu will result in failures.

I'm trying to download another 12.10 image now, but the isp is not cooperating. Will check the md5 sum when I can get the file downloaded. Unfortunately, I deleted the original file after I burned it to a CD. Another lesson learned::>

Will report progress or lack thereof later.

TY.

Art

---

### Post by goodbye-windows(tm) on 2013-01-03
MD5SUM checks ok, I'm burning a new CD now.

I use XFBURN, click  on burn image and select a slow burn speed. Not sure if there are checks  to be done in the burning process though.

---

### Post by mastablasta on 2013-01-03
> **goodbye-windows(tm) said:**
> MD5SUM checks ok, I'm burning a new CD now.
 
I use XFBURN, click on burn image and select a slow burn speed. Not sure if there are checks to be done in the burning process though.
 
 
in nero you can check the disk if it burned ok. another way to check it is in the grub menu that shows just after the boot.

---

### Post by goodbye-windows(tm) on 2013-01-03
Hi Mastablasta et al,

I'm not sure I want any part of nero as it's not open sourced and I remember the nightmares from attempting to use it under the brand W operating systems from many years ago.

The burn went ok in xfburn and I was able to boot into the live cd without incident. I notice they suggest a burnable DVD instead. Didn't have a burnable DVD, so I used a CD. I'll purchase a stack of burnable DVD's soon-have a new lightscribe burner and hopefully it runs ok under linux. 

TY to all who helped me get the job done!

Art

---

### Post by mastablasta on 2013-01-03
it is better to use USB instead. 4 GB usb will do wonders and you can load multiple versions of linux on it and then boto from it live. you can also make it persistant (a live USB that will save settings and drveirs...)

---

### Post by Calinou on 2013-01-03
> **coldraven said:**
> I find it easier to create a bootable SD card, no wasted CDs and a 1GB card is cheap!
Unetbootin seems to be reliable or use "Startup Disc Creator".
But as Cheesmil says, check the MD5sum of the .ISO first.

Few computers can boot from SD cards, but any computer from > 2007 can boot an USB drive, they are also cheap.

---

