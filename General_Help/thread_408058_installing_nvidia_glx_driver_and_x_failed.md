---
title: "installing nvidia glx driver and x failed"
date: 2007-04-12
forum: General Help
---

### Post by titan3169 on 2007-04-12
I'm in a jam right now. After i installed my nvidia drivers through the package manager I rebooted x and it failed. i got this message:

"(ww) Nvidia: no matching device section for instance (bus ID PCI 1:0:0) found
(ee) No Devices Detected

Fatal Server error:
no screens found"

If any one can help it would be greatly appreciated.
thx, 
jp

---

### Post by dcstar on 2007-04-12
> **titan3169 said:**
> I'm in a jam right now. After i installed my nvidia drivers through the package manager I rebooted x and it failed. i got this message:

"(ww) Nvidia: no matching device section for instance (bus ID PCI 1:0:0) found
(ee) No Devices Detected

Fatal Server error:
no screens found"

If any one can help it would be greatly appreciated.
thx, 
jp

There are a squillion posts on similar Nvidia problems, it may be best to do a forum search and pick out one with the detailed procedure for fixing this sort of issue.

---

### Post by rsambuca on 2007-04-12
Try installing the linux-restricted-modules... first.  You need to pick the right one for your kernel.

---

### Post by iamtheiconoclast on 2007-04-12
Greetings, friend.

I'm brand new to this stuff, and had exactly the same problem.  I installed and enabled nvidia-glx and suddenly, upon reboot, got exactly the message you're getting.  My configuration file had the wrong PCI bus id for my video card.  No idea why, but apparently I'm not the only person it's happened to, so you should check it out.

Here's what I did.  If I do something wrong, please forgive me; I'm still an idiot newbie ;)

1. Boot into recovery mode (I think you need to hit 'escape' as the boot loader is coming up).
2. Check/modify the contents of your xorg.conf file:

```
sudo pico /etc/X11/xorg.conf
```

3. Scroll down till you see device information including a BusID.  If you're like me (and 1 other guy I found on the forums here who tipped me off), yours will say PCI:0:5:0.
4. Change this to read PCI:1:0:0, save, and reboot.
5. Pray it works like it did for me.

---

### Post by cmat on 2007-04-13
I ran **sudo dpkg-reconfigure xserver-xorg** in command line, followed all the steps and got back my desktop upon a reboot. Changed my video driver to **vesa** until I was certain that the problem was fixed.

---

