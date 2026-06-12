---
title: "Bad hard drive. Ubuntu LiveCD 6.10 Help."
date: 2008-06-18
forum: General Help
---

### Post by ech0419 on 2008-06-18
Ok, long story so I'll just tell you what I have. 320gb Hard drive which is recognized by ubuntu 6.10 live but I cannot install an OS on it..? The file system is NTFS for the entire thing. No swap, nothing.  

I am running a live CD and I want to partition this volume, anything where I could put ubuntu/XP/Vista etc. The problem is that I cannot resize the volume. I know that 6.10 does not support the NTFS file system out of the box. Is there a way to run the gparted live CD from a flash drive? 

Remember I am using my only DVD drive/burner to run the Live CD so I cannot burn it thru this. 

Thanks.

---

### Post by Happy_Man on 2008-06-18
That is really odd. NTFS partitions should be able to be modified in Edgy's version of Gparted (I should know, that's the version I used when I installed Ubuntu for the first time). If you run GParted from a terminal, do any errors come up?

---

### Post by ech0419 on 2008-06-19
Hmm I heard elsewhere that it does not support NTFS resizing right off it needs a patch or a packages along with a driver... I don't get any errors if I run * sudo gparted * all I get is "Auto mounting disabled" which seems more like a notice then an error. 

I'm curious why it won't resize it, my XP and Vista disks both had trouble as well.

---

### Post by logos34 on 2008-06-19
> **ech0419 said:**
> Hmm **I heard elsewhere that it does not support NTFS resizing right off it needs a patch or a packages along with a driver**... I don't get any errors if I run * sudo gparted * all I get is "Auto mounting disabled" which seems more like a notice then an error. 

I'm curious** why it won't resize it**, my XP and Vista disks both had trouble as well.

You must be confusing ntfs write support...you'd need to install the ntfs-3g driver because pre-gutsy didn't suport it outof the box...

Edgy cd has the 0.2.7 version of Gparted, which I remember does not support resizing any partitions from the **left** side.  Is that perchance what you're trying to do?  Post a screenshot of gparted if you can.

If necessary get the [USB-flash version of the newest Gparted.]("http://gparted.sourceforge.net/liveusb.php")

---

### Post by ech0419 on 2008-06-19
Ok, I'm having a bit of trouble with the USB version. I am on a live CD so I can't really download a whole lot. (2GB file system) most of which is being used. 

I used an old recovery disk of mine called hiren's (heard of it?). Non of the HDD utilities could resize the Hard Drive. So I believe this is beyond that of Gparted. I am now quite clueless on what would allow me to resize it without formatting and losing the data I am trying so hard to save. 

[[IMG]http://img264.imageshack.us/img264/6492/screenshotxn0.png[/IMG]](http://imageshack.us)
[[IMG]http://img264.imageshack.us/img264/6492/screenshotxn0.07b27769e8.jpg[/IMG]](http://g.imageshack.us/g.php?h=264&i=screenshotxn0.png)

---

### Post by logos34 on 2008-06-19
I've heard of Hiren's.

Maybe there are some 'unmovable' files scattered at the end of the windows partition.  

Some things to try: 

boot back into windows and 

-defrag several times 
-run error-checking (with repair option)  (a.k.a chkdsk /r)
-turn down system restore to min.
-temporarily disable hibernation
- "              "   virtual/paging file

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)
(-->'Windows disk prep')

---

### Post by logos34 on 2008-06-19
ok, I just noticed you're trying to shrink it down to '256.36' gb--that's pretty aggressive!  Try it again but leave a little slack--windows needs at least 15% free space in order to run things like defrag and system utilities.  So maybe shave only ~7 gb off sda1.

That may have been the problem all along.

---

### Post by ech0419 on 2008-06-19
Well I don't have windows on it, also I can't install windows on it(unknown reason). I defraged the system quite often before. I had 2 hard drives 1 hard my opperating system files and recently accessed files, the second (this one) had all of my media and backed-up files to make my entire computer run faster. I used O&O defrag to constantly monitor it, defragging once a week. I think that may be the problem as well. 

The 1st drive (160GB) died completelty after plugging it into a new build and I am contacting OCZ, which is the company with the faulty part, about replacing it and compensating me for the loss of data on the drive.

---

### Post by ech0419 on 2008-06-19
Also, that was just an example, so I thru the slider back into the middle. I went as low as 512mb to no avail, I doubt it is the amount I'm taking away that's causing this.

---

### Post by logos34 on 2008-06-19
> **ech0419 said:**
> Also, that was just an example, so I thru the slider back into the middle. I went as low as 512mb to no avail, I doubt it is the amount I'm taking away that's causing this.

ok, I see now.

well, if it's just a non-system ntfs partition, I'm out of ideas.

---

### Post by ech0419 on 2008-06-19
Yeah it's just a regular NTFS partition. My guess is it was also affected when plugged into my new build. 

My power supply shorted and wont even turn on. OCZ(the manufacturer) wont answer there phone, takes a day to respond to emails and seems pretty shady when they ask me for my entire system so they can inspect it for damage that may have been caused by the power supply.

---

### Post by logos34 on 2008-06-19
You could run a hard disk diagnostic on it (from the livecd) using either hdparm or smartctl (for the latter you might have to download the smartmontools pkg)

---

### Post by ech0419 on 2008-06-19
Well I finally contacted OCZ, they sent me a prepaid slip to ship it down and have it inspected by one of their technicians. They also said they will replace anything damaged by their product in house, so how could I go wrong.

---

