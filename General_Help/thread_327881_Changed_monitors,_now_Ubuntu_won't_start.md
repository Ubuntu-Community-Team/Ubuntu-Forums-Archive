---
title: "Changed monitors, now Ubuntu won't start"
date: 2006-12-29
forum: General Help
---

### Post by lagreca on 2006-12-29
I installed Ubuntu and got everything working to my liking.  I then took the computer to the garage, and plugged it into a different monitor than the one I installed with.  Now it won't boot.  

I tried:  
```
sudo dpkg-reconfigure xserver-xorg
```
but didn't know a lot of the answers and wasn't able to get x windows working again.  ](*,) There must be an easier way to reconfigure Ubuntu for a new monitor, because it configures itself just fine when installing.  Does anyone have an idea on how to get my installation working again?  Thanks.

---

### Post by taurus on 2006-12-29
If you don't know an answer, just hit the return for the default value.  Otherwise, try boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by dcstar on 2006-12-30
> **lagreca said:**
> I installed Ubuntu and got everything working to my liking.  I then took the computer to the garage, and plugged it into a different monitor than the one I installed with.  Now it won't boot.  

I tried:  
```
sudo dpkg-reconfigure xserver-xorg
```
but didn't know a lot of the answers and wasn't able to get x windows working again.  ](*,) There must be an easier way to reconfigure Ubuntu for a new monitor, because it configures itself just fine when installing.  Does anyone have an idea on how to get my installation working again?  Thanks.

First thing to do is plug the original monitor back in and see if it displays.

If it does, go into System-Preferences-Screen Resolution and set it to the lowest resolution and refresh rate available.

Now if you use the other monitor, you should at least see something displayed.

You can then try upping the resolution (first) and then the refresh rate a step at a time to see what works with that monitor.

---

### Post by lagreca on 2006-12-30
I was able to get it working with:
```
sudo dpkg-reconfigure xserver-xorg
```

My main problem was when it was asking how much RAM my video card had, I kept telling it 32, but it was asking for kb, not MB.  When I put 32000 in, it worked.  I also figured out the correct driver, and resolution, which helped.  

Thanks for all the pointers.

---

