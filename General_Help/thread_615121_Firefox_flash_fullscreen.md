---
title: "Firefox flash fullscreen"
date: 2007-11-16
forum: General Help
---

### Post by joeri_83 on 2007-11-16
I've noticed on a lot of sites with flash videos, they will not go to fullscreen mode when I click the icon. I'm using Firefox, and Flash version 9.0.31.0. It's not an issue of pop up blockers either. Any ideas?

---

### Post by joeri_83 on 2007-11-16
I should perhaps add that it works on some sites, like YouTube and Google Video but not on others.

---

### Post by joeri_83 on 2007-11-17
Nobody? Has this got anything to do with the Linux version of the flash player?

---

### Post by GreatSlovakia on 2007-12-03
The "real" fullscreen option (not a new window) is still in beta on linux... isn't working for me in ubuntu... I always get a 200x200px window, which disappears when I click on it or try anything with it... but that is after I installed the flash player beta...

---

### Post by motang on 2007-12-04
> **GreatSlovakia said:**
> The "real" fullscreen option (not a new window) is still in beta on linux... isn't working for me in ubuntu... I always get a 200x200px window, which disappears when I click on it or try anything with it... but that is after I installed the flash player beta...
Yep same here, but this issue started with Ubuntu 7.10.  With Ubuntu 7.04 I had no problem, full screen worked the way it was suppose like it does on my Win XP Pro machine.  Hopefully this would be solved soon.

---

### Post by fatbuttlarry on 2007-12-14
I'm getting the small window pop-up too, but not for Google Video.  For some reason Google video works great.  Youtube, which most videos are hosted on does the small window.

I have a "maximize" button on the window which works for now, but it really sucks when something that used to work gets broken! :/

-Tres

---

### Post by werewolfzx8 on 2007-12-14
I'm having the same problem. I'm also having a problem with when I adjust sound. Adjusting the sound, or really doing anything besides maximizing the window, causes the window to close.

Edit:
I'm going to try this when I get home:
[http://ubuntuforums.org/showthread.php?t=600795]("http://ubuntuforums.org/showthread.php?t=600795")

---

### Post by some.hacker on 2008-02-09
I have the "small window, and when I click on it the window goes away" problem as well. Any news yet?

---

### Post by anatole on 2008-02-13
> **some.hacker said:**
> I have the "small window, and when I click on it the window goes away" problem as well. Any news yet?

go to system > preferences > advanced desktop settings (you need to have the package compizconfig-settings-manager iirc) and in Utility > Workarounds, uncheck legacy fullscreen support. This even improved the fullscreen stuff on my comp as now i can switch between fullscreen and window during playback.

---

### Post by luisito on 2008-02-25
> **anatole said:**
> go to system > preferences > advanced desktop settings (you need to have the package compizconfig-settings-manager iirc) and in Utility > Workarounds, uncheck legacy fullscreen support. This even improved the fullscreen stuff on my comp as now i can switch between fullscreen and window during playback.

Interesting. I tried this and now my video goes fullscreen for one tenth of a second and then it immediately closes and comes back to the original youtube page.

---

### Post by dysonsphere23 on 2008-03-06
> **anatole said:**
> go to system > preferences > advanced desktop settings (you need to have the package compizconfig-settings-manager iirc) and in Utility > Workarounds, uncheck legacy fullscreen support. This even improved the fullscreen stuff on my comp as now i can switch between fullscreen and window during playback.

Thanks for the workaround tip.  That brought up the fullscreen for me on YouTube, but the frame rate of the video is all messed up in that mode, it looks like still images flipping every 3 seconds or so.  It is fine in the small YouTube window when I close fullscreen.

---

### Post by reeferman on 2008-03-14
I gotta say I'm running amd64 and the only way I could get it to work was running my windows firefox through wine emulating windows 98 (the default 2000 setting made video stop on full screen after a few seconds).  I tried all the workarounds listed here & every other relevant thread I could find (other forums as well), I even went and tried several alternative players etc.So far it's working like a dream (strange that it made me install the plugin again even though it should have been installed on that browser).  Now the only reason I have to use windows is my games.:guitar:

---

### Post by dysonsphere23 on 2008-03-15
Thanks for the tips reeferman.

However when I run Firefox as Windows 98 in WINE I have no sound and the fullscreen is blank (sometimes white, others black).

Tried with 2000 and XP, but no good with those either.

---

### Post by dysonsphere23 on 2008-03-15
> **dysonsphere23 said:**
> Thanks for the tips reeferman.

However when I run Firefox as Windows 98 in WINE I have no sound and the fullscreen is blank (sometimes white, others black).

Tried with 2000 and XP, but no good with those either.

Fixed when I upgraded to Wine 0.9.57 from the WineHQ repository.

Thanks for the help.

---

### Post by gasparov on 2008-03-15
Running firefox in wine ?come on....

---

### Post by forrestcupp on 2008-03-15
> **gasparov said:**
> Running firefox in wine ?come on....

Hey, don't knock it till you've tried it.:)

Seriously, I have done that before to access certain sites that use a plugin that is Windows only.  Since then, all of the web sites that I needed that for work in Linux now.

---

### Post by gasparov on 2008-03-16
:D
I have no doubt it works well but is not a solution, firefox used to handle flash videos in fullscreen pretty well, it does on other distros (on my desktop for example)....

Sorry for the tone ....

---

### Post by flat on 2008-07-14
the problem with fullscreen seems to be gone for me after i switched to 'none' for visual effects in Appearance Preference.

---

