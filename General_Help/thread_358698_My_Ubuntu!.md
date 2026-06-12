---
title: "My Ubuntu!"
date: 2007-02-11
forum: General Help
---

### Post by Spotswood on 2007-02-11
Hello everyone,

Firstly, thank you to all for helping me with my system by posting 'howtos' and sharing your  fixes.

I've now got Ubuntu running very nice on P4 box although I do have a few tiny issues. The biggest issue is my ATi Radeon 9250, you all know that a lot of us have issues with these cards and I've read a lot of the threads that try to help people get their cards working correctly. None of these tips and tricks worked for me so I've decided to upgrade my card to an nVidia - but which one? Because I have an older mobo I have to buy an AGP card which does bump the price up, eventually I would like to get Beryl working but I'm not entirely sure which card to buy. I still have Windows installed for playing a few games (PES6) and would like a card that would work well for both of these needs. I don't know much about graphics cards and their chipsets but I have been looking at these two cards, an XFX GeForce 6800XT 256MB and a MSI 7600GS 512MB. Would these be ok? Any other suggestions?

Cheers,

Spotswood

PS I should have switched over sooner... :)

---

### Post by teaker1s on 2007-02-11
out of Nvidia and MSI I'd go with Nvidia

---

### Post by mgmiller on 2007-02-11
I currently have a gigabyte Geforce 6800 128 meg AGP in my edgy box that works well for me with UT2004.  I am in the process of upgrading to an xfx 7600GT 256 meg becasue I want to get a 22" wide screen monitor and the 6800 card does not suppoort the 1650x1050 resolution I need.  I looked at the 7600GS also and the extra memory is interesting, but it is of a slower type (GDDR2).  The GT version of the card uses GDDR3 memory and has other extra pipelines and stuff enabled.  The difference in price was very small from Newegg.com   All the reviews and benchmarks I saw showed the 256 meg 7600 GT is faster than the 512 meg 7600GS.  Bottom line, I don't think you will have any real problems with either of the nvidia based cards you are looking at.
Since you are changing from ATI to Nvidia, when you reboot, your "x" will most likely be broken.  Don't panic!  ](*,)

When it dumps you to the terminal type:
```
sudo dpkg-reconfigure xserver-xorg
```
Just hit enter for anything you are not sure of.  When it gets to the monitor section, if you have a flat panel, make sure you don't select any resolutions higher than your panel can support.

You can then try typing:
```
startx
```

If that doesn't work, a simple reboot should then bring you back up.

Once you are back on your desktop, you can load the accelerated drivers with automatix2 or easy ubuntu.

Good Luck.

---

