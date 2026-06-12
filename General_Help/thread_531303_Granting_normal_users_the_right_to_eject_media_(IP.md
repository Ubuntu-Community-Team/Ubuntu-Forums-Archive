---
title: "Granting normal users the right to eject media (IPOD)"
date: 2007-08-21
forum: General Help
---

### Post by eyemou on 2007-08-21
I was wondering if someone could tell me how to grant my normal user account ownership over my iPod, when mounted, or to at least allow that account to 'eject' the device.

At present, I need to open a console and 'sudo eject /media/IPOD' in order to dismount it. I figure that if I can get this working without sudo, I can just add this task to my taskbar/kicker, in a handy button.

Any ideas?

[i](I do realize that I could always right-click on the Desktop icon for the iPod and select "safely remove" from the menu, but I am in the midst of ironing out the conky + KDE 'disappearing icons' issue at the moment.

And if I can figure out how to allow my normal user account to issue the 'eject' command, without using sudo, then I can really drag my heels on the disappearing icons issue, as I almost NEVER put anything on my desktop to begin with...)[/i]

---

### Post by Dave54 on 2007-08-21
Well, i have a couple ideas, but I'm not sure if they would work, especially in kde.

1. look into pmount (sudo apt-get install pmount).

2. I used this method to make my hard drive user-mountable, but it might work with your IPOD.
run:```
sudo fdisk -l
``` with your ipod connected and figure out your device name (/dev/sdxy)
run: ```
gksudo gedit /etc/fstab
``` (gedit is a text editor, replace it with whatever one you use) and add the line ```
/dev/sdxy	/media/IPOD	auto	rw,user,noauto		0	0
``` I'm really not sure if that will work on a removable device tho.

3. you don't need the icon to eject it (in gnome, anyway). Go to "Places", select your device, and in the window that pops up, right-click on the white space and select "unmount volume".

---

