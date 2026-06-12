---
title: "gnome-terminal &amp; x-terminal-emulator not running"
date: 2007-06-26
forum: General Help
---

### Post by letkemanp on 2007-06-26
Everytime I try running gnome-terminal or x-terminal-emulator I get a message in the taskbar for a few moments saying "Starting terminal" and then it disappears. This just starting happening today, yesterday it was fine. The differance between yesterday and today is that now my system is setup with Samba to connect to a Windows 2003 ADS and I'm using Xinerama with my system to get the laptop screen and another screen working.

I've done a reinstall of both programs using Synaptic, but that did not help.

I've tried with I was logged in as a Windows 2003 ADS user and still have the same problems.

I've rebooted a few times and this still happens. Could the applications be starting at an invalid X Y postition? If so how can I fix this. 

Are they any logs that I should look at that would help me fix this?

---

### Post by dfreer on 2007-06-26
Did you set up xinerama using nvidia-settings? I experienced a similiar problem with the terminals not showing when using tv-out, it was fixed by restoring my backup of /etc/X11/xorg.conf and restarting x (or rebooting, either way). see if that is the case, if it is at least you'll know what is causing it.

---

### Post by letkemanp on 2007-06-26
Yep, when I went back to the xorg without xinerama  they two programs ran fine. Is this a know bug? Do you know of any solutions/work arounds?

---

### Post by letkemanp on 2007-06-26
I guess this is a know bug and here is the work around that i found

Section "Extensions"
	Option "Composite" "false"
EndSection

This is listed in the following places:
[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)
[http://ubuntuforums.org/showthread.php?t=285512&highlight=gnome-terminal+Xinerama](http://ubuntuforums.org/showthread.php?t=285512&highlight=gnome-terminal+Xinerama)
[http://ubuntuforums.org/showthread.php?t=385295&highlight=gnome-terminal+Xinerama](http://ubuntuforums.org/showthread.php?t=385295&highlight=gnome-terminal+Xinerama)
[http://ubuntuforums.org/showthread.php?t=445317&highlight=gnome-terminal+Xinerama](http://ubuntuforums.org/showthread.php?t=445317&highlight=gnome-terminal+Xinerama)

And probably more.

Thanks for your help

---

### Post by dfreer on 2007-06-26
Thanks to you! I didn't realize there was a solution for this! lawl... i need to use google more often.

---

