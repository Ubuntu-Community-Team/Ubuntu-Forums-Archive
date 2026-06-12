---
title: "intel express graphics"
date: 2007-05-02
forum: General Help
---

### Post by celticbhoy on 2007-05-02
I have a small prob with my install which will seem very trivial, because it is.

My PC uses an integrated Intel Express 82945G graphics chip. On the Vista side of my dual boot it runs at 1280x800. On Feisty I can only get 1024x768. I know it is only a small difference, but it is bugging me, Everything else is working fine, all my other hardware works.

I have tried editing my xorg.conf to add the higher resolution. Doesn't work.
I have tried reconfiguring the whole xorg. Doesn't work.

Does anyone know the most up to date driver for this chipset. I am using the xorg i810 driver.

Once again I know it is a small prob compared to others, but it is eating away at me.

---

### Post by gerscht on 2007-05-02
I think you have to install 915resolution:
```
sudo apt-get install 915resolution
```

see: [http://ubuntuforums.org/showthread.php?p=2501666](http://ubuntuforums.org/showthread.php?p=2501666)

Gerscht

---

### Post by celticbhoy on 2007-05-11
gave it a shot didnt make any dif

---

### Post by ramjet_1953 on 2007-05-12
Try this, after un-installing 915resolution:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel
[/COLOR]

Re-boot and hopefully, all will be good, as it should automatically detect the optimum settings for your system.

Regards,
Roger 8)

---

### Post by celticbhoy on 2007-05-15
Cheers RamJet.

Worked a treat !!

---

