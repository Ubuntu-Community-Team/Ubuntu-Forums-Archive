---
title: "Nexuiz exiting when setting native resolution of monitor."
date: 2013-03-23
forum: General Help
---

### Post by stchman on 2013-03-23
I have the latest Nexuiz 252 and whenever I set the resolution to 1920x1200 the game exits and this is the error message I get.

```

VID_Restart: changing from fullscreen 1024x768x32bpp, to fullscreen 1920x1200x32bpp.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3c00002
  Serial number of failed request:  216
  Current serial number in output stream:  219

```

I have tried disabling Compiz, but that does not help.  My graphics card is a GeForce GTX 550 Ti.  I am running the Nvidia 304.64 drivers.

Thanks.

---

### Post by PhantomTurtle on 2013-03-26
This thread might be able to help with your problem. [http://forums.xonotic.org/printthread.php?tid=3313](http://forums.xonotic.org/printthread.php?tid=3313)  (2nd post)(I know it's for Xonotic, but the same instructions should apply for Nexuiz). I'm going to assume that the native resolution of your monitor is 1920x1200 (because if it wasn't  they we know what the problem is). Basically the post says to use SDL, instead of GLX. 

Hope that helps.

-Phantom

---

