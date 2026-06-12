---
title: "New 8.42 ATI driver killed my Gutsy, Won't log in."
date: 2007-10-23
forum: General Help
---

### Post by Toadmund on 2007-10-23
Went to test my new install by going into the game 'nexius'
It was a bit choppy, so I selected a lower resolution in the game, then it crashed, and reverted me back to the open source driver.
So then I tried to re-install the ATI driver, would not install, so I went into restricted driver manager, and unselected the restricted driver, re-booted like it asked.
I wanted to re-enable it when I booted back up.

But, I put in my log on info, then it crashes right back to the log-on screen again.

Is their not some command I can put into the recovery mode, like reconfigure 'X' or re-enable the driver or something?

Thanks.

My Gutsy is busted :frown:

---

### Post by Maestro23 on 2007-10-23
> sudo dpkg-reconfigure xserver-xorg

Pick "vesa" and accept defaults elsewhere.  When you get back into Ubuntu, install whatever driver you want.

---

### Post by Toadmund on 2007-10-23
It worked, BUT my screen is all messed up, when I hit 'ctrl-alt-back' for a brief moment I see a nice clear 1 quarter size screen desktop.
Seems my problems arise from this size issue.

Also the ubuntu intro is quadrupled and in b&w.

Do I have to do a re-install just to keep things from getting too insane here?

---

### Post by Maestro23 on 2007-10-23
> **Toadmund said:**
> It worked, BUT my screen is all messed up, when I hit 'ctrl-alt-back' for a brief moment I see a nice clear 1 quarter size screen desktop.
Seems my problems arise from this size issue.

Also the ubuntu intro is quadrupled and in b&w.

Do I have to do a re-install just to keep things from getting too insane here?

When you reconfigured, did you input any desired resolutions?

---

### Post by Toadmund on 2007-10-23
1024 x 768

The screen is messed up in a slanty repetitive fashion.

---

### Post by imfrompa on 2007-10-29
I have the same problem as OP.  Luckily, I have two HDDs in this PC and have kubuntu running on the other one.  This is my work computer and me and my co-worker both upgraded and both had different problems with identical machines.  ATI drivers were his problem too, but could not get to the login screen.  He did a fresh install to fix his issues.  I will try the reconf xorg command to see if that helps.  Thanks for the tips guys.  I'll report back in a few.

---

