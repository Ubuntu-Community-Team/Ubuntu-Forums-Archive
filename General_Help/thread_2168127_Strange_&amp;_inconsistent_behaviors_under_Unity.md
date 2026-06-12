---
title: "Strange &amp; inconsistent behaviors under Unity"
date: 2013-08-16
forum: General Help
---

### Post by r_avital on 2013-08-16
Hi,

I've found only one post addressing this, and it referred to oneiric and natty, while the problems I've observed are on Raring.

The system:
i7-950 Quad-Core processor, hyperthreading enabled.
nVidia GeForce GT-640.
Nvidia driver v.310.44 (verified in both sysinfo and Synaptic).

1. Launcher is set to auto-hide.  Initially, bumping the mouse against the left edge would reveal it.  Now, it does not.  I am aware, that it's not the "force" or "speed" or slamming of the cursor against the edge that matters, but just "pushing" the cursor against the edge, that should bring it back.  

I've set the sensitivity in both the Compiz Unity plugin and the Unity-tweak-tool, to no avail.  Sometimes it works, sometimes not.  Sometimes It only works if I push AND move up/down against the left edge.  Most of the time, I have to hit Alt-F1 to "give the keyboard focus" to the first item on the launcher, just to reveal it.

2. Panel transparency: unity-tweak-tool has a setting for it, no matter what I do, it's never transparent, always opaque.  I move the "transparency level" slider all the way left to right, it simply moves between black, white and all the greys in between.  "Opaque for maximized windows" enabled, disabled, no difference.

3. Minimized windows, when restored (through Alt+Tab), are completely black.  Just a nice window frame with decorations, no content.  Moving the window around changes nothing.  Resizing the window, even very slightly, "refreshes" the window and shows its contents again.

4. I use several machines, on a KVM switch.  All of them are in portrait orientation.  If I switch away from the Raring machine long enough for the screen-lock to engage (I use no screen-savers), when I come back to the Raring machine, the display is in lower resolution (everything is much too large), and in normal landscape orientation.  Launching a terminal and issuing "xrandr -o left" resets the correct orientation AND resolution.  Sometimes, instead of "left" I need to use "normal" because, believe it or not, it goes form landscape to clockwise (when it should be counterclockwise), but "normal" brings it back to the correct orientation (couterclockwise).

These are minor, but annoying (escpecially 3 and 4 above).  I understand there may not be a solution, other than to wait for the next LTS, hope, pray, do rain-dances to invoke whatever fixes fortune may produce. 

 ***I just would like to know if there is anyone else who has experienced these, or similar such inconsistent behavios, that do not respect the settings set by the user.***

I'm not sure I should use nVidia drivers other than v.310.44, as the higher-version is said to be unstable.  I could try, but with the inherent instabilities of Raring, I'm afraid to breathe next to the system for fear of breaking yet something else.

Thanks in advance.

---

### Post by r_avital on 2013-08-19
Bump

---

