---
title: "Will not complete shutdown"
date: 2013-06-16
forum: General Help
---

### Post by mayagrafix on 2013-06-16
Laptop freezes during the last part of shutdown or suspend process.

An old laptop, which has a non working CD-ROM, was given a new life via Ubuntu (Precise Pangolin 12.04), by removing the HDD, then connecting the HDD inside a USB external disk enclosure to a 64bit desktop and installing from there.  Upon completion, I extracted and re installed the HDD with the fresh Ubuntu OS back into the laptop. So far it works very well except for... shutdown and suspend. 

On **shutdown** it goes through the motions until the Ubuntu logo screen with the flashing circles appears, then it freezes (with the CPU still running at 100%). For **suspend** it just freezes on the desktop. Even after waiting a long time when either of these situations occur the shutdown process will not complete, so I have to press the power button for six seconds in order to provoke a hard shutdown. However, when I re-start the machine it boots up normally and apart from the shutdown problem, everything else works OK.

The laptop is a Compaq Presario 2100 Notebook PC with a one core AMD Athlon XP-M @ 1.86Ghz, 512 megs RAM, and a ATI Mobility Radeon XPRESS 200M AGP 4x GPU.

Thanks for your help.

---

### Post by mayagrafix on 2013-06-17
Here is a pix of the problematic laptop
[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/Presario2100_zps2050c5de.jpg[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/Presario2100_zps2050c5de.jpg.html)

---

### Post by matt_symes on 2013-06-17
Hi

In the first instance, try adding ```
acpi=off
``` to the kernel command line from the grub menu.

Boot into Ubuntu and then try to shutdown.

Does it shutdown cleanly with acpi disabled ?

Kind regards

---

### Post by mayagrafix on 2013-06-17
Ok, I followed these instructions to turn off ACPI
[http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting](http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting)
since the shift key upon startup did not work for me I went with a GUI option, a program called Boot-Repair. What happens now is that when Ubuntu boots into the desktop, the machine quits. Too much of good thing I guess!

---

### Post by mayagrafix on 2013-06-18
So I re instated the acpi option to ON in the GRUB menu and it seems to work again, but still same problem at shutdown.

---

### Post by matt_symes on 2013-06-18
Hi

Open a terminal and type

```
sudo shutdown -h now
```

Does it shutdown then ?

On the splash screen displayed, hit the <escape> key. That should hide the splash ssreen and display text on the screen. What are the last couple of lines  displayed ?

Kind regards

---

### Post by mayagrafix on 2013-06-18
Decided to start over and re installed Ubuntu 12.04. After installation finished, re installed HDD to laptop and booted new system. After a few minutes of testing, I tried Shutdown from menu and same thing. After rebooting also tried *sudo shutdown -h now* and same thing. Here is a screen cap (don't laugh, at least readable) of last lines
[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/StopScreen_zpsf6d9cb73.jpg[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/StopScreen_zpsf6d9cb73.jpg.html)
At this point machine stays in wait.

---

### Post by matt_symes on 2013-06-18
Hi

That line from your screen cap is interesting.

> umount: / is busy

It may be the cause of the problem.

I'll get back to this post soon.

EDIT:

There's one thing i want to check.

Please can you post the output of

```
lspci -nnk | grep -iA2 net
```

That's a captial A after grep.

I want to check the network drivers on your machine and unload the before shutdown.

I don't think this is the problem in your case but it will eliminate it.

Kind regards

---

### Post by mayagrafix on 2013-06-18
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
	Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network [103c:0024]
	Kernel driver in use: natsemi
	Kernel modules: natsemi

---

### Post by matt_symes on 2013-06-19
Hi

Before shutting down, open a terminal and type

```
sudo modprobe -r natsemi
```

Enter your password. It will not be echoed to the screen.

```
sudo service network-manager stop
```

```
sudo service networking stop
```

Then try to shutdown.

Does it still hang ?

Kind regards

---

### Post by mayagrafix on 2013-06-19
Greetings: **yes, still hangs.** However, even with a hard shutdown (by pressing the power off button) when this happens, the ol' laptop boots up again normally when powered on. Can this behavior damage the OS? I guess I'll have to live with a quirky old computer (10 years+). Otherwise, works perfectly in every other way. 

Thanks for your help.

---

