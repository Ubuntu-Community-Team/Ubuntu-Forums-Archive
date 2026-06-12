---
title: "Keyboard, Mouse don't work after power outage"
date: 2022-07-06
forum: General Help
---

### Post by criageek on 2022-07-06
We had some pretty good storms roll through here last night and I lost power for about 15 minutes.  My primary computer runs all the time because it gets backed up every night.  When I started it up this morning the keyboard and mouse do not work.  It boots up to the login screen but I can't do anything with either the keyboard or mouse.  The keyboard does work on the grub screen, and I can boot into a live usb running Ubuntu 21.04 and the keyboard and mouse work fine.

What can I do??

Thanks,
Rich

---

### Post by criageek on 2022-07-06
I think I have this solved...here is what I did in case it can help someone else.

I found a couple of instances where running this command fixed this problem.

sudo apt install xserver--xorg-input-all

So I booted into recovery mode, enabled networking, and dropped to a root shell.  But every time I tried to do anything with apt I got a bunch of "Temporary failure resolving"... errors for each repository.  I solved that by editing /etc/resolv.conf and adding this line:

nameserver 192.168.1.1

I know this file is generated and that line will go away, but it got me to the point that I could install xserver--xorg-input-all and now all is good!

Rich

---

