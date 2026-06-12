---
title: "ubuntu loads but then just a blank screen"
date: 2007-04-22
forum: General Help
---

### Post by redneckracin on 2007-04-22
hey i updated the drivers for my nvidia 8600GT and when i restart i get the grub boot screen and i get the ubuntu load screen but then the screen just goes blank.

I am in recovery mode right now. What do i need to do to get my GUI back?

---

### Post by dcstar on 2007-04-22
> **redneckracin said:**
> hey i updated the drivers for my nvidia 8600GT and when i restart i get the grub boot screen and i get the ubuntu load screen but then the screen just goes blank.

I am in recovery mode right now. What do i need to do to get my GUI back?

```
sudo dpkg-reinstall xserver-xorg
```

Select the generic VESA driver to get a basic system going, and then do a forum search for install the NVIDIA drivers.

---

### Post by cubdukat on 2007-04-29
I am having the exact same problem, except I'm using Dapper. I've tried regenerating things, but that doesn't work at all.

I tried getting all of the individual parts for compiling a fresh driver from 9775 (i did manage to d/l 8755, but it took nearly an hour over dialup), but it won't let me.  I even tried installing Edgy over the entire thing, but it won't start X either.

Is it possible that the 8600 series is so new that not even Feisty has complete support?

---

### Post by Ekstreme on 2007-05-06
I'm having the exact same problem. Just bought a shiny new PC but I can't even run Ubuntu, well I can with the nv module, eeew

Has anyone managed to crack this?

---

### Post by cubdukat on 2007-05-06
We may have to wait until nVidia comes up with a new driver. This past weekend I ended up installing Suse 10.2 over Dapper 64-bit because the live CD wouldn't even start-up because X wouldn't load. After I installed the nVidia driver, it totally locked things up. Since the exact same thing happened on two different and fairly recent distros, I believe the problem's on nVidia's side.

Apparently the 8600GT's architecture is sufficiently different from the 8800 that it confuses the system.

One thing I noticed during startup was the phrase" "NVIDIA taints kernel." That's never a good sign. I haven't checked the logs to investigate further where the problem lies, but if it's doing that in Suse, it's probably doing it in Ubuntu as well.

I'm going to attempt to install Feisty Fawn over Suse tonight, since I'm no longer as enamored of it as I used to be. I've been using Ubuntu on my laptop more than I used Suse, so I'm more proficient with it. Not to mention Novell's being in bed with Microsoft...

In the meantime, I will hold off on installing programs like Blender...

---

### Post by cubdukat on 2007-05-07
Well, I managed to get Feisty 64-bit installed and working, but not without issues.

I tried using the Desktop CD to install it, but it wouldn't work because of the 8600GT card, so I ended up having to use the Kubuntu alternate CD to get it installed. I haven't attempted to get the restricted driver because apparently Kubuntu doesn't have the manager that Ubuntu has for it, so I'm downloading the Ubuntu and Xubuntu alternate CDs so that I can get those options as well.

Also, when I boot up, the power light on my monitor flashes orange, as if output to the card's been cut, but then it comes back on and I get the login screen. It strange that the splash screen wouldn't be displayed, but the login screen would. Believe you me, it caused me to reset the computer a few times before I realized what was happening.

I had a brief moment of panic last night because I attempted to have my monitor detected automatically. Kubuntu determined it was a PnP monitor (it's a Sampo AlphaScan 17mx), and I was unable to get a usable screen after rebooting, so I wiped out the frakked xorg.conf file and generated a new one, and everything was back to normal again. 

So far things seem to be quite good. Hopefully installing the restricted nVidia driver won't frak my system up again. nVidia really should have been more on the ball. It's not like they could totally kick the crap out of ATI so easily anymore. I dumped ATI because of their screwy drivers, and I'd hate to have to go back to them because their competition's no better.

---

### Post by Nythain on 2007-05-07
i've heard people with similar and or same problem resolving thier problem with
gksudo gedit (or sudo nano if you are in console) /boot/grub/menu.lst
and delete teh quiet splash (or splash quiet) options from the menu entries.
save and reboot... not sure if its a solution to everyones problem, but its helped some with similar symptoms

---

