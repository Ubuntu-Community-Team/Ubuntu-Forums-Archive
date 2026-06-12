---
title: "&quot;window switcher&quot; tooltips...."
date: 2007-02-04
forum: General Help
---

### Post by Choad on 2007-02-04
[img]http://img50.imageshack.us/img50/1571/screenshot3rk1.png[/img]

how can i get rid of the tool tip. i would like to just have the beryl thumbnail :)

---

### Post by mayonaise15 on 2007-02-04
I second this motion.

One tip for you Choad,
You can go into the beryl settings manager, then the extras section, then window thumbnails, and if you open up the Taskbar tab in there you can check the box that says "Thumbnails Always On Top" until we can figure out a better solution.

---

### Post by Choad on 2007-02-04
[http://www.debianhelp.org/node/1777](http://www.debianhelp.org/node/1777)

not good news

nothing less than hacking the source and recompiling the window-list applet will fix this i think

---

### Post by Choad on 2007-02-04
lol im downloading the source now. you might not hear from me for quite some time, coz its likely i will bork the whole system doing this :D

edit: cant even begin to find where it sets the tooltip... i am bored of this. ill count myself lucky that everything still works

---

### Post by reclusivemonkey on 2007-02-05
> **Choad said:**
> lol im downloading the source now. you might not hear from me for quite some time, coz its likely i will bork the whole system doing this :D

edit: cant even begin to find where it sets the tooltip... i am bored of this. ill count myself lucky that everything still works

I too have been trying to do this after getting the thumbnail previews in Beryl. I think there might be a way to do it in Beryl... setting the tooltips from the panel to 100% transparency in the attributes section might work. I am going to try to remember to have a go when I get home. I use this method to set the transparency of my cairo-clock to 75% at all times.

---

### Post by reclusivemonkey on 2007-02-05
In Beryl Settings Manager, go to "Set Window attribs by various critera" and in the "Absolute Window Opacity" click on Add (the disk icon), and then choose "Window Type" from the dropdown list. Type "tooltip" in the box, and leave the slider at 0. Hey presto, the tooltips are no longer seen on the panel. Now this will probably disable some other tooltips you want, but you should be able to refine that. I'll work on that later on in the week! For now at least, I don't have those ugly-*** yellow tooltips any more! Whoopee!

---

### Post by Choad on 2007-02-05
well it disables them all as you've pointed out. it also leaves a big shadow still. :S

---

### Post by reclusivemonkey on 2007-02-05
I don't see any shadow myself.

---

### Post by cosimo on 2007-06-29
Hello guys, this might be late for you but in beryl settings manager, go to window management... Window Specific Settings... the Main tab   then the Window Opacity pull down. in the first pull down select  Window Type, in the blank space to the right of that type in   Tooltip:0   then click ok.
this will put the command in that now looks like this    w:Tooltip:0:0
this will turn off system wide tooltips including the tooltips on the window previews in the panel.
 By the way this is for Gnome since that is what I use and the   Tooltip:0 is a zero not an o.
   coz

---

### Post by d3dtn01 on 2007-07-01
Great thread. I'm annoyed by those tool tips also.  But your solution didn't work for me, even after a reboot. Any other suggestions?

---

### Post by arjones85 on 2007-10-18
Any idea how to do this with the new compiz install with gutsy? I would like to get rid of all of the annoying tool tips as well

---

