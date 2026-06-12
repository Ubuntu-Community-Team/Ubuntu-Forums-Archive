---
title: "Ubuntu 14.04 Brightness control does not work in Toshiba Laptop Satellite"
date: 2014-05-03
forum: General Help
---

### Post by lennart3 on 2014-05-03
Hello !

I am running Ubuntu 14.04 on a Toshiba Laptop Satellite A100 and it works great except from this issue:

Brightness (backlight) is too high and can not be set.

In the system settings menu/brightness:
If I set the slider to any point over zero position (black-screen) there is no change at all in brightness. What puzzles me is that if I set a screen locking time of 1 minute and wait, the screen brightness dims down completely - softly and nice after a minute. The same thing, (in reverse) after "waking up", so technically it would be possible to set a constant brightness of any value between min and max ? What specific programs/scripts are involved in
the process of brightness settings from the system menu ? Is something broken/ missing?

There are many suggestion for solutions on this problem in the forums and elsewhere, so it might be a common issue with laptops.

So far I have been testing to run xbacklight -set 50 (and other values)  with no success at all. Seems unlikely that xbacklight is useful for this Laptop....

I am not a software guy and have only rudimentary knowledge about programming
but I would gladly receive any hints/comments and suggestions on this matter !

---

### Post by fkkroundabout on 2014-05-03
there is a small application named 'brightness controller' which darkens the graphics card output, so that's something, but this application does not affect the monitor directly in the same way the buttons would on windows, i am afraid. but certainly it's better than nothing, for now. i strongly empathise with you as i especially dislike bright monitors. i would recommend keep running your thoughts through search engines, as it is likely to be a common problem, and common problems often mean available solutions. alternatively, i hope someone does respond with help for you, on this

---

### Post by lennart3 on 2014-05-03
Thanks !!!!
**YES,YES,YES** - the brightness controller app works great !!!
Thanks a lot, sometimes there is too much info in forums, I found a lot of posts with brightness problem, tried some solutions without success- and actually
most of the posts were about the non-working function keys. Thanks again !

---

### Post by RSA-2010 on 2014-08-20
On my T135-S1310 running Kubuntu, I was previously using the acpi_backlight=vendor trick in the grub.cfg successfully.  However, after upgrade, that wasn't working.

The gist of the story is that somehow or other the default is that your OS is trying to do things via Toshiba brightness controls but needs to be talking Intel, the graphics maker.  

I tried everything I could find via extensive googling, including combinations of grub entries like:

```
acpi_osi="!Windows 2012" 
acpi_osi=Linux
acpi_backlight=vendor video.use_native_backlight=1
acpi_backlight=legacy
```

 . . . et cetera.  Some would at least make the little on-screen slider appear, but others did not, and in any case none of them worked.  I also had that nomodeset thing going at times, but all that seemed to do was jack up my resolution altogether.

I finally found a dude who recommended creating xorg.conf and adding 

```
    Option "RegistryDwords" "EnableBrightnessControl=1"
```

 . . . on a Toshiba, as I recall, but that didn't seem to do the trick for me either.

I finally found this cat:

[http://techoverflow.net/blog/2014/07/27/how-i-solved-my-toshiba-backlight-issues/](http://techoverflow.net/blog/2014/07/27/how-i-solved-my-toshiba-backlight-issues/)

 . . . who noted what needed to be added in xorg.conf to make the OS talk properly to the Intel bits . . . but I had grub manipulations still present which resulted in Sleep not working.

Since that would be battery-death just the same, I finally removed the grub manipulations, and that is the only thing that makes both backlight and sleep function properly for me.

Specifically, in Devices, my xorg.conf looks like this:

```
    Identifier  "Card0"
###    Driver      "modesetting"
    BusID       "PCI:0:2:0"
    Option "RegistryDwords" "EnableBrightnessControl=1"
    Option "Backlight" "intel_backlight"
    Driver      "intel"

```

I don't know if the EnableBrightnessControl bit is needed . . . I'll test that some other time.  Nothing is in flames, though, so I take that as a good sign.

Good luck.

---

