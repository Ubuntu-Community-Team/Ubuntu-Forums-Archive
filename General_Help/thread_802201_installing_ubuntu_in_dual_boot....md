---
title: "installing ubuntu in dual boot..."
date: 2008-05-21
forum: General Help
---

### Post by Mia_tech on 2008-05-21
I have windows xp installed in my laptop and I want to install ubuntu, is there any way to repartition the hard drive without having to wipe it out and reinstalling xp again, I've tried booting with the systemrescuecd and using gparted to resize the hard drive partitions but didn't work....

any help appreciated

thanks

---

### Post by ibuclaw on 2008-05-21
First, make sure that you have at least 50% of disk space free on your Windows Install.

Then get a powerful defrag tool to compact up your files on the disk.
ie: So the Windows defrag tool will show an analysis image like this:
[PHP]Analysis of C:\
start:'#############              ':end[/PHP]
Basically, there is nothing but white space in the second half of the image.

Then boot into the Ubuntu LiveCD and install.
Ubuntu uses a somewhat forceful algorithm to cut out a portion of the NTFS partition and format that slice into an ext3 format.

Select the default option ("Install on Free Space" I think...) in the installer.

Regards
Iain

---

### Post by Mia_tech on 2008-05-27
what defrag tools are available for windows besides the one that comes with the installation?

thanks

---

### Post by HuntMike79 on 2008-05-28
Try JkDefrag

---

### Post by cybrsaylr on 2008-05-28
When I did a dual boot with XP & Ubuntu I used the XP defrag with no problems. After the defrag I used the Ubuntu install tools to do the rest and everything works fine. 

I had XP on a 40GB partition with the rest used as storage partition. I split the 40GB in half, 20GB for XP, 20GB for Ubuntu and have been using it this way about a year now with no problems. The rest of the HDD is for storage.

---

