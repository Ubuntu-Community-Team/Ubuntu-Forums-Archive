---
title: "ubuntu slow, not sure why"
date: 2007-08-06
forum: General Help
---

### Post by c.wilson on 2007-08-06
I just switched from windows xp to ubuntu and took a dramatic decrese in overall speed in which the system operates. Not sure why, curious if I am missing something.

My information is as follows:

> Computer Processor	2x AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
Memory	969MB (403MB used)
Operating System	Ubuntu 7.04  32bit
Display Resolution	1280x1024 pixels
OpenGL Renderer	GeForce 6150 LE/PCI/SSE2/3DNOW!
X11 Vendor	The X.Org Foundation
Multimedia Audio Adapter	HDA-Intel - HDA NVidia
Version Kernel	Linux 2.6.20-16-generic (i686)
Compiled	#2 SMP Thu Jun 7 20:19:32 UTC 2007
C Library	GNU C Library version 2.5 (stable)
Distribution	Ubuntu 7.04
SWAP 2.1GB

Thanks for any help, I REALLY don't want to go back to XP =(

---

### Post by SeanHodges on 2007-08-06
I have a very similar system, and haven't had the slow performance problem like what you have described. It is possible that some hardware module is playing up and causing the system to run slowly. Are you able to narrow down what actions you find particularly slow? e.g. Opening the Web browser, or playing a video...

Can you type

```
dmesg
```

and then

```
less /var/log/Xorg.0.log
```

into a terminal window (Applications->Accessories->Terminal) and attach the output of both commands here?

Also, could you specify if you are using a wireless network card (and which make/model if so) because I have seen a friend's computer perform slowly due to a bad wireless configuration.

---

### Post by c.wilson on 2007-08-06
Thanks for responding!

no wireless internet card, I'm hard wired with this machine.

attachesd is the result of the two commands..

---

### Post by SeanHodges on 2007-08-06
I'll take a look at the logs tomorrow, as it's pretty late here.

I'll post up something if someone hasn't already solved your problem

cheers

---

### Post by c.wilson on 2007-08-06
Thanks man,

---

### Post by SeanHodges on 2007-08-09
Sorry for the late reply, been busy with work.

I can't see anything obviously wrong with your setup. I only got the first page of the Xorg.0.log, due to my bad instructions on getting hold of the contents, but the other log looks OK.

It looks like you have an NVidia driver, are you using the restricted driver for it? (you can find this out in the System->Administration->Restricted Drivers Manager utility) Basically the Nvidia driver is not supported by Ubuntu, but can improve performance on the graphical-intensive programs/games. If you are using a 3D accelerated desktop like Beryl or Compiz-fusion then you are most likely using this driver.

If you are in fact using a 3D accelerated desktop then try turning it off to see if that improves performance.

Also it looks like you might be using NFS? I can't be sure on that, but if you are (you'll know that you are) then I recommend un-mounting those remote filesystems and seeing if the performance improves.

Does every action appear slow? logging in, opening a directory, playing a movie? To track down the cause we really need to narrow down what actions are triggering this.

---

