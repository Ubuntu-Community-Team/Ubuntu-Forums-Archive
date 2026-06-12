---
title: "Using gparted"
date: 2008-06-23
forum: General Help
---

### Post by gregrae on 2008-06-23
I have a HD with the MBR corrupt,I have downloaded gparted live CD-0,3,4 -11  I have run this software and I am at a point where there is a command prompt and I do not know what to type in the prompt.
The prompt is written in orange , The prompt is    " parted ~ #  "
Can you help me.

---

### Post by lennartack on 2008-06-23
The gparted live cd should start a gui, so I think something went wrong. Do you see any error messages?

---

### Post by BUSHYBOB on 2008-06-23
Try typing sudo startx

---

### Post by gregrae on 2008-06-23
X.Org you need graphical environment 
Run forcevideo script
This is a summary of the display 
I think I require a video drivers but I do not understand If so how do I load video drivers

---

### Post by lennartack on 2008-06-24
You really need to give us some more information. WHY doesn't the gui start. What are the error messages? What is the output of sudo startx?

If the gparted livecd doesn't work you can always use the ubuntu livecd. Gparted is installed there too. Just go to System - Administration - Partition Editor.

---

### Post by danwood76 on 2008-06-24
I think what you need is the supergrub disk as opposed to the parted disk.
That way you can restore your MBR to grub.

---

