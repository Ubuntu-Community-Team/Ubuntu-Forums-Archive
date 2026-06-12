---
title: "Kubuntu graphical error"
date: 2007-09-26
forum: General Help
---

### Post by tera4d on 2007-09-26
Well i installed kubuntu 7.04 but i also installed compiz-fusion.
But it doesnt seem to work.
These are my system specs (laptop btw)
Intel gma 950 (244 mb) < 3d card
1 gig ram 
Intel celeron m 440.

I get this error:

tera4d@MainFrame:~$ compiz --replace
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Can some body please help me out?

---

### Post by dabl on 2007-09-26
Which driver for your GMA950 did you install?  I would try the xserver-xorg-video-intel package first -- I think it is most likely to run your display correctly.

Basically, the sequence is (a) install Kubuntu, (b) install a graphics driver and make sure it works (like run glxgears and observe the graphic running and the fps figures that are computed), then if that is all working, go for (c) compiz, including the emerald window decorator.  Actually, on my rig, Beryl + emerald is more stable on Feisty than compiz.

The last part of the message that you got, beginning with "X Error: BadDevice, invalid or uninitialized input device 169" is unrelated to any graphics issues -- this is xorg.conf complaining that there are wacom devices defined, but no wacom devices found on your system. You can ignore that stuff, or search the forums and comment out the offending lines in xorg.conf if you want to, but they won't hurt anything.

:)

---

### Post by tera4d on 2007-09-27
Thank you for your replyu =)
I didnt had to install any drivers with UBUNTU but i have to with KUBUNTU?
i tought they were based from the same system but only with different desktops :P
But i installed them now and everything works.
And yes there is an problem ^^
Every effect runs fine except for the 3dcube effect?
It lags extremely much.
And i didnt had that with ubuntu.
But also i manually start compiz with this command in the terminal : compiz --replace
If i leave the console open everything is fine all effects work etc.
But if i close the terminal the skin from the windows disappear?
Can someone help me with these problems please?
Thanks for reading.

---

### Post by dabl on 2007-09-27
> **tera4d said:**
> Thank you for your replyu =)

i tought they were based from the same system but only with different desktops :P



They are the same Linux OS, but K_DM_ and G_DM_ are not the same, and your issue is all about graphics display, which is based on the _D_isplay _M_anager, so you can expect some differences in this area.

> 
And yes there is an problem ^^
Every effect runs fine except for the 3dcube effect?
It lags extremely much.
And i didnt had that with ubuntu.
But also i manually start compiz with this command in the terminal : compiz --replace
If i leave the console open everything is fine all effects work etc.
But if i close the terminal the skin from the windows disappear?
Can someone help me with these problems please?
Thanks for reading.

I had the exact same problem when attempting to get compiz working in Kubuntu Gutsy.  All I can advise is to look through the compiz packages listed in your Adept Manager -- did you get compiz-kde and emerald, along with the basic package?  Compiz-fusion is pretty "developmental" still, and not the most stable software out there, so don't expect it to perform perfectly without some twitching and tweaking.  

You should have also gotten a new KMenu item named "Settings", which appears above my "System" menu on my Gutsy system.  When you open that item, there should be a "Advanced Desktop Effects Manager" icon -- open that and make sure you have checked "Desktop Cube", "Rotate Cube", "Wobbly Windows" and/or whatever else you want.  :)

---

