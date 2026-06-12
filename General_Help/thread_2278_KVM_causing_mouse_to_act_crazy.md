---
title: "KVM causing mouse to act crazy?"
date: 2004-10-26
forum: General Help
---

### Post by wes480 on 2004-10-26
I just finished the install, everything went perfectly...

However, when I got into Gnome the mouse was acting crazy. I would move it an inch, and it would randomly jump all around the screen...while apparently clicking on its way (programs opening all over the place).

It is a microsoft optical mouse, usb but using a ps/2 adapter.

The thing is, I use a KVM between this box and a Windows machine.

I plugged the mouse directly into the box after it was acting so weird - and it worked perfectly. When plugged back into the KVM, it goes crazy.

In the past, I have used Gentoo/Gnome/Fluxbox and never had any problem with the mouse working in this setup - so either there is some different driver I need for using it with the KVM (though I never had to jump through any hoops with other distros)...or maybe it is some weird Gnome 2.8 glitch?

Really out of ideas..

---

### Post by wes480 on 2004-10-26
I saw in another post that it may have something to do with the 2.6 kernel - but no real explanations of what process to take to possibly fix it?

Worst case scenario I can just use two mice until it gets sorted out - the K and V switch fine.

---

### Post by disturbed1 on 2004-10-26
[QUOTE=wes480]I saw in another post that it may have something to do with the 2.6 kernel - but no real explanations of what process to take to possibly fix it?

Worst case scenario I can just use two mice until it gets sorted out - the K and V switch fine.[/QUOTE]

I use 2 generic KVMs with a PS/2 Keyboard and PS/2 (not usb adapter) mouse with out any issues. 

The first KVM switches between Windows 2k, and Ubuntu, the other KVM switches between Vector Linux (2.6.8 kernel) and Slackware (2.6.8 kernel).

I did have this issue once with Slackware (2.4.x kernel) but it was an improper xfreeconfig for my mouse. Experienced the same issues as you. Booting into Slackware was fine, but once I switched to Vector, then back to Slack, mouse was screwed. Moving it would cause windows to open/close, and all kinds of wierd stuff. I justed edited my config file to represent the correct mouse settings.

---

### Post by wes480 on 2004-10-27
the weird thing is that if I plug into the computer directly, bypassing the KVM - it is fine. Which makes me think changing the config wouldn't help...

---

### Post by /error on 2004-10-31
same problem here
usb mouse over an ps2 adapter connectec to a switch
and the mouse is acting crazy.

since i'm a linux starter its kind of hard to track the problem down :/

---

### Post by jmcgurk on 2004-10-31
I think this is something with Ubuntu specifically.  I've got a normal Debian install sitting right next to this install.  It is functioning fine witht the same config and hardware.  I also installed Ubuntu over a Suse install which was working fine with the same hardware, (and config I think).

This is a AMD64 install with a Asus MB.  On the upside the install autodetected all of the other hardware. (Video, sound, USB, network.)  So for the moment I have a normal mouse plugged directly into the machine.  Until I can work out a solution.

JM

---

