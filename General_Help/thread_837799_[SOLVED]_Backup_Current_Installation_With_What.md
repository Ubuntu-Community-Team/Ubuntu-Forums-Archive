---
title: "[SOLVED] Backup Current Installation With What?"
date: 2008-06-22
forum: General Help
---

### Post by Spaceman9 on 2008-06-22
I need something that will copy my current installation of Ubuntu 8.04 so if I mess up my current installation I can restore it from the copy. Would “bootcd” do that and if so how do I use it? Can I make the copy on a CD-RW? I have a root partition and a home partition in my current installation. Thankx for any help.

---

### Post by iaculallad on 2008-06-22
Try to use [SystemRescueCD]("http://www.sysresccd.org/Main_Page") instead.
Here's a [tutorial]("http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php") on how to create a drive image.

---

### Post by macaholic on 2008-06-22
I don't know about bootcd, but you could always try sbackup, you can install it via synaptic or with sudo apt-get install sbackup

---

### Post by cariboo on 2008-06-22
You could also try partimage. It will make an image of your partition, it will only backup used sectors of the hard drive. Partimage is available in the repositories and you can use synaptic to install it.

Jim

---

### Post by steveneddy on 2008-06-23
Personally I just copy my /home to a USB stick so all of my settings and photos and stuff are saved. 

I can always reinstall the apps I need.

My .02 .

---

### Post by Spaceman9 on 2008-06-23
Iaculallad I got SystemRescueCD and it looks like it will do what I need. Thankx for the help.

Macaholic I installed sbackup and I'll check it out. Thankx for the help.

Cariboo907 I installed partimage and I'll check it out. Thankx for the help.

Steveneddy I really have a ton of apps installed including all of Ubuntu Studio and KDE and it would take me many days to reinstall all of it. Thankx for your help.

---

