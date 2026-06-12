---
title: "Video problem Gutsy 64bit with ati driver"
date: 2007-11-03
forum: General Help
---

### Post by Digitallysick on 2007-11-03
When i go to play any video the screen goes black (the whole screen) then it returns to normal, when the video plays its just flashing and sped up, unwatchable, at first i thought it was mplayer so i tried vlc, and it does the same, what could cause this?  Does it have something to do with the ati driver/compiz?

---

### Post by Light- on 2007-11-03
have you tried it with compiz disabled?

---

### Post by Digitallysick on 2007-11-03
have not tried that yet, but i will see, if it works with compiz disabled, then how can i fix it?

---

### Post by Light- on 2007-11-03
re-enable compiz, then try enabling the "workarounds" in ccsm

---

### Post by Digitallysick on 2007-11-05
with compiz off, video plays fine, when compiz is enabled, video is jumpy and unwatchable i checked csm , works arounds are checked. but i still have the same problem

---

### Post by Maestro23 on 2007-11-05
> **Digitallysick said:**
> with compiz off, video plays fine, when compiz is enabled, video is jumpy and unwatchable i checked csm , works arounds are checked. but i still have the same problem

Been seeing this on the boards of other Distros as well, not just in Ubuntu.  As far as I know, there is not a fix yet for this bug.

---

### Post by RavanH on 2007-11-10
> **Maestro23 said:**
> Been seeing this on the boards of other Distros as well, not just in Ubuntu.  As far as I know, there is not a fix yet for this bug.

Bugger! And I was so happy with the arrival of ATI 8.42.3 :( should going back to 8.40.2 help?

---

### Post by Maestro23 on 2007-11-10
> **RavanH said:**
> Bugger! And I was so happy with the arrival of ATI 8.42.3 :( should going back to 8.40.2 help?

I did notice something today.  I'm running the new ATI driver (8.42.3) in 64-bit Gutsy.  I switch my Compiz theme from a gtk based theme to a metacity theme.  Playback of movie trailers, any embedded video on the net is smooth now. Also my OpenOffice works correctly again. There's a bug with hits gtk plugin as well.

Never had a problem watching the vids in a standalone player anyway though, just embedded.

---

### Post by Digitallysick on 2007-11-10
It happens to me with either player, embedded and stand alone. The video just flickers, or the screen will go black for min, and then flicker. Its a brand new video card to

---

### Post by Digitallysick on 2007-11-13
I think i fixed part of the problem, i opened VLC and went to Preferences> Video Output Modules> t and checked advanced, i then from the drop down instead of "default" i changed it to "x11 video output" and hit save , now my videos are perfect!

---

### Post by samshi on 2007-11-14
Thanks man that was the greatest help!!!!

---

### Post by RavanH on 2007-11-19
> **Digitallysick said:**
> I think i fixed part of the problem, i opened VLC and went to Preferences> Video Output Modules> t and checked advanced, i then from the drop down instead of "default" i changed it to "x11 video output" and hit save , now my videos are perfect!
VLC works for me without these changes, however: this does indeed do the trick for Gnome Player :)

In Gnome Mplayer go to **Edit>Properties** and select **Video Output: x11** ... 

And also the regular Mplayer: Right-click the player and select Preferences and on the tab Video select X11 .

Thanks Digital! :)

---

