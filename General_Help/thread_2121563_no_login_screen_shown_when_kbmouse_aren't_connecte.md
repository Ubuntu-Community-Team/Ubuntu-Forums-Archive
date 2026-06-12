---
title: "no login screen shown when kb/mouse aren't connected"
date: 2013-03-02
forum: General Help
---

### Post by cdr74premium on 2013-03-02
Hi guys. I'm new here, but not exactly new to the Linux world. I used to run Slackware 10+ years ago, and, after a long Linux hiatus, decided to try Ubuntu. My Pentium 4 3.0GHz was a little slow running it, so I choose Xubuntu.

It's running fine, and I really like it. I'm thinking about replacing almost all of my Windows installations with it.

...but there's a problem. I have a KVM installed, and I use it to alternate my KB+M between this Pentium 4 machine and my other computer. Trouble is, if I try to boot Xubuntu without the KVM switch set to the machine I run Xubunu on, it displays the wallpaper, but nothing more. It doesn't hang, as I can access the terminal using CTRL+ALT+Fx, but I have to reboot and keep the KB+M attached to it if I want to get a login screen.

As I usually turn the machine on while I'm using the other, I wanted to know if there's a fix for that. I tried Googling, but all I found was issues with not having a monitor connected. That's not my problem: if I set the monitor to the Xubuntu machine, it behaves the same way. KB+M = login screen. No KB+M = no login screen.

Thanks everyone.

---

### Post by cwsnyder on 2013-03-02
Just a quick question to ponder:  If you have no keyboard or mouse, how are you going to log in?  Your input devices are detected as part of the boot process, and it is possible to boot headless in Linux (no screen, keyboard or mouse), but no input device connected means you are going to have to either reboot or SSH into the machine to log in, and the remote login process must be enabled.

---

