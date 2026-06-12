---
title: "Big Problem with Nvidia drivers"
date: 2007-06-03
forum: General Help
---

### Post by Nehvrook on 2007-06-03
Hi. I'm looking for some help with getting Nvidia drivers working properly.

On my PC I'm running Ubuntu 7.04 with an Nvidia 6600. I have the Nvidia drivers working fine, Beryl and games all work fine. I installed the Nvidia drivers by going to system > Preferences > Desktop Effects. It told me I needed the drivers to use the feature, I installed them through that menu and all games and stuff just worked from there.

The Problem is on my Girlfriends PC. She's also running Ubuntu 7.04 on an Nvidia 6600. Her system is dual boot with two hard drives. One for Windows one for Ubuntu. Everything works fine in Ubuntu, untill we try to install the Nvidia drivers.

First I tried to install them the same way I did it. I went to desktop effects, installed them. Re-started the PC for the changes to take effect. Grub comes up, I choose Ubuntu, it goes through the Ubuntu loading screen but then just displays a black screen. I can't ctlr alt backspace, I can't alt and F key to get the terminal up. Can't do anything. I don't even see the login screen.

So after this problem we re-installed Ubuntu formatting the hard drive and we installed the Nvidia drivers by the terminal. I can't remember the exact  command but it was something like "sudo apt-get install nvidia-glx-new". After doing this, exactly the same problem.

We formated again and installed Ubuntu again. This time I thought I'd install the legacy drivers via add/remove. Re-started the PC and this time we get a weird blue screen telling us what went wrong. Didn't understand it, but that time I managed to fix it by replacing my xorg.conf with a backup using:

```
cp /var/backups/xorg/xorg.conf.2007-06-01-00:41:47 /etc/x11/xorg.conf
```

So this fixed that problem but we're still left with her PC being unable to run games. She prefers Ubuntu but still spends most time in Windows because she plays WoW a lot.

If anyone can tell me a way to install the Nvidia drivers without causing this black screen (Or the other screen) please tell me. Or a way to fix this black screen when it happens.

Thank you for your time.

---

### Post by Nehvrook on 2007-06-04
Bump (I really need to get this sorted)

---

### Post by FuturePilot on 2007-06-04
Don't use the nvidia-glx-new package. Just try the nvidia-glx package```
sudo apt-get install nvidia-glx
```
Or go System>Administration>Restricted Drivers Manager
I have a Nvidia GeForce 6600 in my desktop and that's how I install the driver and it uses the nvidia-glx package.

If you still get a black screen boot in Recovery Mode and change the driver back to the nv driver by doing```
sudo nano -w /etc/X11/xorg.conf
```
Go down to the Device section and where it says "nvidia" change it to "nv"
Ctrl+x to save. Say yes when it asks you if you want to write the changes to the file then hit enter.
That will at least get you back to a graphical environment.

---

### Post by ashwin on 2007-06-04
i have a similar problem... i did that sudo apt-get install nvidia-glx and all the steps after that to install nvidia drivers. (by the way i have a 7600GT) in the restricted driver manager, it says that the drives in installed.. when i open desktop effects, it says"composite extension not available..... i dont know what to do!!!

---

### Post by Nehvrook on 2007-06-04
Okay thanks for the reply. We just tried installing with the command you gave us, same problem as before. Fortunatly changing nvidia to nv allowed us to get back to how things were, so we didn't have to format to fix it this time (Learning ftw)

However since we've had to disable the drivers again we're back to square one. Any more suggestions?

---

### Post by Gausian on 2007-06-04
[Nvidia Driver Install]("http://doc.gwos.org/index.php/Latest_nvidia_feisty")

Try that link.  I was having some troubles too, but following the steps here worked a treat

---

### Post by Nehvrook on 2007-06-04
Thanks, that link looks good. I won't be able to try it out today but I'll try it out as soon as possible and report back.

---

### Post by Nehvrook on 2007-06-07
Okay, I tried following the howto you posted. But still exactly the same problem :(

I just can't understand it

---

### Post by Nehvrook on 2007-06-07
Haha! Never mind. I've found a solution in this thread

[http://ubuntuforums.org/showthread.php?t=373003](http://ubuntuforums.org/showthread.php?t=373003)

Doing this suggestion I've managed to log into Ubuntu using the proper Nvidia drivers. I'm on installing World of Warcraft now to see if they are fully working :D

*Very happy*

EDIT: Yep tested it. WoW works :)
Thanks for all the suggestions guys :)

---

