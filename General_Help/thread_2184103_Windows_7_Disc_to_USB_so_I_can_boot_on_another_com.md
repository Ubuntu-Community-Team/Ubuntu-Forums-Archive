---
title: "Windows 7 Disc to USB so I can boot on another computer"
date: 2013-10-27
forum: General Help
---

### Post by jcoop114 on 2013-10-27
My MacBook has Parallels, but I guess I lost my iso for Windows on it. I have the disc, but my MacBook cd drive is broken. I need to transfer the disk to usb drive. Then I want to plug that USB drive into my MacBook so I can re-install windows onto my Parellels.

So far, I've extracted all the files from the disk, but I can't find any iso. Am I supposed to covert all these files from the disk into an iso? If so, how can I do that? I think I need the iso to create a bootable usb drive, right?

---

### Post by JKyleOKC on 2013-10-27
> **jcoop114 said:**
> So far, I've extracted all the files from the disk, but I can't find any iso. Am I supposed to covert all these files from the disk into an iso? If so, how can I do that? I think I need the iso to create a bootable usb drive, right?Yes, you need the ISO to create a bootable USB, but you won't find it stored on the disk -- it **IS** the disk (in a roundabout fashion). Basically, the ISO file is a bit-for-bit image of the entire CD, not just the files that it contains.

One way to create it is to put the CD into your working drive, open a terminal, and issue the command "dd if=/dev/cdrom of=$HOME/Win7.iso" (no need to mount the CD first). However that command can be dangerous, since any typing error such as adding a blank space in the wrong place can destroy your system; the "dd" command is known as "data destroyer" for a very good reason!

If you have the "brasero" CD-burning package on your system, I'm told that it has an option to create an ISO file from a CD (it's "Disk Copy" in the opening menu). That probably does the very same thing as the "dd" command but with safeguards to make sure nothing gets damaged, and is what I'd recommend.

---

### Post by jcoop114 on 2013-10-27
Brasero allows me to create Data Project, Disc Copy, and Burn Image. Data Project and Burn Image tell me to choose a file, but it won't allow me to choose the entire folder or disc. Disc copy seems to recognize the disc as a whole, but when I select it from the dropdown, it won't work; the select menu just reverts back to blank.

---

### Post by JKyleOKC on 2013-10-27
In brasero, select Disk Copy. That gets you a dialog with two entry boxes. In the upper one, select your Win7 CD. In the lower, pull down the arrow symbol and select "image file," then give the file a name. Finally, click on "Create Image" and it will do the job.

---

