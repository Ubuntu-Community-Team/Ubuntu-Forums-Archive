---
title: "fiesty Live CD-Desktop Effects"
date: 2007-05-05
forum: General Help
---

### Post by apunc1 on 2007-05-05
Just to preface, i am a happy dapper user. i thought i would boot up the feisty live cd just to see the fancy new desktop effects. the live installer boots up fine and it detects my wired internet connection and loads web pages. when i went to system>preferences>desktop effects it said i needed a nvidia driver for my graphics card. i ok-ed the install and when finished installing i was prompted to reboot. i rebooted with the live cd in but was instructed to take the live cd out and thus rebooted to my installed dapper. i inserted the live cd again and rebooted. when i went to desktop effects again, i was again prompted to install the same nvidia driver. 
if i install feisty will my graphics card be installed correctly? 
here is the output of my lspci


0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:08.0 Communication controller: Agere Systems LT WinModem (rev 02)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

i'm not jumping to upgrade to feisty (or edgy for that matter) because dapper is a LTS release and i am happy with it. i however would like to be able to safely upgrade (via clean installs) without graphics card problems. do the live cd messages indicate any problems or is it just because i have not done a proper install?

---

### Post by schmidtbag on 2007-05-06
The live CD saves absolutly nothing to the HDD.  It makes no difference what you use.  Yes, you can save plenty of data when running the live CD but I believe thats all RAM storage if you save to the "filesystem" drive.  When a computer reboots, the RAM is cleared so when you run the CD again you're back where you started.  As far as I know, Ubuntu has nothing to save your desktop to the HDD with, its a relatively basic OS.  If you tried something such as Knoppix, then you could save data while booting with the CD but it doesn't have the same features since its KDE.

---

### Post by izizzle on 2007-05-07
What types of desktop effects are available in fiesty. Does it have Wobbly windows? or The 3D cube?. Any others?

---

### Post by schmidtbag on 2007-05-08
> **izizzle said:**
> What types of desktop effects are available in fiesty. Does it have Wobbly windows? or The 3D cube?. Any others?

ya its basicaly the beryl effects just a lott less and not customizable

---

### Post by Coucouf on 2007-05-08
The desktop effects are a lot *less customisable* than in beryl, but most of the events handled by beryl have an animation. As mention, the desktop effects have :
- the desktop cube
- wobbling windows
plus :
- the windows presentation function when clicking the top right corner
- windows preview in alt+tab
- unfocussed windows title bar transparency
- windows/dialog fade in/out when opening/closing
- windows zoom out to the task bar when minimizing/windows zoom in from the task bar when unminimizing
- kind of wave for some menus and for tooltips
- fade in/out for some menus
- beryl windows maximization effect
- windows greyed when not responding

I think that's *all*. I'll update if other effects come to my mind/monitor. :)

In fact the only thing that I would miss from beryl is the windows preview when leaving the mouse on the taskbar button representing the window.

So the downside compared to beryl is mainly that those effects are not customizable at all.
You can only enable/disable the wobbling windows and the desktops cube separately.

---

### Post by izizzle on 2007-05-08
Ok thanks guys. I think ill stay with the preinstalled effects, save myself the frustration of installing beryl...:D

---

### Post by warjowuch on 2007-05-09
This 'restart system' is in my opinion a noob-ish option. It should be ok to just restart your X/Gnome with control alt backspace. Then you should be, also on livecd-environment, fully 3d accelerated

---

### Post by apunc1 on 2007-05-09
> **warjowuch said:**
> This 'restart system' is in my opinion a noob-ish option. It should be ok to just restart your X/Gnome with control alt backspace. Then you should be, also on livecd-environment, fully 3d accelerated

thanks, i'll try that.

---

