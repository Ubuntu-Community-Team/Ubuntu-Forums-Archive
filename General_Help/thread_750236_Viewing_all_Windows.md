---
title: "Viewing all Windows"
date: 2008-04-09
forum: General Help
---

### Post by dstein on 2008-04-09
I sometimes see Mac OS X users press some keys that cause all the open windows to arrange themselves nicely on the screen, such that one can be selected. It seems like a more efficient way of Alt-Tabbing. Is there any similar function in Ubuntu? Is this something that would be handled by the Window Manager or the Desktop Environment? Anyhow, I'm using Gnome. Thanks.

---

### Post by SpaceTeddy on 2008-04-09
gnome itself does not support that feature (as far as i know), but compiz fusion has it build in and actived by default.

what you need to do is enable the gl-desktop. one that runs you should have compiz fusion enabled. just move your mouse to the top-left corner of the screen and all active windows will auto-resize and be displayed in agrid on your screen.

Also, compiz fusion comes with a TON of options.. unforteunatly, it sometimes crashes (at least for me) and needs to be restarted manually... 

hope it helps

---

### Post by dstein on 2008-04-10
Oh no. I installed gnome-compiz-manager and things got kinda messed up. First, the program wasn't opening properly, so I ended up deleting it, however it seems to have permanently changed my settings. Ctrl-Alt-Arrow no longer switches between Workspaces. Also, the effect of switching workspaces (when clicking on a different one on my panel) is no longer the same. The windows used to have a 'sliding' effect, now they seem to have a 'fading' effect. How can I completely restore my settings as if I never installed gnome-compiz-manager in the first place. I like the original settings from when I installed Ubuntu. Making changes in System->Preferences->Appearance->'Visual Effects' doesn't seem to help (except when switching to no visual effects, in which case my Ctrl-Alt-Arrow functionality is restored). Also, it now seems as if I lose the title bar on my windows when switching to any mode other than 'None'. Please help me restore my settings. Thanks.

---

### Post by dstein on 2008-04-10
It seems that purging compize-core and the installing compiz-core then compiz fixed the problem.

---

