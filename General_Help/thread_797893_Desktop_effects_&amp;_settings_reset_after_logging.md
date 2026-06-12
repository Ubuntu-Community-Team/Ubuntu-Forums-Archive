---
title: "Desktop effects &amp; settings reset after logging out"
date: 2008-05-17
forum: General Help
---

### Post by nohitter151 on 2008-05-17
Hi, new Ubuntu user here.  After much googling and guide-reading, I have been able to set up my compiz-fusion effects as well as my emerald theme just the way I want it.  The problem is that every time I log out, the settings are back to the default - emerald is not active (GTK is instead) and metacity is on instead of compiz as my window manager.  I can easily enable my compiz-fusion and emerald settings by running fusion-icon and right clicking "Reload window manager", but I would prefer that these settings loaded when I log in.

I have done a lot of searching on this as well, and the general advice is to add ```
compiz --replace
``` and ```
emerald --replace
``` to my startup programs under "Sessions preferences".  Unfortunately, my problem persists after trying this.

---

### Post by nohitter151 on 2008-05-19
Anyone?  Sorry to bump this, but I'd really like to get this set up the way I want it - and I just feel like I've tried everything.

---

### Post by Forlong on 2008-05-19
Install Simple-CCSM:
```
sudo apt-get install simple-ccsm
``` 
Then go to *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* and choose **Custom**.

If it works without an error, Compiz should be running next time you log in.

---

### Post by nohitter151 on 2008-05-19
Thank you for your help.  I ran the code suggested via the terminal and the custom section did appear under my visual effects settings.  When I logged out, custom was selected and the visual effects were working.  When I logged back in, the effects were off again.  I went to the visual effects tab again, and "None" was selected.  When I tried to switch to the "custom" setting, I got the message "Desktop effects could not be enabled".  I don't know why I get this message, everything seems to work fine when I "Reload window manager" via the Compiz Fusion icon.

---

### Post by Forlong on 2008-05-19
Try this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by nohitter151 on 2008-05-19
Thanks again!  I ran the script, here were the results (now I see why it wasn't working!):

```

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility 7000 IGP
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

Would you like to know more? (Y/n) y

 It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze, this particular combination had to be
 blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is
 safe to skip the blacklist. 

Do you want to skip blacklist checks by Compiz? (y/N) y
```

I'm going to log out now and see if disabling the blacklist check did it (it should :)).  Thanks so much for your help.

EDIT:  Its working.  Thanks so much for the help :D

---

