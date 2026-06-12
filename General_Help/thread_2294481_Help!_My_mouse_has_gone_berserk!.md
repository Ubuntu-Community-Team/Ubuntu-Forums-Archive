---
title: "Help! My mouse has gone berserk!"
date: 2015-09-11
forum: General Help
---

### Post by Ilmari on 2015-09-11
After login and using my computer for a little while my mouse cursor suddenly goes out of control moving around and clicking at random. I've tried cleaning my track pad but that doesn't seem to help. Rebooting fixes the problem for a few minutes before the mouse starts acting up again. Any ideas?

Here is a short video of what is happening:
[https://youtu.be/cQwRJyk__wg](https://youtu.be/cQwRJyk__wg)

My computer (running Ubuntu 14.04LTS):
-Acer Aspire ES1-111 11,6"



[LIST]
[*]Intel Celeron N2840 Dual-Core 2,16 GHz
[*]2 Gt (1 x 2 GB) DDR3L 1600 MHz
[*]32 Gt eMMC
[*]11,6" WXGA (1366x768) LED
[*]Intel HD Graphics
[*]WiFi b/g/n, Gigabit Ethernet, Bluetooth 4.0+HS
[*]Web-cam
[*]SD card reader (SDXC compatible)
[*]USB 2.0, USB 3.0, HDMI
[/LIST]

---

### Post by ventrical on 2015-09-11
Is that an older tack-ball mouse? I still use them. I have ssen such behaviour. You have to clean the ball n' wheels inside the mouse. Cotton swabs, isopropyl and a skewer stick. Some times grunge builds up on the tracking rollers and it causes abberant behaviour. You have to actually scape it off the rollers then clean and vacume.

regards..

---

### Post by Ilmari on 2015-09-12
Thanks for replying. The laptop doesn't have that ball-mouse-thing. It's a modern laptop (from 2014 I believe?).

Any help is appreciated!

---

### Post by Old_Grey_Wolf on 2015-09-12
Have you enabled remote desktop sharing?

---

### Post by Ilmari on 2015-09-12
No! (creepy thought though!) 

This is a clean install of 14.04 LTS. I had the same problem on my previous install using Lubuntu 14.04 LTS.

---

### Post by nknwn on 2015-09-12
Does the same happen when it is powered by battery only?

If it doesn't then you likely have an incompatible power cable.
Power cables effect the touchpad.

---

### Post by chemist931 on 2015-09-12
Maybe this will work:
sudo service lightdm restart

My laptop frequently has cursor-related problems and this fixes them.

---

### Post by Ilmari on 2015-09-13
Thanks for replying guys. 

There is no change with having the power cable on, it seems.

"sudo service lightdm restart" seems to just show a black screen and crash the computer.

I'm going to university next week so I'm in a little bit of trouble!

---

### Post by pqwoerituytrueiwoq on 2015-09-13
you have to run that on a tty or it only stops the service
press ctrl+alt+f1 to get to a tty login

i doubt that will solve the issue you ar having, even if it does you will have to do every boot
maybe you can disable a driver so another one will be used, maybe a newer kernel will work better
maybe the 3.19 will work (test a live 14.04.3 disk)
if that works you can install it like this
[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#LTS_Hardware_Enablement_Stack)
you can also try the mainline 4.2 kernel, here is a installer for that
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

---

### Post by Ilmari on 2015-09-15
Yep "sudo service lightdm restart" unfortunately does nothing to help with this issue.

How would I go about disabling drivers? Could you direct me to a tutorial?

Will test different kernel versions thanks.

---

### Post by Ilmari on 2015-09-25
Up? Problem is still present.

---

### Post by pqwoerituytrueiwoq on 2015-09-25
you can disable drivers by putting the name of it in this file
/etc/modprobe.d/blacklist.conf
im not sure how to find out what driver a mouse is using though, it could also be the one the keyboard uses

with the restart lightdm part do it from a tty (ctrl+alt+f1) not the gui
if you do it from the giu it stops the process and never starts the giu again

---

### Post by Ilmari on 2015-10-05
Thanks for replying!

I think the touchpad driver is the 1.8.1 version of "xserver-xorg-input-synaptics-lts-vivid"

In Synaptic I noticed there was a 1.7.4 version of the driver but I can't seem to install it through synaptic or the terminal. Is reverting to this driver even possible?

How would blacklisting the driver help? Wouldn't that just turn off the touchpad?

By the way, I've tried to restart the touchpad using e.g. "sudo modprobe -r psmouse" or "synclient touchpadOff=0" but these don't seem to do it. Would there be any other work-around commands that I could try?

Thanks again!

---

### Post by Ilmari on 2015-10-10
Up?

---

### Post by J_Me on 2015-10-10
Did you spill any liquid on your laptop at any time. I've had a drawing tablet do strange things like this, turned out that the beer I spilt next to it seeped into the plastic layers and stayed there for ages. Just a thought

---

### Post by nknwn on 2015-10-10
Maybe try running on a Windows live disk (Hirens or UBCD) to check if the problem exists while running different software. If it does then there is a problem with the hardware. 
Did the problem start at some point or has this computer always had this problem?

---

### Post by deathbyfreezeray on 2015-10-12
I have this very same computer. Is your computer running in UEFI or bios mode? Also, in bios (UEFI) settings, is the touchpad set to "advanced" or "basic" mode? This webpage also makes a note that an immediate but temporary solution is to use "fn-F7" twice to disable and enable the touchpad: [http://blog.mdda.net/oss/2014/11/16/acer-e11-es1-111-c3nt-linux/](http://blog.mdda.net/oss/2014/11/16/acer-e11-es1-111-c3nt-linux/)
I found that running Ubuntu in UEFI mode with touchpad set to "advanced" (or bios with touchpad set to "basic"), I do not encounter this problem, however, somewhere in intermittent installs (I had some issues setting up at first), I had encountered it.

My current configuration in which the problem is never present is Ubuntu 15.04 in UEFI with touchpad set to "advanced" and secureboot enabled. I upgraded from Ubuntu 14.04, where it had also worked just fine in those conditions.

P.S. It may be worth adding that while I believe this is a software configuration problem, the comments in the link I provided claim otherwise, with evidence suggesting a hardware issue. So it may still be worthwhile to test windows for a day and check if the issue persists.

---

### Post by Ilmari on 2015-10-14
Thanks for your help! 

My bios is indeed UEFI, but interestingly enough the touchpad option was set to basic. I set the option to advanced but the problem persists. I feel that this might be a hardware issue. 

The "fn-F7" solution is pretty handy though! Thanks for that. It feels like a solid work-around.

Marking this thread as solved. Check out the link provided by [**[COLOR=#000000]deathbyfreezeray[/COLOR]**[COLOR=#000000] above [/COLOR]]("http://ubuntuforums.org/member.php?u=1850177")if you have similar problem with this laptop.

[http://blog.mdda.net/oss/2014/11/16/acer-e11-es1-111-c3nt-linux/](http://blog.mdda.net/oss/2014/11/16/acer-e11-es1-111-c3nt-linux/)

---

