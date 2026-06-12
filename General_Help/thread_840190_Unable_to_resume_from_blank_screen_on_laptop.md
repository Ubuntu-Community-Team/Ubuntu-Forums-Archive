---
title: "Unable to resume from blank screen on laptop"
date: 2008-06-25
forum: General Help
---

### Post by Ninja Catfish on 2008-06-25
I'm having a bit of an issue with Hardy Heron 32-bit. Whenever I leave my laptop for any extended period of time inactive, the screen will turn off, fair enough. But when I try to use it again, the screen once again lights up, however it remains a black screen. I've tried tapping the power button on the laptop, pressing every button on the keyboard, moving the mouse, clicking the mouse, trying any of the other laptop controls (volume, media button, mute) and they do nothing. I have to force a power off by holding the power button, and reboot from there.
It's only doing this while running Ubuntu, and it does the same thing when I close the laptop lid also.

I've gone into power management settings and have it set to do nothing after a period of inactivity, and when the lid is closed, but the issue just keeps happening.

When this happens though, the system still actually responds, just the screen stays blank. For example, Caps Lock light comes on, and when I randomly hit a bunch of keys (had Firefox open before screen went blank) they went into the Firefox address bar, and I know this because when I rebooted I was able to restore the previous Firefox session and a blank tab with all the random text was in the address bar.

I have all the latest updates directly from Update manager.

I'm running Ubuntu on a Compaq V6000 laptop, with a GeForce Go 6150 graphics chip. I have installed the nVidia drivers from the Hardware options in Ubuntu.

Any ideas?

---

### Post by psoplayer on 2008-06-26
Same story here. Only this time the laptop is a HP Pavilion dv6000 series (same video chipset).

---

### Post by heathen on 2008-06-26
just posted something similar to this myself...  Compaq V6000  running amd64..

---

### Post by Ninja Catfish on 2008-06-28
Well at least I'm not the only one. It's one of the very few issues I'm still having with Ubuntu.

---

### Post by heathen on 2008-06-28
This is the first time I've had the issue, so it seems to be something with 8.04

---

### Post by alterpinguin on 2008-07-05
same on a MSI-laptop with nvidia go-graphic-chipset,
one thing: it never happened with ubuntu 7.04, there
on closing the laptop-screen, the screen went black and
after open again forced the user to enter the password.
Now with ubuntu 8.0x, the screen goes black, no way to 
switch to console-screens with strg-alt-F1/2/3
-
first workaround: disabled in powersettings
(menu->system->power-administration) the option to go to black at
closing-laptop - after setting this to "ignore", closing and opening
the screen works again.
The screen still goes black, which seems to be a hardware-bios-kind-switch
and sometimes the screen is a bit garbeled, then switching to console (strg-alt-f1) and back does the right refresh.
Starting with "vga=normal" did change nothing, but setting a lower memory (only 128 instead of 256) for the graphics-card made the switch to the text-console no more possible.

I can remember those problems from the early x11-days, could be a low-level timing problem.

---

### Post by Paradoxfox93 on 2008-07-12
Ditto...exactly.  Except that if it screen saves while open the same thing happens without even closing the lid.

---

### Post by alterpinguin on 2008-07-26
> **alterpinguin said:**
> same on a MSI-laptop with nvidia go-graphic-chipset,
one thing: it never happened with ubuntu 7.04, there
on closing the laptop-screen, the screen went black and
after open again forced the user to enter the password.
Now with ubuntu 8.0x, the screen goes black, no way to 
switch to console-screens with strg-alt-F1/2/3
-
first workaround: disabled in powersettings
(menu->system->power-administration) the option to go to black at
closing-laptop - after setting this to "ignore", closing and opening
the screen works again.
The screen still goes black, which seems to be a hardware-bios-kind-switch
and sometimes the screen is a bit garbeled, then switching to console (strg-alt-f1) and back does the right refresh.
Starting with "vga=normal" did change nothing, but setting a lower memory (only 128 instead of 256) for the graphics-card made the switch to the text-console no more possible.

I can remember those problems from the early x11-days, could be a low-level timing problem.

I had some time to try the normal (non-hardware) nvidia driver (nv) and noticed the problem went away. There is a second hardware-specific nvidia driver with name "envy" as part of its name. I installed this one and it worked again like with ubuntu 7.04 version, switching to character console (ctrl-alt-F1/F2..) no more garbeled or black screen. Same when closing the desktop, screen goes black and comes back again. Suspend does work now (shutdown with blinking powersave-light and restart with normal screen and running apps again (no more black screen). Because i had to change nothing special in the settings for acpi i would everyone suggest to try first the non-nvidia driver (you can get it if you boot the "resume kernel" and choose fix the x11 display, this will use the nv-driver (without 3d-acceleration)) and check you have no problems with your hardware or with some acpi-settings. If it works, try the envy-driver, there must be some difference because it had no special problems to restore the screen-settings.

---

### Post by gregalynch on 2008-09-18
I'm having the same problem on my Dell laptop.  When I close the lid I get a black screen that I cannot get out of.  

I'm a bit of a newbie.  In the last post you say to 'boot the resume kernel'.  What does this mean/how do I do it?

---

### Post by starcannon on 2008-09-19
Same problem here on Nvidia 6150 go, in a dv6xxx series HP. Suspend/Resume works beautifully, but blank-screen when lid is closed or computer is inactive will not resume without a CTRL-ALT-Backspace.

---

### Post by starcannon on 2008-09-19
I installed the latest driver from nvidia.com, problem fixed.

---

### Post by gregalynch on 2008-09-19
which driver is it that you installed?

---

### Post by starcannon on 2008-09-19
I used these drivers:
[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

I wrote an nvidia install guide, which I had hoped was now an outdated post since the Ubuntu Hardware Drivers Installer{System>Administration>Hardware Drives} was doing such a nice job. Unfortunately the driver that Ubuntu has stashed in the repositories is old and outdated and really needs to be updated. The machine I'm working on is a Vista with Wubi Install I am doing for a client, I discovered the driver flaw when I compared the driver version to the driver version on my wifes dv2000(I do manual driver installs on my own machines); Her laptop suspends/resumes great, and wakes from blank screen just fine, so I tried the latest driver from Nvidia using manual install and it fixed the 6150 Go's issues. At the bottom of the guide is a link to another guide that will keep the driver updated when kernel changes, if your doing this for someone else it is advisable to go through the extra step so as to make future tech support problems concerning the nvidia gpu less probable. 

You can find my guide here(don't skip steps):
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

That has the Nvidia 6150 Go graphics in this HP Pavilion dv6325us working perfectly, suspend/resume, wake from blank screen, excellent 3d and 2d performance. Indeed it(the entire laptop) is now a linux 100%er.

GL and Have fun.

---

### Post by gregalynch on 2008-09-23
Thanks for the guide.  I went through all the steps but when I went to install the new nvidia driver it said that it had to construct a new kernel (or something like that) and when it tried to do so it failed.  I'm not sure if I'm even running nvidia as my graphics driver, so it might be completely unrelated to the problem.

---

