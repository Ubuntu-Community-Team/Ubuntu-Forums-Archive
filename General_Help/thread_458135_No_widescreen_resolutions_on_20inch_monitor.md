---
title: "No widescreen resolutions on 20inch monitor"
date: 2007-05-29
forum: General Help
---

### Post by prettynew on 2007-05-29
I have taken the opportunity to switch to ubuntu, and it is great. I do however have a problem where my 20 inch BENQ FP202W monitor does not display its optimal resolutions (1680x1050). I can only get it to go to 1280x1024.

I believe it has to do with my VIA integrated graphics on a MSI KM4M-V motherboard. I have tried switching the VIA packages in Package manager (from VIA to VIA Unichrome) but I have had no success. I have also messed around with xorg (adding modes etc) but when these modelines are added they still dont show up in my GUI. My Xorg logs show this :

(II) VESA(0): Not using mode "1680x1050" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (width too large for virtual size)


Would anyone know if this a limitation of the LINUX support available for my motherboard (and thus would need to get myself a new video card), or am I missing some sort of driver/BIOS update? I have looked extensively for anything on this, and I cant find a thing.

Any help would be appreciated.

---

### Post by kuja on 2007-05-29
You may need more than the modelines to get it to take, try adding a line like this:

Option         "metamodes" "DFP-0: 1680x1050_60 +0+0; DFP-0: 1024x768 +0+0;
DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0; DFP-0: 1600x1024_60 +0+0"

Put it in the section for Screen 0

It should force 1680x1050 @ 60hz, at least it does for me with my 22" viewsonic.

---

### Post by coffeecat on 2007-05-29
Have a look in /etc/X11/xorg.conf, in the "Device" section, specifically the Driver line. What does it say? If it says "vesa" then that's your problem - despite your installing the VIA driver xorg will still be using the generic VESA driver which is very limited.

My machine has onboard VIA graphics but I installed a nvidia card when I built it a couple of years ago because there wasn't then an (easily available) VIA graphics driver. Just recently, as an experiment, I took the nvidia card out, edited xorg.conf to use the VIA driver, and was pleasantly surprised at how well it drove my 1680x1050 monitor.

If you've got "vesa" under Driver, just edit this to "via". You don't need to add modelines - not in the version of xorg that comes with Feisty - but you'll need to make sure you've got the appropriate modes listed in Section Screen. But it sounds as though you've done that already.

---

