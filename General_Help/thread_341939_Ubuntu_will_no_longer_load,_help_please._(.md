---
title: "Ubuntu will no longer load, help please. :("
date: 2007-01-19
forum: General Help
---

### Post by c.jelly on 2007-01-19
Hey everyone, my first post on here as I normally just use the search to find what I want :mrgreen: 

I've been using Ubuntu flawlessly for about 2 months now, and I've just encountered my first major error. Basically, Ubuntu will no longer boot up.

I get some kind of UI (very basic, a bit like a BIOS screen), which says Ubuntu failed to load and asks if I want to see the XServer log or something.

Anyway, I click Yes, and it mentions something about nVidia. Now, I had installed the Nvidia drivers from a package someone on here posted a while back and it was working fine (I was seeing the Nvidia logo before the Ubuntu login screen), but I think it may have possible some how become corrupt and is preventing Ubuntu from loading altogether.

Does anyone have any ideas on how I could fix this, please? Perhaps some help on how I can revert to the default display driver or something?

I am completely new to Linux so please can I have suggestions as simple as possible, please.

I'm currently running the Live CD and haven't touched anything on the HD, so (in theory), everything should be as I left it, and I'm open to suggestions.

Thanks. :KS

---

### Post by der_joachim on 2007-01-19
You can do two things: edit your xorg.conf to use the open source nv driver. This will disable 3D acceleration, but at least you'll have a working desktop again. Second, I'd use the nvidia driver from the repos. Make sure that you have enabled all repositories (Universe, multiverse and restricted) and issue the following commands:
```
sudo aptitude purge nvidia-glx
sudo aptitude install nvidia-glx linux-restricted-modules-2.6.17-10-generic
```

This will install the standard nvidia drivers, after removing the corrupt ones. 

Disclaimer: I am assuming that you are using Edgy now. Furthermore, you may have to remove even more nvidia packages first. 

Good luck.

---

### Post by c.jelly on 2007-01-19
All of a sudden I seem even more confused... how do I even access my HD? :(

---

### Post by CroEragon on 2007-01-19
To issue upper orders boot Ubuntu in Recovery mode (you chose it in grub). Since you do not have GUI in it, it would be wise to write down commands.

---

### Post by c.jelly on 2007-01-20
Thanks for the replies, in the end I just got so confused that I just re-installed. :)

---

### Post by r4ik on 2007-01-20
Next time could just do a,

sudo dpkg-reconfigure xserver-xorg 

follow the defaults and start x again with

sudo /etc/init.d/gdm restart

Should work.

---

