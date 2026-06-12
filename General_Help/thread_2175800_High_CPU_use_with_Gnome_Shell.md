---
title: "High CPU use with Gnome Shell"
date: 2013-09-21
forum: General Help
---

### Post by mvjt-dobson on 2013-09-21
I am having excessive CPU usage with Gnome Shell and I am wondering if this has to do with Gnome Shell using the CPU rather than the GPU for accelerated graphics? I have disabled all extensions and still have crazy CPU usage.

I have tried installing propertiery drivers and all that happens is that it boots into fallback mode with the screen a third of the size than it should be, AMD Catalyst center wasn't giving me any options to increase screen size and there is no compositing. I have removed all propertiery drivers and gone back to the open source drivers in the meantime.


I am using Ubuntu Gnome Edition 13.04, my graphics car is an AMD HD5570.  Can someone please give some direction or help?

---

### Post by mvjt-dobson on 2013-09-21
This error just popped up:

> Your system is providing 3D via software rendering rather than hardware rendering.  This is a compatibility mode which should display 3D graphics properly but the performance may be very poor.  If the problem you're reporting is related to graphics performance, your real question may be why X didn't use hardware acceleration for your system.

---

### Post by su:bhatta on 2013-09-21
Have you seen the output of 

```
top
```

See if  there is any application that is using up CPU.


Please read this page about Fglrx settings : [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Maybe 13.1 Drivers would suit that chipset of yours.

Also, you can refer to amdcccle pages like [http://packages.ubuntu.com/search?keywords=fglrx-amdcccle](http://packages.ubuntu.com/search?keywords=fglrx-amdcccle) and see if you get a correct driver.

Best of luck .

---

