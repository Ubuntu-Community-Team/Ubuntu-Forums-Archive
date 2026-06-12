---
title: "Monitor: &quot;out of range&quot;&quot;"
date: 2018-09-28
forum: General Help
---

### Post by hrsetrdr on 2018-09-28
I installed 18.04 with Mate on an old Intel D850GB  Pentium 4 socket 423.    All was well until rebooting to new install, getting "input not supported" message appearing on otherwise blank LCD monitor screen.      I've read that what is needed is to set a "nomodeset" parameter for the kernel, but the "out of range" message and otherwise blank screen appear immediately as Ubuntu is booting.

Options?

---

### Post by wildmanne39 on 2018-09-28
How to fix an out of range problem at boot
IF IT IS ONLY HAPPENING IN GRUB and you can boot into Ubuntu then please do this:
```
gksudo gedit /etc/default/grub
```
and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=640x480

Then save and exit.

Then do:
```
sudo update-grub
```

I had this issue a long time ago and my computer would boot if I left it alone for about 3 minutes.

---

### Post by hrsetrdr on 2018-09-28
Thing is, the system never gets to grub, as a matter of fact since Ubuntu is the only OS on the machine, I don't think grub even displays.    

Update:  OK, I read that if you press "shift" during boot grub will display.  Tried that, get a momentary "entering grub" in the upper left, then back to blank screen with "input not supported" dancing around.

Here's a video I took and uploaded to Youtube:   [https://youtu.be/YqwWqRYAO1g](https://youtu.be/YqwWqRYAO1g)

---

### Post by wildmanne39 on 2018-09-28
If you just let it set for 3 to 5 minutes and do not try to enter grub then does it boot? mine always did even though the screen was blank, once booted then you do what I posted, if it does not boot then hopefully someone else has a better idea.

---

### Post by hrsetrdr on 2018-09-28
I let the machine go for a half hour, the display issue did not resolve.     I did install Ubuntu server, a very nice system sans GUI.  I'll have to refresh my memory on which packages needed for a windowing system and desktop environment.   During the process I can set 'nomodeset' which I hope will be a solution.  

The video card is not a "powerhouse", a simple ATI display adapter from the early 2000s.   I had thought of picking up a more powerful video card off ebay, but that would be just clutching at straws, not a guaranteed solution derived from methodical troubleshooting.

---

### Post by hrsetrdr on 2018-09-29
I did install LXDE desktop environment, which cured the "input not supported"  issue.   System runs decently even-though it has only 512mb RAM.  I have 2 more sticks of 128mb RDRAM, but the system just won't boot with all for RIMMs installed.    ???   It used to just fine, when I first built the system, not sure what's changed.

---

