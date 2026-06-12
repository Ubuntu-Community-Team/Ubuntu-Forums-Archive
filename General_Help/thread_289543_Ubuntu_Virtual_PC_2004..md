---
title: "Ubuntu Virtual PC 2004."
date: 2006-10-31
forum: General Help
---

### Post by MacPC on 2006-10-31
Hi,

I have Microsoft's Virtual PC 2004 on my PC, the host OS is Windows 2000 pro. I installed Windows XP on one VM, it works great but I don't seem to be able to install Ubuntu. I tried using both Live CD and the Alternative CD. If someone here have successfully done this, would you mind telling me how?

Thanks alot.

MacPC

---

### Post by turkenator on 2006-10-31
umm i remember reading a while back it couldnt be installed because there was something in the linuxkernel that stopped it from werking on virtual pc u need an update to get it 2 work and virtual pc does not support linux if u can afford it try vmware its better and runs linux without any problems hope it helped

---

### Post by MacPC on 2006-10-31
Hi, 

I think it's possible to install Ubuntu on VM 2004, I read it some where else in this forum, it can be done. The problem I have installing it is that the VM screen can't display the menu, especially when it comes to the partitioner part of the installation, I can't see anything, so I can't partition the vitural disk space. I wonder if there is a way to change the screen size?

MacPC.

---

### Post by turkenator on 2006-11-01
which version of ubuntu are u trying to install maybe old versions have some problems or if its a new version try installing in text mode?

---

### Post by MacPC on 2006-11-08
I try to install 6.06. I used both live CD and in text mode. Any suggestions?

MacPC

---

### Post by Macmania on 2007-03-12
I installed Dapper 6.06.1 on a Dell Dimension PC with XP Home SP2 and VPC 2004. All I had to do was boot it up in safe graphics mode. Everything worked fine during the install. It worked great. On the VPC side select "new" and then "install your own operating system", when you get to the drop down menu to "select an operating system" select "unspecified". If it has "hard disk format" (which mine did) select "FAT32". When it asks you for a name I just put Linux but you can call it whatever you want. That's it. When you boot the OS from your VPC menu make sure you have the disc in your drive and it should boot to the live menu. Select "boot in safe graphics mode" and thats it. I didn't do that the first time and my screen went crazy. It will boot and go to the desktop where you will see the install icon and I think you can take it from there. The only problem I had was there is no sound because VPC simulates a Sound Blaster 16 sound card which is a little old and now unsupported by Creative Labs so the drivers are no longer available from them. You might have to hunt the driver down online. Also in the preferences menu of VPC make sure you adjust the system ram to at least 256mb but be careful to not go too high because VPC shares your actual system ram and if you only have like 512mb don't go over 256mb, as a general rule of thumb, when I set up a virtual machine I usually set the ram to about half of my actual ram. Set the video ram to 16mb which is as high as it will go so it will run smoothly. Good Luck!

---

