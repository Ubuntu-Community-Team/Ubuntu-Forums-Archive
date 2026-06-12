---
title: "Reformat of Sandisk USB Device"
date: 2007-12-03
forum: General Help
---

### Post by JustinAlf on 2007-12-03
I searched the forum and feel as though I have a unique problem.  I set my sandisk up as a bootable Ubuntu drive, aka I made it a boot cd from the USB.  Now, I want to have it as a storage drive.  I have tried to reformat it using Gparted and QTparted, and it comes up as a read-only drive and will not let me make changes to it.  I have also tried to reformat it under windows and Mac, and it comes up as a CD in both.  How can I reformat this USB drive!?  Any help will be appreciated.

---

### Post by fjgaude on 2007-12-03
I believe Parted Magic 1.9 can do what you wish. Do a Google and you should find its website for free download.

---

### Post by JustinAlf on 2007-12-03
I was hoping for an easy command line solution to my problem.  Any suggestions?  and why and I locked out from using Gparted or QT Parted?

---

### Post by bingoUV on 2007-12-03
> **JustinAlf said:**
> I was hoping for an easy command line solution to my problem.  Any suggestions?  and why and I locked out from using Gparted or QT Parted?


In Gparted, unmount the drive before trying to format it. Right click, unmount.

---

### Post by JustinAlf on 2007-12-05
Got it.  I did have it unmounted when trying to reformat it, but Gparted still wouldn't disolve the partitions I made with OSX.  Here is what i did [http://www.linuxforums.org/forum/linux-newbie/19316-how-format-usb-drive.html]("http://www.linuxforums.org/forum/linux-newbie/19316-how-format-usb-drive.html")
Thats What helped me.

---

### Post by drs305 on 2007-12-05
I am also trying to reformat a USB drive. It's a 512MB drive. fdisk reports 514MB but whenever I try to reformat it via fsdk and then check the contents it yields 490MB. I once had tried to make it bootable. Has the extra space been reserved? If so, how to I recover it? I can't get it back by reformatting the drive with either fdisk or gparted. Perhaps I just never noticed it always only had 490MB available.

---

### Post by Driv3r912 on 2007-12-05
Right-click on your flash drive icon and click Properties.

Select the Permissions tab, and make sure you have everything selected as "Read and Write".

Now try to format.

---

