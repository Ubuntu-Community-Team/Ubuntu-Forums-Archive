---
title: "[Solved] Install issues - 13.04"
date: 2013-04-25
forum: General Help
---

### Post by FrogDemon on 2013-04-25
[B]So I used Unetbootin this time. The install is starting out just like before when I used Ubuntu Startup disk Creator in 12.10. 
 
 This is the first error I got last time. Am worried that if I continue the install will fail again. (As posted at the Ubuntu Facebook page)

[IMG]http://img850.imageshack.us/img850/4536/46122856144216722223517.jpg[/IMG]

I went ahead and tried to install it and once again, the install has failed. Don't know what else to try now. I have used Linux since 1995. Since then i have used many Distros. (mainly Ubuntu and Fedora) But l guess i will be going back to 12.10. But I refuse to do an in-place upgrade. I don't have hours to waste.[/B]

---

### Post by FrogDemon on 2013-04-25
So I decided to burn it to a disk and of course it failed once again. I give up. Y'all can keep Ubuntu 13.04. Ubuntu has been nothin but trouble since 10.04. Takes a miracle to get it installed. There is never any help coming and when it does, it's like we are the stupid ones and don't know what we are doing. 

It's been a great run, but I'm done.

---

### Post by FrogDemon on 2013-04-27
I guess I'm just a glutton for punishment. I dl'd Xubuntu and after starting avahi manually by using: 
> 
sudo /etc/init.d/avahi-daemon restart 

And the making the partitions maunually with the installer. The Xubuntu installer is actually working! No idea why the installer won't call avahi during install for me, but atleast starting it manually is getting the installer working. I just hope it doesn't fail.

---

### Post by dandroid13 on 2013-04-27
Try this in a terminal: ```
sudo usb-creator-gtk
``` and use it to create a bootable usb. I had no issues installing Raring.

---

### Post by FrogDemon on 2013-04-27
> **dandroid13 said:**
> Try this in a terminal: ```
sudo usb-creator-gtk
``` and use it to create a bootable usb. I had no issues installing Raring.
 
That's how I always start it. That way I don't have to input my pass while making the thumb drive.

Anyways, I just had to start gnome-keyring-daemon manually to get the installer going again. Hopefully the install doesn't fail on me again.

---

### Post by FrogDemon on 2013-04-27
Xubuntu is installed! After a bit of tweaking in the recovery terminal on boot. I now have it running. On first boot Xubuntu wouldn't load, so I restarted into recovery, I started network, installed missing items and system still wouldn't load to desktop. Restarted back into recovery and installed the nVidia drivers and I now have a running Xubuntu system.

---

