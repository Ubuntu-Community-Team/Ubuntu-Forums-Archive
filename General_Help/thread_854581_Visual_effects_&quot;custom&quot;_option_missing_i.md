---
title: "Visual effects &quot;custom&quot; option missing in Hardy"
date: 2008-07-09
forum: General Help
---

### Post by vancouverite on 2008-07-09
Hi all,
I upgraded to Hardy a while ago and lost one of the options in the "Visual Effects" tab in the Appearance Prefs dialog that I used frequently.  

Some of the programs that I run as an engineer (most notably Matlab) do not work well when compiz is active (no menus, resizing of frames within the window doesn't work, etc), so I disable compiz to get the proper functionality.  When I go to turn it back on (admit it, even on a "work machine" intuitive window and effects handling makes life easier) I have to:
1) System -> Prefs -> Appearance -> Visual Effects and select "Normal", then I have to 
2) System -> Prefs -> Advanced Desktop Effects Settings and turn on the individual options that I have grown accustom to.

Previously, there was a "Custom" option in the Visual Effects tab that eliminated the second step.  I have tried re-installing the Advanced Desktop Effects Settings manager through synaptic, but the option is still missing.

Does anybody have any recommendations for me?  This behavior is the same on two totally different computers, one Dell and one that I built.

Cheers,
Seth

---

### Post by sayakb on 2008-07-09
The Custom Option doesnt seem to be there in Hardy. You can try exporting your compiz profile to make a **filename.profile** file and import it each time to avoid the hassle. To export/impost, press Preferences in CCSM.

---

### Post by sayakb on 2008-07-09
[https://bugs.edge.launchpad.net/compizconfig-settings-manager/+bug/178467](https://bugs.edge.launchpad.net/compizconfig-settings-manager/+bug/178467)
Says there is a fix. Try upgrading to the latest Compiz and see.
[http://ubuntuforums.org/showpost.php?p=5335372&postcount=24](http://ubuntuforums.org/showpost.php?p=5335372&postcount=24)

---

### Post by vancouverite on 2008-07-09
Thanks for the replys LII.  I upgraded my compiz, but to no avail on getting "custom" back.  However, I think saving and loading a set profile is the perfect solution to this problem.  I can even keep a copy online and be able to set all my Ubuntu computers just to my liking!

Cheers,
Seth

---

### Post by sayakb on 2008-07-10
Glad I could help! :)
Please mark the thread as solved.

---

### Post by jerome1232 on 2008-07-10
actually there's a package you can install, simple-ccsm that will put the custom option there again.  also fusion-icon will put an icon up in your systray that allows you to turn compiz and/or emerald off/on by right-clicking on the icon and selecting which window manager you want to use.

---

### Post by sayakb on 2008-07-10
Simple CCSM would bring the option back but since OP is using the usual CCSM to save his settings, I doubt that the simple-ccsm would bring back the old settings for him (Though, I may be wrong) ;)

---

### Post by jerome1232 on 2008-07-10
I use the usual ccsm to edit my settings, so thought I'd test it out, and switch from custom to none then back to custom. It does restore those advanced settings! I've never even used the simple cssm and I've never actually used this method to turn off compiz so thought I would try.

The fusion-icon package is actually easier if you find yourself turning off compiz alot anyways IMHO so no real need for simple-cssm if you have fusion-icon I guess. cheers

---

### Post by shamusl on 2008-07-10
> **jerome1232 said:**
> actually there's a package you can install, simple-ccsm that will put the custom option there again.  also fusion-icon will put an icon up in your systray that allows you to turn compiz and/or emerald off/on by right-clicking on the icon and selecting which window manager you want to use.

simple-ccsm works great for me, thanks.

---

