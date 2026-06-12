---
title: "GeForce 9800 GX2 on 8.04"
date: 2008-04-25
forum: General Help
---

### Post by dyr on 2008-04-25
Hi guys,

Yesterday I installed the drivers off the nvidia site because the included drivers ( most likely generic ) would only use resolutions as large as 800x600, the drivers installed succesfully and everything was fine. Compiz, cube spinnyness, 1920x1200, everything.

However upon restarting, X launches and asks to run in safe graphics mode with an 800 x 600 resolution again, it seems that something is resetting the x config file, which is configured automatically by nvidia-xconfig.

Anyone have any ideas how to resolve this?

Cheers,
Dayle.

---

### Post by dcstar on 2008-04-25
> **dyr said:**
> Hi guys,

Yesterday I installed the drivers off the nvidia site because the included drivers ( most likely generic ) would only use resolutions as large as 800x600, the drivers installed succesfully and everything was fine. Compiz, cube spinnyness, 1920x1200, everything.

However upon restarting, X launches and asks to run in safe graphics mode with an 800 x 600 resolution again, it seems that something is resetting the x config file, which is configured automatically by nvidia-xconfig.

Anyone have any ideas how to resolve this?

Cheers,
Dayle.

Try the **envy** package (do a search).

---

### Post by dyr on 2008-04-25
Thanks, did not know about that one, thats perfect!

---

### Post by batjew_beyond on 2008-08-06
OK, I'm also trying 8.04 with a GeForce 9800 GX2 card.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150284](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150284)
There's the specific card just in case.
I have tried everything short of ritual sacrifice.  EnvyNG, The NVidia Official Drivers, even the Nvidia-glx-new drivers from the Multiverse.  Simply put, this does not work.  I'm at my second fresh instal here, and every time I attempt to get it running, I restart after attempting to install the drivers and update X, and as soon as X tries to start, the screen flashes black maybe once or twice, then nothing.  Normally restarting in restore mode and fixing xserver works, but then I am left with no advanced graphic features.
Any help greatly appreciated.  Thanks everyone.

My next step if no one here has an answer is to try an install of Gutsy and see how that works.  That and I've been thinking of looking into some other distros.

---

### Post by nbayiha on 2008-08-06
[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

---

