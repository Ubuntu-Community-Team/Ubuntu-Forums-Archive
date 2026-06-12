---
title: "Dual-screen issues on Ubuntu 18.04"
date: 2018-10-22
forum: General Help
---

### Post by platinum95 on 2018-10-22
[COLOR=#242729][FONT=Arial]I have 2 monitors set up with my Ubuntu system, primary (landscape) and a secondary rotated (portrait) monitor to the left of primary. I've been having a problem where there's about a 2-pixel wide overlap from the secondary monitor onto the primary. This isn't window-specific (as in, its not a window-bleed, its the entire leftmost columns of the secondary framebuffer).[/FONT][/COLOR][COLOR=#242729][FONT=Arial]This issue doesn't occur with both monitors set to landscape. On top of this, strangely, it doesn't occur with the secondary monitor set to portrait and set to the *right* of the primary monitor. Another thing to note is that when arranging the monitors with display settings, there's a space between the monitors when placing the secondary to the right, but no space when placing the monitor to the left. 
Here's a side-by-side comparison of monitor arrangement in gnome-control-center.
 [ATTACH=CONFIG]281409[/ATTACH]
This led me to believe the issue may be in the treatment of rotated screens in gnome-control-center (not rotating around the true origin?) so I started looking at the source for it, making small modifications but to no avail.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've tried manually setting monitor positions with xrandr and managed to remove the pixel overlap by bumping up the distance between the monitors, but the issue I ran into there was that the 'screen' framebuffer (for the overall desktop) ended up consisting of a full bounding box of both monitors (i.e. windows/mouse in the primary display could go above and below the monitor due to the secondary monitor being a higher vertical resolution).
[/FONT][/COLOR]I was also pointed towards arandr by someone else, but this did not work for me.

[COLOR=#242729][FONT=Arial]System-wise, I'm running Ubuntu 18.04 with Wayland disabled (completely different kettle of fish with Wayland), with an AMD Rx370 primary GPU (AMDGPU driver) and an NVidia gtx 660 GPU for compute (NVidia 396 driver).[/FONT][/COLOR]

Has anyone run into this kind of overlap before? It'd also be handy if someone with 2 (or more) monitors could see if the issue can be replicated with a similar layout (primary landscape, secondary portrait to the left of primary).
Failing a direct solution to this, does anyone know how to correct the mouse-boundary issue that comes with the xrandr fix?
 
[COLOR=#242729][FONT=Arial]Thanks[/FONT][/COLOR]

---

### Post by platinum95 on 2018-11-15
Upgraded to ubuntu 18.10, issue persists.

---

### Post by platinum95 on 2018-11-18
I was having issues with screen tearing, and in my attempt to fix that it seems the overlap issue has now been solved.
Solution for me was to add to the xorg device configuration. Full section is now:
```

Section "Device"
     Identifier     "Device0"     
     Driver         "amdgpu"                                                 
     VendorName     "AMD"
     Option "RandRRotation" "on"
     Option "TearFree" "on"
     Option "DRI" "3"
     Option "AccelMethod" "glamor"
EndSection

```

I'm not sure why this solved the overlap issue, possibly something to do with enabling DRI3? Either way, it's solved the overlap but not the screen tearing! Ah well, one step at a time...

---

