---
title: "[Xubuntu] Running old P4. Ran intel update tool, X/LightDM has damaged fonts."
date: 2013-08-15
forum: General Help
---

### Post by Chris_Katko on 2013-08-15
Hello everyone, I am new to this place.

I ran a fresh install of Xubuntu 13.04 onto an old Pentium 4 2.6 GHz (single core, no hyperthreads!). It has a:

```
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

Everything was fine. I had to manually make an xorg.conf to force it to detect 24-bit color on my old LCD television over VGA, and use XRANDR to force it to get into the insane resolution of 1360x768, but all was incrementally fixable.

Then I did something "stupid." I ran the Intel Graphics Driver Installer tool from the XFCE/Gnome settings manager. It ran, updated, and on reboot my computer is crippled.

1) My login screen is now completely black and glitched. If I start typing the dialog box appears but no text. The mouse cursor is fine.
2) Xfce/X/LightDM has corrupted drawing certain dialog boxes as evidenced by the following screenshot:


[http://i.imgur.com/1cH58MQ.png](http://i.imgur.com/1cH58MQ.png)

The letters g, h, n, o, s, and u as well as the numbers 0, 1, 2, 3, and 5 are gone! Also notice the status bar on the top. Notice how it seems to show the "shadows" of the text just fine, but the normal "foreground" text is all funkified AND YET they (obviously) have to be the exact same font--foreground and shadow--so it's something strange with the dialog text drawing. Lastly, note that my once-beautiful Conky on the far right is nothing but lines now. No text at all.

(*The video playback is fine)

So the key to this is: Everything worked fine, I ran the Intel graphics installer, everything is messed up.

I tried,

```
 $ sudo apt-get purge xserver-xorg-video-intel 
```

and then reinstalling it, but that didn't help. I tried the same with one named like "intel-video-drivers" but I don't recall the exact name right now.

---

### Post by sudodus on 2013-08-16
Welcome to the Ubuntu Forums C*hris_Katko* :-)

Try to remove the intel graphics completely without reinstalling it. You can try it from a text screen

***ctrl + alt + F1***

if that works better.

Reboot.

Then I suggest that you continue running with the built-in drivers (and the tweaks you were using before).

---

