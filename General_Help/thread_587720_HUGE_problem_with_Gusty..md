---
title: "HUGE problem with Gusty."
date: 2007-10-23
forum: General Help
---

### Post by tylerdustin2008 on 2007-10-23
I hooked up a regular lcd to my laptop, because it has a small screen. I had to log off and log back on. But i encountered something.... I would click on "Computer", "Pictures", "Quit" and etc. Nothing would happen. If i clicked on items in the menus like paint... they would open. So I forced the computer to shut down.  Started it back up, and I get nothing but this.

[http://s203.photobucket.com/albums/aa186/tylerdustin2008/?action=view&current=DSC01320.jpg](http://s203.photobucket.com/albums/aa186/tylerdustin2008/?action=view&current=DSC01320.jpg)

Help would be nice.

Thanks.

Tyler

---

### Post by tylerdustin2008 on 2007-10-23
Help....

---

### Post by seldenthuis on 2007-10-23
Does booting from the LiveCD work?

---

### Post by Austin_KW on 2007-10-23
try rebooting in recovery mode and typing

```
dpkg-reconfigure -phigh xserver-xorg
```

then type; to boot into multiuser
```
telinit 2
```

---

### Post by tylerdustin2008 on 2007-10-23
THANKS!

That fixed it.

Also i have one more problem, I have a really slow boot. It is on a black screen for about 2 mins, then the log in screen pops up.

Tyler

---

### Post by Austin_KW on 2007-10-23
> **tylerdustin2008 said:**
> THANKS!

That fixed it.

Also i have one more problem, I have a really slow boot. It is on a black screen for about 2 mins, then the log in screen pops up.

Tyler
There is a couple of things you can do to see what is causing the delays on boot.

1) At the grub menu use the 'e' key to edit the boot line; remove the "quiet splash" from the end of the line. You can then watch the boot messages scroll by and sometimes see where the delay is.

2) Or you can install bootchart. "sudo apt-get install bootchart" from the command line. This will produce an easy to read graphic of the boot sequence in the directory /var/log/bootchart/ Looking at the bootchart, (or posting it in the forums), it is often obvious where the problem is.

---

### Post by tylerdustin2008 on 2007-10-23
Here is the exact picture that was int hat folder. I have NO clue why it is so big??

But there ya go, hope it helps you to help me.

Tyler

---

### Post by Austin_KW on 2007-10-23
Some v. high cpu usage in usplash; Mine has no 'blue' after 5 seconds;

You could disable splash in /boot/grub/menu.lst, Just remove the word splash from the lines "kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=xxxxxxx ro splash"

But first; check the file /etc/usplash.conf; Is the resolution still set for the larger monitor?

---

### Post by tylerdustin2008 on 2007-10-23
I have un hooked the bigger monitor. I will try what you say in just a min.

---

### Post by tylerdustin2008 on 2007-10-23
It says I do not have permission to edit/save menu.lst.

And the other one says this.

# Usplash configuration file
xres=1280
yres=1024

My laptop lcd res is... 1024x768 though.

---

### Post by Austin_KW on 2007-10-23
Try gksudo gedit, eg
```
gksudo gedit /etc/usplash.conf 
``` and change to
# Usplash configuration file
xres=1024
yres=768

---

