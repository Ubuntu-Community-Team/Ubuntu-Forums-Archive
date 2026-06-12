---
title: "Ubuntu boot problem blinking cursor"
date: 2024-04-30
forum: General Help
---

### Post by jerekn on 2024-04-30
I have the following problem during the boot of the Ubuntu: sometimes (not always) Ubuntu does not boot but instead blinking cursor/underscore is shown after grub. How to resolve this. For somehow it is confusing that this not happening all the time. I have laptop that has Ubuntu 20.04.6 LTS, GNOME Version 3.36.8, Windowing system x11, kernel version 5.15.0-105-generic. I hope that someone can help me with this since I am not that professional with Linux yet. Based on this post: [https://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot](https://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot) I am able to use ctrl+alt+del to resume.

---

### Post by Rubi1200 on 2024-04-30
Have you tried switching to Wayland instead of X11? Does that make a difference? Have you tried booting an older kernel and does that help?

What graphics card do you have installed and how much RAM?

---

### Post by jerekn on 2024-04-30
Actually now when I look etc/gdm3/custom.config wayland should be in use I think?
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.


[daemon]
# Uncomment the line below to force the login screen to use Xorg
#WaylandEnable=false


# Enabling automatic login
#  AutomaticLoginEnable = true
#  AutomaticLogin = user1


# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10


[security]


[xdmcp]


[chooser]


[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true

Moreover I have integrated intel graphics card as well nvidia GeForce RTX 3080. Based on nvidia-smi it should be off at the moment. I have 32GB of RAM. I have not yet tested newer kernel. Somehow this is very confusing since this started in last week and I have not updated anything in very long time. So in theory nothing should have changed.

---

### Post by Rubi1200 on 2024-04-30
An unusual problem.

Not in order, but perhaps try some/all of these steps:

1. check logs for error messages especially journalctl -b (check the manpages for usage parameters)
2. check your GRUB configuration and update if needs be
3. run a check on the hard drive for errors, perhaps something is failing?
4. check BIOS/UEFI settings, maybe something changed like you need to disable fast startup or similar?

---

