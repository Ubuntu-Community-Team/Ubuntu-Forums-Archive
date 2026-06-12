---
title: "No Visual Effects"
date: 2008-03-16
forum: General Help
---

### Post by jackdelamare on 2008-03-16
Hello,

When I go to the Visual Effects menu on Ubuntu and click on any of the effects except for "none", they do not work. It says "Desktop effects could not be enable".

Please help.

Jack

---

### Post by scragar on 2008-03-16
what graphics card do you have? you may need to install restricted drivers for the desktop effects, alternativly it may be the case that your drivers just need to be whitelisted(although that's only if the drivers will work but ubuntu still thinks they wont).

---

### Post by jackdelamare on 2008-03-16
I am unsure of the graphics card and since I cannot get into Vista currently could you please tell me how to find out in Ubuntu?

---

### Post by scragar on 2008-03-16
[http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/](http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/)

```
lspci -v | less
```and post the output back here if you can(or if you can find your own graphics card name that'd be even better).

---

### Post by jackdelamare on 2008-03-16
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Lenovo Unknown device 383c
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA])
        Subsystem: Lenovo Unknown device 383e
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
        Subsystem: Lenovo Unknown device 383e
        Flags: bus master, fast devsel, latency 0
        Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contolle:

```

---

### Post by scragar on 2008-03-16
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA])
```
looks like it's a GM965 or GL960 built in graphics card.

your card for some reason is blacklisted, you can remove the restrictions:
```
mkdir -p ~/.config/compiz; echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```
you will also need to make a small edit to your Xorg config file:
```
sudo gedit /etc/X11/xorg.conf
```
and find where it says:
```
Section "Extensions"
    Option "Composite" "false"
EndSection
``` replacing false with true.

after editing xorg you will have to restart your gui for changes to take effect, log out then press ctrl+alt+backspace to quickly restart the graphics and log back in.

---

### Post by Ub1476 on 2008-03-16
You should know that removing the blacklist may lead to issues.

---

### Post by jackdelamare on 2008-03-16
What kind of issues? I don't want to screw it up...

---

### Post by scragar on 2008-03-16
issues can vary from the occasional messed up graphics, or compiz not picking up on videos correctly at a minimum to completely closing your graphics in the event of a big error.

no major errors reported regarding your graphics card and graphic effects(although there are reports of errors starting compiz in the first place).

---

### Post by jackdelamare on 2008-03-16
Well do you think I should go ahead and do it?

---

### Post by scragar on 2008-03-16
if it doesn't work properly you can always turn it off.

---

### Post by jackdelamare on 2008-03-16
So do what was suggested, hope it works and if it doesn't then change the codes back?

---

### Post by scragar on 2008-03-16
```
metacity --replace
```
from any command line will turn compiz off.

you shouldn't need to remove the first command, although you will want to remove the edit to the xorg.conf file.

---

### Post by jackdelamare on 2008-03-16
When I go into the file, it is empty.

---

### Post by dopievoli on 2008-03-17
> **scragar said:**
> ```
metacity --replace
```
from any command line will turn compiz off.

you shouldn't need to remove the first command, although you will want to remove the edit to the xorg.conf file.

I'm currently using the GM965 drivers and I've entered the command in the terminal, however in the Xorg.conf I do not find the **Section "Extensions"** at all what should I do?

---

### Post by Tomatz on 2008-03-17
You can easily disable compiz if you do.

---

### Post by jackdelamare on 2008-03-17
Ugh, when I go into that file it is empty, so I cannot change the line thing, so can somebody please help me further?

---

