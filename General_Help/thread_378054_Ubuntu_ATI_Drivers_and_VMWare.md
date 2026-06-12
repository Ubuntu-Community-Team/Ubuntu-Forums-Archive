---
title: "Ubuntu ATI Drivers and VMWare"
date: 2007-03-06
forum: General Help
---

### Post by Wizzy on 2007-03-06
Ok - I had this problem with Ubuntu the last time I installed it, and I managed to fix it: 

[http://www.ubuntuforums.org/showthread.php?t=361720&highlight=wizzy](http://www.ubuntuforums.org/showthread.php?t=361720&highlight=wizzy)

was fixed by doing this:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)


That was on a separate drive. I tried it just now running Ubuntu through VMWare, and it doesn't work. It completely freezes when at the Ubuntu loading screen about 1/2 a bar away from loading the OS.

I'm wondering if anyone has any ideas

I've got an ATI x1800xt that I'm trying to get to work properly with this thing. *sigh* this is why I hate linux, it's so damn complicated at times. Why can't I just download a file and run it and have it automatically configure itself?

---

### Post by ubergeeknz on 2007-03-06
If you are running it in VMWare... you have to use standard video drivers (to suit the virtual hardware...) 

If you try to run the Ati drivers inside VMWare of course it is going to crash, it doesn't have direct access to your hardware...

---

### Post by AndyCooll on 2007-03-06
Got to agree with the above post. VMware ain't using your graphics card drivers, it's using VMwares own built in bog standard drivers.

:cool:

---

### Post by PilotJLR on 2007-03-06
> **Wizzy said:**
> *sigh* this is why I hate linux, it's so damn complicated at times. Why can't I just download a file and run it and have it automatically configure itself?

The funny thing here is that this has nothing whatsoever to do with Linux... you're overthinking the problem.

VMware presents a "vmware" SVGA adapter to guest OS's, like the other posters said. **You need to install VMware Tools!**
Nothing to do with the Linux host or guest; same deal on Windows.

---

