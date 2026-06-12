---
title: "Check for unused libraries/dependencies?"
date: 2007-05-17
forum: General Help
---

### Post by EtanSivad on 2007-05-17
When I use the Synaptics package manager it goes through and automatically scans for missing libraries and dependencies.  Is there a way to do the opposite? 

I uninstalled a couple of programs I won't be using in the near future (g++, gcc) but I noticed that during the removal it doesn't uninstall nearly as many libraries as when I installed it.  

So is there a way to scan for extraneous libraries? :confused:

Thanks,

-Etan

---

### Post by zvacet on 2007-05-17
Inatall deborphan package and i think it will give you what you want.

---

### Post by total wormage on 2007-05-17
indeed you can check for unused libraries with deborphan, but use common sense when removing libraries, deborphan doesn't always get it right ;]]

---

### Post by EtanSivad on 2007-05-17
Thanks for the response.  

It's probably a bit silly to worry about extraneous libraries, but I'm running ubuntu on a 5gb usb drive and it runs out of hd space FAST.

---

### Post by EtanSivad on 2007-05-17
Whoa.  Boy you weren't kidding about it finding false positives.  It flagged a whole bunch of the ALSA drivers as "orphans."  But it did help me find the random compile libraries I wanted to get rid of.  Thank you!

---

