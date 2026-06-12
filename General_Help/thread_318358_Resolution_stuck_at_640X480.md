---
title: "Resolution stuck at 640X480?"
date: 2006-12-13
forum: General Help
---

### Post by RobotChild on 2006-12-13
After picking up a spare 30gb drive for cheap-as-free, I decided to install Ubuntu.

After it loads up everything is 640X480 res., and I cannot change it.

I know it is possible in the terminal. but I cannot remember what I was supposed to type.
(I've not been using Linux steadily for a year or so)

Thanks,

-Darcy

Edit -

Hardware:
Athlon Xp 2600+
1024mb Hynix DDR400 RAM
XFX GeForce 6800
Antec TruePower 480W

---

### Post by hikaricore on 2006-12-13
```
sudo dpkg-reconfigure xserver-xorg
```

That should do the trick :)

Once you've gone through and configured your Xserver use ctrl+alt+backspace.  To restart X or logging out and logging back in/rebooting should work.

Note: If you are ever doing this on a live CD you obviously won't want to logout or restart so ctrl+alt+backspace will do the trick. (assuming you've properly configured X)

---

### Post by hikaricore on 2006-12-13
ps.  Make sure you look around for info on how to install the Nvidia drivers for your card if it's supported.  (I'm not a nvidia expert hehe)

---

