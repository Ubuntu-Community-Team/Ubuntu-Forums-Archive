---
title: "Gutsy recognizes integrated graphics instead of newer card.."
date: 2008-02-20
forum: General Help
---

### Post by k1dicarus on 2008-02-20
Hello Everyone,

I'm having an issue with a desktop. I cannot enable Desktop Effects. This is an older machine with nForce integrated graphics. A while back, I put a GeForce FX5500 250MB video card into this box. I have changed the preferred graphics in the BIOS and messed with the drivers in Gutsy, but I still get 'Desktop Effects could not be enabled". Is this a common issue? Does anyone have any advice?

Thank you!

---

### Post by blueturtl on 2008-02-20
I had this issue with my system and unfortunately the onboard video has to be disabled *before* setting up Ubuntu. Having Ubuntu setup and detect video during installation is the safest way to go.

Backup your xorg.conf by typing
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

and then disable the restricted drivers. After rebooting do a
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Word of warning though, be prepared to work in command line mode if something goes awry.

---

### Post by rovernaut on 2008-02-20
> **k1dicarus said:**
> Hello Everyone,

I'm having an issue with a desktop. I cannot enable Desktop Effects. This is an older machine with nForce integrated graphics. A while back, I put a GeForce FX5500 250MB video card into this box. I have changed the preferred graphics in the BIOS and messed with the drivers in Gutsy, but I still get 'Desktop Effects could not be enabled". Is this a common issue? Does anyone have any advice?

Thank you!

I have the same issues. Yet on Kubuntu.
 I am frustrated after fitting the FX5500 AGP card.
In display properties it recognizes the card as Fx4000.
 I installed the installed the latest driver, used Envy also, reinstalled uninstalled, bashed my head against the wall, contiplated suicide etc etc, but I can't get it to work properly.
 It showed up as a Fx5500 in the Nvidia config tool. but crashes all the time.
I did a google on FX 5500 and it oped up a hornet's next of posts re this graphic card and it's problem s, but no real solution, so will watch this post with interest.
 good luck to you.

---

### Post by julian67 on 2008-02-20
> **k1dicarus said:**
> Hello Everyone,

I'm having an issue with a desktop. I cannot enable Desktop Effects. This is an older machine with nForce integrated graphics. A while back, I put a GeForce FX5500 250MB video card into this box. I have changed the preferred graphics in the BIOS and messed with the drivers in Gutsy, but I still get 'Desktop Effects could not be enabled". Is this a common issue? Does anyone have any advice?

Thank you!

have a look at this thread: [On-board Graphics Install Issue]("http://ubuntuforums.org/showthread.php?t=570098")

---

### Post by k1dicarus on 2008-02-20
Okay, I'm going to try these suggestions when I get off work later tonight. I'll be back for a status update ..hehe.

---

### Post by k1dicarus on 2008-02-23
How would I find out which driver is being used for the nforce so I can blacklist it?

---

