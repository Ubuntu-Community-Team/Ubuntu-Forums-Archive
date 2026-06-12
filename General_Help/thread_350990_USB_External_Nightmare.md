---
title: "USB External Nightmare"
date: 2007-02-01
forum: General Help
---

### Post by kurlee daddee on 2007-02-01
So I bought a USB external hard drive for a good price for the intentions of using it to run Ubuntu from. I was able to load Ubuntu onto the drive, but I cannot boot to the USB drive. 

I was told that my Toshiba laptop does not and will not have support for booting from USB drives.

Now for my problem. 

I loaded Ubuntu onto my USB drive and now I can't get Windows to recognize my drive at all. How do I erase Ubuntu off of my USB drive in order to use it on my Windows machine. 

Sorry for the newb question.

---

### Post by BoneSaw on 2007-02-01
you could try reformating it using the gparted live disc or the version of gparted thats on the live cd.

---

### Post by kurlee daddee on 2007-02-01
Actually, if I connect it to a Windows based machine, it recognizes the drive as a USB mass storage device. But it does not show in the Explorer tree as a drive. If I could somehow get to it from Explorer, I could reformat it.

---

### Post by kurlee daddee on 2007-02-01
Got it to work and all done.

For anyone else that has this problem. And yes this is Windows XP rules.

Go to My Computer and right-click. Choose Manage. 

You should see your USB drive there. 

I right clicked on the drive and deleted both partitions on it. Then reformatted it with a new partition in NTFS. It now works on Windows. YIPEEEE!!!!!:D

---

### Post by vincentvee on 2007-02-01
> **kurlee daddee said:**
> So I bought a USB external hard drive for a good price for the intentions of using it to run Ubuntu from. I was able to load Ubuntu onto the drive, but I cannot boot to the USB drive. 

I was told that my Toshiba laptop does not and will not have support for booting from USB drives.

Now for my problem. 

I loaded Ubuntu onto my USB drive and now I can't get Windows to recognize my drive at all. How do I erase Ubuntu off of my USB drive in order to use it on my Windows machine. 

Sorry for the newb question.
plug it into your windows box, go to control panel>administrative tools>computermanagement>disk management from the tree on the leftthen right click on the volume and click format, it's all prompts after that, easy huh?

---

