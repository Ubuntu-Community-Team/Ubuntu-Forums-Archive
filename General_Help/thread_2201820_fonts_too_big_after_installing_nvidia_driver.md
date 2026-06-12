---
title: "fonts too big after installing nvidia driver"
date: 2014-01-26
forum: General Help
---

### Post by uselessone122 on 2014-01-26
I have recently installed kubuntu 13.10 on my computer, and everything went smooth, but after installing the nvidia driver from additional drivers, I rebooted and all the fonts are too big and it looks bad. How do I fix this? Btw I have an nvidia geforce gts 450 with 319.32 driver.

---

### Post by DeMus on 2014-01-26
You are probably using the wrong settings for your monitor.
Since you use Kubuntu try this:
Open System Settings > Display and Monitor
In the right hand side window you see three icons at the bottom. Click the right one and choose the correct resolution for your monitor.
Choose apply and stop the system settings.

Success.

---

### Post by buzzingrobot on 2014-01-26
Look especially at the DPI setting.  Typically, it's at 96.  I've seen it much higher here sometimes after installing the Nvidia driver, and that will push font size up.

---

### Post by uselessone122 on 2014-01-26
I went into the font settings and set it to force fonts to 96 and rebooted the computer, and everything is normal now, but the login screen is still big. Any way to fix that?

---

### Post by charles.figura on 2014-04-19
I'm curious about this, too - I just updated to 14.04 and installed the NVIDIA drivers and had the same problem.  I found the 'force 96dpi' setting on my own, and it looks *mostly* normal.  But the boot screen (the black screen with the glowing 'kubuntu') is large and pixellated.  While that's not a big deal, it makes me think that there *is* a misconfiguration somewhere.

---

### Post by voidcastr on 2014-06-02
I found the following to be a somewhat clean solution to the problem (found this somewhere on the net - all credits to whomever figured it out). It will only work for lightdm users. If you're on Ubuntu and you don't know what lightdm or an X display manager is in general, you are probably using lightdm.

**1.)** Run this command in a konsole to find out your current DPI setting:
```
$ cat /var/log/Xorg.0.log | grep -i dpi
```

For me, the output with a freshly installed Kubuntu 14.04 x64 with proprietary nvidia drivers contained:
```
[    11.509] (--) NVIDIA(0): DPI set to (143, 144); computed from "UseEdidDpi" X config
```

To no surprise, all fonts appeared ridiculously huge - even deforming windows and making the desktop pretty much unusable. The issue was also present in the login screen.

**2.)** Edit this file with superuser permissions:
```
/usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
```

Look for a line starting with "xserver-command" and append a -dpi XXX argument to it. For me, the line now looks like
```
xserver-command=X -core -dpi 96
```

**3.)** Reboot. Logging out and in again won't suffice.

**4.)** Enjoy fonts of appropriate size. Check again with the above cat/grep command:
```
[    11.643] (++) NVIDIA(0): DPI set to (96, 96); computed from -dpi X commandline option
```

So, this EDID based DPI calculation seems to be broken. Not sure if in xorg, in the nvidia driver, in some Ubuntu package or inherently.

Does anybody know more about this? Can anybody provide a link to some bug on the appropriate tracker?

---

### Post by buzzingrobot on 2014-06-02
> **voidcastr said:**
> I found the following to be a somewhat clean solution to the problem...So, this EDID based DPI calculation seems to be broken. Not sure if in xorg, in the nvidia driver, in some Ubuntu package or inherently.

Does anybody know more about this? Can anybody provide a link to some bug on the appropriate tracker?

Thanks!   Nice writeup.  

I'm gonna blame Nvidia since I've never seen it happen using anything other than Nvidia video with an Nvidia driver.

---

### Post by a-you on 2014-11-13
Thanks [**[COLOR=#000000]voidcastr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1927328"). Worked for me too; ubuntu studio (so approximately xubuntu) 14.4 trusty 64 bit, nVidia GeForce GT 330M.

---

