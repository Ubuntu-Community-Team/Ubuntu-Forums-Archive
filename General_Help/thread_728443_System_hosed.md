---
title: "System hosed?"
date: 2008-03-18
forum: General Help
---

### Post by kender42 on 2008-03-18
I tried to use an external keyboard on my laptop and when I tried to reboot nothing happened. I removed the keyboard and tried to reboot but still nothing happened.

How can I fix this without losing everything I've done so far?

I have spent the last 2 months configuring my system and with no way to do a back up, since I am a COMPLETE linux beginner, I am lost.

When I reboot all I get is a black screen and some strange looking characters that seem to be stretched horizontally that I don't recognize nor could I describe

but look something like this:

[eeee^^feec^c[[[

---

### Post by ajmorris on 2008-03-18
hi there,
we are going to re-install your bootloader, grub.

First, boot into any linux live cd, then once logged in, mount your ubuntu partition, (you can find the /dev block device by sudo fdisk -l, then do sudo mkdir ubuntu then sudo mount /dev/[I]Block device from sudo fdisk -l)
[/I]
open up a terminal and type in the following commands:
```
1) sudo grub
```
```
2) find /boot/grub/stage1
```
```
3) root (hd#,#) *Where #,# are the numbers found in step 2)*
```
```
4) setup (hd0)
```
```
5) quit
```
```
6) reboot
```
then, eject the cd, and you should be able to boot back into your system

---

### Post by kender42 on 2008-03-18
Thank you, that worked for rebooting, now I get the error:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

So I entered yes and got:

/etc/gdm/failsafeXServer : line 47 : [ too many arguments
Warning:  Failsafe mode was already attempted in 30 seconds.
Warning: Falling back to gdm to report the issue.

Why would a usb keyboard hose my GUI
and how do I fix this?

---

### Post by ajmorris on 2008-03-19
the keyboard input driver that xorg was using may have changed for some odd reason when you plugged in the keyboard, i dont know why, but, when it comes up with that error, click through ok, or yes or whatever, then, when it goes back to the CLI do this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
follow the prompts, and enter in any data it asks, then try starting X again, you can either type startx to go into your default XSession (probably gnome) or type sudo gdm to start your Login Manager, and then login from there.

---

### Post by kender42 on 2008-03-19
Thank you so much. That did the trick. Also thank you for explaining the why a bit.

Also thank everyone who see this that I am greatly pleased that I can get help so fast unlike that "other" OS. This is my first attempt at any Linux based OS and I'm grateful for the help you've shown.

---

