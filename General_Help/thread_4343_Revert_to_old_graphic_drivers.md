---
title: "Revert to old graphic drivers?"
date: 2004-11-14
forum: General Help
---

### Post by phew on 2004-11-14
Hi,

I have a IBM Thinkpad R50 with ATI Mobility Radeon 7500.. which seems to be unsupported by the fglrx drivers.. anyway, I want to revert to my old drivers, and changed all the fglrx to ATI in the /etc/X11/Xfg<tab> file... but my Quake3 doesn't work anymore! It did before I tried the fglrx drivers.. slow but it did. Now it says I have to use software mode. But my glxinfo says "direct rendering: on"! What's up? How can I revert to the old drivers?

---

### Post by HiddenWolf on 2004-11-14
replace 'fglrx' in your xfree86config file to 'ati'

That should do the trick, but you won't have 3d acceleration anymore, and that means no doom 3.

---

### Post by phew on 2004-11-14
Dude, that's my whole point. I don't have 3d acceleration anymore. Doom won't run anyways, but Quake 3 ran totally fine on Windoze and "ok" unter the default drivers.. how can I get the 3d acceleration back? I mean it's not just "gone", is it? There's gotta be a way to redo the auto-detection or something (besides reinstalling the whole system).

---

### Post by glmeece on 2004-11-16
I'm in the same boat. I mistakenly installed the fglrx drivers for my Radeon 7200 (pre-fglrx support) and ended up hosing my X-server. I edited my config file, so I have X back, but now OpenGL acceleration is in the toilet. Quake 3 was halfway enjoyable, now it's in slideshow mode.
   
   Anyone know how to deal with this?  Additionally, I get the "[fglrx:firegl_init] *ERROR* Device not found!" error on bootup.
   
   Anyone have any suggestions?  [img]http://www.ubuntuforums.org/images/smilies/eusa_shifty.gif[/img]

---

### Post by glmeece on 2004-11-17
OK, I ended up answering my own question about getting rid of the error *and* reinstating 3D acceleration... [img]http://www.ubuntuforums.org/images/smilies/eusa_clap.gif[/img]
     
     **Removing the Error**
     You must edit the "modules" file in the /etc directory.  
   For a GUI method, try:
  [font=Courier New][color=Navy]    sudo gedit /etc/modules[/color][/font]
     Non-GUI:
  [font=Courier New][color=Navy]   sudo pico /etc/modules[/color][/font]
     Now, just remove any lines that refer to the "fglrx" stuff.
     Reboot and you'll not see that line anymore.  However, DON'T reboot just yet...
     
  **   Re-enabling 3D Acceleration**
     As with the steps above, you need to edit the same file.  What you need to do is *insert* "ati" to re-instate the original "weak but works" 3D acceleration.
   *Now* you should reboot.  The error should be gone, and you should have a modicum of 3D goodness back in action.
   
 In my case, I was able to get back enough so Quake 3 changed from a slide-show to a playable game (still no sound though!). I also installed Army Ops and UT 2004 just for grins. Both are playable if I lower my screen res and don't go for all the eye candy. Either would have been a joke if I hadn't gotten acceleration back.
   
 As mentioned in other posts, you of course need to have already edited your XF86Config-4 file and have replaced "fglrx" with "ati". I went with this assumption as you'd *have* to do that in order to have your X-server working at all (at least on my machine with a Radeon 7000/7200).
   
 FWIW, I'm going to try changing the module from "ati" to "radeon" and see if the native drivers give me anything else (besides trouble). I'll report if it's worthwhile.

---

### Post by phew on 2004-11-17
Hehe that's funny, I also came up with my own solution... well, copied from some guy over at the Gentoo forums..

Here goes:

Enter the following in the device section of your XFree config file...

  Option "AGPMode" "4"
  Option "AGPFastWrite" "True"
  Option "EnablePageFlip" "True"

I did this and - it worked. Quake ran as usual. 
Later this day I went to some LUG meeting in my town, and a guy gave me WineX.. now Quake runs FASTER on WineX than native with the ATI drivers! This is kinda sick. Also WC3 and all my other games run smoothly.. sound, everything. Really cool! Try WineX if your ATI drivers suck...

Quake is really perfect now!

---

