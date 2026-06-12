---
title: "Won't resume from standby"
date: 2008-06-06
forum: General Help
---

### Post by sgardne on 2008-06-06
I finally got the wife to switch over to Ubuntu fully :guitar: There's only one hitch: I can't get the darn thing to resume properly from standby. I've tried everything in [this post]("http://ubuntuforums.org/showthread.php?t=350265"), plus some other stuff from random internet sites, and nothing works. I've also upgraded my nvidia drivers, and checked BIOS settings. 

I always have the same result. It seems to standby okay; it powers down, and the standby light blinks like it should. But when I try to resume, the drives spin up and the power light comes on, on the tower, but the monitor appears to stay in standby mode and I can't ping the box from other machines on the network. Pressing CTRL+Alt+F1 has no effect. CTRL+Alt+Backspace does nothing. I end up having to press the reset button to reboot. 

I'm running the 64bit version of 8.04. Nvidia/Intel box.

Thanks for reading.

---

### Post by pedro_orange on 2008-06-06
From what I've heard on the grapevine standby/restore is done by the vendor for the laptop depending on what OS it ships with. So the vendor will only do it for that OS, which tends to be Windows. 

Basically, I'd say, if it works - You're lucky. If it doesn't - I doubt it will. Maybe you're lucky and someone else has done it before and posted a fix.

I could be, and usually am wrong. So feel free to ask around & send flames to /dev/null :)

---

### Post by sgardne on 2008-06-06
This is actually a full sized tower, not laptop.

Edit: also I should mention that it's a custom build that I put together last year that has been running windows until now. It's an Asus P5WD2 with a GeForce 7 series graphics card.

---

### Post by t.rei on 2008-08-05
I have the same effect on a totally different thing: ASUS A6000 with an ATI X700 (compiz+emerald). 

But the same borked resume. Am looking for a solution for some days now. I shure hope I get it working again - it worked "out of the box" on previous releases of ubuntu. :/

---

### Post by ulp on 2008-08-27
I had the same problem on kubuntu across several of the newer releases (8.04 now).  My "fix" was to set my screen saver to an actual screensaver (opengl - euphoria) instead of the blank screen screensaver it was set to before.  Don't know if this will help you guys but it definitely ended my resume from standby problems.

Edit: Way late edit but I realized that the fix was actually to just "test" the opengl screen saver.  After doing so on a current boot, you will not experience the problem.  This is not that user friendly as it requires you to do a dummy screen saver test on each boot but it always works from what I can tell.

---

### Post by jerome1232 on 2008-08-27
I'm not of help but I guess it doesn't hurt to throw in some hardware spec's it doesn't work with. I get that exact thing, my motherboard is an ABIT-KU8,with a Pheonix Bios D686, Nvidia FX56000LE.

I use nvidia-glx-new as my driver, doesn't work with latest drivers from nvidia as of this writing either. (maybe we should all be making/adding to bug reports)

---

### Post by Meson on 2008-11-11
The only fix I currently know of right now is to use the "nv" driver rather than "nvidia"

"nv" are the drivers your system uses before you tell Ubuntu to use the "restricted" drivers.  I'm still looking for a way to resume from standby while using the real nvidia drivers.

---

### Post by Meson on 2008-11-11
Yay!!! I found the solution here: [http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)

I'll summarize:

1) Add this to /etc/X11/xorg.conf:
```

# /etc/X11/xorg.conf
# This can go in either a "Device" section or "Screen" section
    Option      "NvAGP" "1"

```

2) Add this to /etc/modprobe.d/blacklist
```

# /etc/modprobe.d/blacklist
blacklist intel_agp
blacklist agpgart

```

3) Check these settings in /etc/default/acpi-support
```

# /etc/default/acpi-support
ACPI_SLEEP=true
ACPI_HIBERNATE=true
SAVE_VBE_STATE=false
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=true

```
note: I left SAVE_VBE_STATE=mem (which is how it was set already), I will play around with acpi-support when I have more time.

4) I restarted my computer once before testing.


Enjoy!

---

