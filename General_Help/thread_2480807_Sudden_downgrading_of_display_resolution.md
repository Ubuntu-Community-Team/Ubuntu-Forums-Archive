---
title: "Sudden downgrading of display resolution"
date: 2022-11-10
forum: General Help
---

### Post by Nosphky on 2022-11-10
Using UbuntuStudio 22.04.1 with KDE Plasma.  The hardware setup has worked fine for some years with occasional upgrading but nothing in the past few months.  I share keyboard, trackball and display with a Windows10 box via a KVM switch. The display is an IIyama 24" 16:9 flat panel. Both computers are shut down at night and rebooted each day.

Suddenly, at boot up this morning, the linux box was giving a really cocked up display. I right-clicked on the screen and selected Configure Display Settings. To my surprise, the only options available today are: 1024 x 768 (4:3); 848 x 480 (53:30); 800 x 600 (4:3); 640 x 480 (4:3).  So I am using 1024 x 768 (4:3) which is far from ideal.

The Windows 10 box is still happily working at 1920 x 1080 giving an excellent display (as I had been used to for so long on both machines that I had forgotten the values of the resolution settings).

So, I have no idea what has upset the linux box. The System Settings gui today shows no options for a 16:9 display. Is there a way to edit some config file to instruct UbuntuStudio 22.04.1 to reset to 1920 x 1080 ?

---

### Post by Autodave on 2022-11-11
I would start by hooking the monitor up directly to the PC.  If your display is back to normal then, I think that your KVM switch needs looked at.

---

### Post by Nosphky on 2022-11-11
> **Autodave said:**
> I would start by hooking the monitor up directly to the PC.  If your display is back to normal then, I think that your KVM switch needs looked at.

Thanks, Autodave. That's the one I overlooked. Hooked directly into the linux box works fine and I get a lot more display settings options including 1920 x 1080 16:9, the one I needed.  So this indicates that one side of my KVM switch has gone weird. The side serving the W10 box was still ok.  Just another example of things working fine right up to the moment they don't.

The D-Link KVM switch that I've had for a few years now only has VGA ins and outs so it's time to look for another switch using something more modern like HDMI.

---

