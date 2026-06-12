---
title: "A long problem..."
date: 2008-01-13
forum: General Help
---

### Post by hacexe on 2008-01-13
Hey all, It seems that I'm having the worst time imaginable with Gutsy Gibbon. It all started with the LiveCD.I couldnt even boot into the livecd desktop for 2 days untill i unplugged one of my monitors. That fixed it, and i installed Gutsy. So I go into Grub and attempt to boot Gutsy. Black Screen. I try millions of things, dunno which fixed it but i configured Xorg mostly and changed the usplash resolution. And then I managed to boot the first time by hitting CTRL ALT f1 or F2 i believe,it booted into a low graphics ubuntu thingy.. After I rebooted it had an option to configure or run the weird low graphics Ubuntu (Super EWWW) so I configured it I believe to a random dell monitor (I have a 19" Flatpanel WideScreen brand new 2 weeks old along with this computer) and it still booted crappily. So I tried a million options and it finally came out normally, and for once in my life wireless worked. All seemed perfect until I noticed desktop effects weren't working. Thats when I got angry. So I went to unable it and it said Can't enable.So I was like RAWR. So then I hear that theres a ati restricted driver thing, so i check my restricted driver manager, and the drivers not there. Only thing that comes up is my broadcom. So I start messing about with Xorg.conf some post said to change the whitelist thing. I had Compiz manager or something installed to. So I tried changing my driver and resolution fifteen million times with the screen and driver thingy in ubuntu, always just ends up with the screens screwed up and stuck at vesa driver every time i do CTRLALTBKSPACe. So I decided to do the xorg config thing from terminal again (except not in recover this time) and when I boot back. WHAM Low Graphics ubuntu, and that is where I stand today. Back at step 2.

Forgot to include my comp Specs.
Dell 19 inch widescreen Flatpanel
XPS 420
3Gigs of Ram
Quadcore Intel (2.4 or 2.6 ghz i forgot)
Ati RADEON HD PRO 2400

Please HELP?

---

### Post by SOULRiDER on 2008-01-13
Im guessing you should reinstall your graphics driver and reconfigure xorg.
Check out [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) there you will find how to install the drivers. After youre done, reconfigure xorg
```
sudo dpkg-reconfigure xserver-xorg
```

Good luck!

---

### Post by hacexe on 2008-01-13
Restricted Driver Manager dosen't even recognize my card. It dosen't think that theres a Restricted Driver to install for it. And I reconfigured Xorg about the 10th time now. Nothin is changin.

---

### Post by Nexusx6 on 2008-01-13
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Try the instructions there and let us know how it works out.

---

