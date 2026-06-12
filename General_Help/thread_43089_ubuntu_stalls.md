---
title: "ubuntu stalls"
date: 2005-06-20
forum: General Help
---

### Post by Bicky on 2005-06-20
hello everybody,

I've had some instalation problems with ubuntu (it stalled while installing), but after some changes in the bios, it all looks to run fine.
But now the problems are coming back. I can leave ubuntu on for hours, but if I start using it it just freezes after a few minutes (exept for the mouse). It is really anoying, can somebody help me ? I've a AMD athlon thunderbird 1400mhz, and I've installed the AMD image.

Bicky

---

### Post by intangible on 2005-06-20
Have you let memtest86 run through all the way to check for bad memory?

I was having some problems at home and found one of my sticks had went bad.

Also, do you have "athcool" installed?  If you do, try removing it, it causes lockups on some mobos (like mine) but there is workarounds for it.

---

### Post by astoltz on 2005-06-20
Another possibility.  Do you have an nVidia graphics card with the "renderAccel" option turned on in your xorg.conf?

---

### Post by Bicky on 2005-06-21
My memory is fine, I had tested that before installing (because off the lockups in while installing). I couldn't find 'athcool' in my pakages so I think that isn't installed then.
I've a Nvidia graphics card (Gforce2) but couldn't find anything about 'renderAccel'. what do i've to input ? (and where ?).

---

### Post by intangible on 2005-06-21
Try this: **sudo gedit /boot/grub/menu.lst**
Find a line that looks like this (there will be two, ignore the recovery one):

**kernel     /boot/vmlinuz-2.6.10-5-K7 root=/dev/hda1 ro quiet splash **
and put this at the end of that line:
**acpi=off noacpi nolacpi**

Then reboot and see if you still have lockup problems.  If that fixes it, let me know and I'll show you where to put it to make it stick through kernel upgrades.

Also, what motherboard brand and model do you have?

---

### Post by Bicky on 2005-06-21
I'd putten the line: 
' option "RenderAccel" "true" '
in the xorg.conf file in the section "device" but that wasn't helping.
I've also did the thing that intangible told me to do. But after I'd done that, it stalled before gnome even could load.

motherboard information, it is an EPoX EP-8KTA3 with a VIA KT133/KT133A chipset

---

### Post by intangible on 2005-06-21
Have you installed the nvidia drivers for your video card yet?

You can follow this guide:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by Bicky on 2005-06-21
if I try to open the site it says: "toegang tot ubuntuguide.org geweigerd" that's dutch for: you're not allowed to see this site. But I've found another site and have done what it said, and I think it did the trick.

---

### Post by intangible on 2005-06-21
Please share your solution here for others :D

---

### Post by astoltz on 2005-06-21
Since you've already solved your issue, this may be a little late. 

With the nVidia drivers, renderAccel should be "false" - or just commented out in xorg.conf.  This has solved my lock-up problems.  If you are using the generic "nv" driver in the device section of xorg.conf, I don't think renderAccel has any meaning and it will just be ignored no matter what it's set to (obviously setting it to false in this case won't have any effect on the lock-ups).

> kernel /boot/vmlinuz-2.6.10-5-K7 root=/dev/hda1 ro quiet splash
and put this at the end of that line:
acpi=off noacpi nolacpi I tried the noacpi boot option but this did not help in my case (I've not heard the nolacpi suggestion before so maybe I'll give that a shot).

---

### Post by astronerd on 2005-06-21
I'm having the same problems with an ATI X300 video card.  I have tried the binary drivers, mem test, and still get freezes.  There seems to be no real cause either.   Intangible, what do these commands do that you suggested earlier? 
 "   Try this: sudo gedit /boot/grub/menu.lst
Find a line that looks like this (there will be two, ignore the recovery one):

kernel /boot/vmlinuz-2.6.10-5-K7 root=/dev/hda1 ro quiet splash
and put this at the end of that line:
acpi=off noacpi nolacpi   "

Should I try this?  Last time I messed with my video card(changing the drivers) I lost my mouse scroll wheel and still havent been able to get it back, so thats why I am a little hesitant to just try this right away... 
Charles

---

### Post by Bicky on 2005-09-28
Guys please help me, my problem is back. Here some info about my pc:
- epox EP-8KTA3
- AMD athlon thunderbird 1,4ghz
- 128mb SDRAM
- 40gb maxtor HD
- Realtek ethernet
- nvidia geforce 2 (drivers installed)

I found that my processor doesn't support 'energy saving' (don't know the real english term for it, it's "energie besparing" in dutch). So I've put it out at the screensaver options.

why does it keeps on stalling ?
(please don't answer: "reinstall linux")

---

### Post by intangible on 2005-09-29
If you upgraded to Breezy, you probably just need to reinstall the nvidia drivers.
```
sudo nvidia-glx-config enable
```

Does **glxinfo** give you any output?

---

### Post by Bicky on 2005-09-29
I've reinstalled my nvidia drivers.
and the output of glxinfo: is a very much. (to keep te topic clean, I shall not post it)


EDIT: It doesn't helps :'(

---

