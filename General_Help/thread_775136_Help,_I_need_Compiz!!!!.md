---
title: "Help, I need Compiz!!!!"
date: 2008-04-29
forum: General Help
---

### Post by jmemm37 on 2008-04-29
I have a Toshiba A105-2001 laptop. Hardy Heron is running like a champ within Windows. Can anyone help me with setting up Compiz on my system? I tried adjusting the settings within desktop adjustments and it says that I can't run extended settings. I know this to not be true because I am running the dreaded WinVista with Aero and I do have the 3D effects working within Windows. I would like to get Compiz working. The more I can do in Hardy, the less tempted I will be to hang in WinVista. Thanks!](*,)

---

### Post by damis648 on 2008-04-29
What video card do you have? And did you install the restricted driver for it? If you did not, goto in the panel System>Administration>Hardware Drivers and check the enable box on your video card.

EDIT: do you have the Intel X3100 card? this one is blacklisted by compiz, you can use it but you have to do some tweaking.

---

### Post by Rocket2DMn on 2008-04-30
Please post the output of 
```
lspci | grep VGA
```
If you have an older ati card, like a 9500 or older, you will need to enable compiz with this workaround: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by russo.mic on 2008-04-30
> **jmemm37 said:**
> I have a Toshiba A105-2001 laptop. Hardy Heron is running like a champ within Windows. Can anyone help me with setting up Compiz on my system? I tried adjusting the settings within desktop adjustments and it says that I can't run extended settings. I know this to not be true because I am running the dreaded WinVista with Aero and I do have the 3D effects working within Windows. I would like to get Compiz working. The more I can do in Hardy, the less tempted I will be to hang in WinVista. Thanks!](*,)

Within windows?  Under a VM?  You can't (as far as I know) get 3d accel running under a VM.  

I'm not sure about wubi, as I haven't gotten around to playing with it, but I don't think it would work there either.

Install native,  

Russo

---

### Post by fhmanas on 2008-04-30
try reconfiguring XORG, in a terminal type 'sudo dpkg-reconfigure xserver-xorg', choose primarily the default until you reach a choose of Simple, Moderate, Advance.  Although, Advance is the default choose simple.  You can also set here the screen resolutions if you are using Gutsy.

---

### Post by Rocket2DMn on 2008-04-30
> **russo.mic said:**
> Within windows?  Under a VM?  You can't (as far as I know) get 3d accel running under a VM.  

I'm not sure about wubi, as I haven't gotten around to playing with it, but I don't think it would work there either.

Install native,  

Russo

That normally would have been my advice, but starting with 8.04, Wubi is an officially supported method of install.

> **fhmanas said:**
> try reconfiguring XORG, in a terminal type 'sudo dpkg-reconfigure xserver-xorg', choose primarily the default until you reach a choose of Simple, Moderate, Advance.  Although, Advance is the default choose simple.  You can also set here the screen resolutions if you are using Gutsy.

I'm not sure if you have tried this with Hardy, but the new version of X does not reconfigure very well - it relies much less on xorg.conf and more on autodetection (xorg.conf is becoming deprecated).  Now when you reconfigure it doesn't ask anything about your video stuff - no driver, no resolutions, no monitor questions.  This has been causing a lot of problems for people whose video cards are not autodetected very well.

---

### Post by jmemm37 on 2008-04-30
Thank you all for the replies and advice. I installed the restricted driver for my ATI card and it seems to be working.:)

---

