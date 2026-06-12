---
title: "Firefox addon Issue.  please help!"
date: 2007-05-27
forum: General Help
---

### Post by mmilitia9 on 2007-05-27
Hello all.  


I've posted here and Mozilla forums looking for an answer about these 2 extensions I have that don't want to open up there preferences for me.

Map This
Tab Mix Plus

I've installed them.  They work.  But when I want to go configure there preferences though Tools>Addons>Map This or Tab Mix Plus and click the "Preferences button".. Nothing happens.  Every other extension that has a preference works but these 2.  

The weird part is... I was just messin around seeing if it would work one last time.. and Map This opened for me and I got a chance to configure it.. Sadly, I didn't have tab mix plus installed so I couldnt get to that in time. So, after I restarted firefox I went to Addons again and tried to configure Tab mix plus.. It didn't open.  I clicked preferences for Map This.. didn't open.. but everything else still does..

I've uninstalled the extensions and reinstalled.  I've saved them to the desktop and manually dragged them into the addon dialog.. That didn't work either.

Anyone got any suggestions? 

Thanks!

Dominick

---

### Post by spin2cool on 2007-05-27
It's probably two extensions that don't play nice with each other, or that have somehow corrupted your profile.  The first step is to run 'firefox -p' and create a clean profile  Then install the extensions one at a time to see if you can figure out what the problem is.

---

### Post by mmilitia9 on 2007-05-27
I have the same set up in Windows.  But does that matter anyway?

---

### Post by spin2cool on 2007-05-27
Extensions are notorious for having all kinds of little quirks, because anyone can submit one and they aren't tested to the same degree that the base firefox build is.  TabMix, in particular, used to be legendary for causing problems (though in all fairness, it's been quite a while since I tried to use it).   It possible that a problem might manifest itself in linux that didn't show up in windows, but it all depends.

Regardless of what OS you're in, starting from a clean profile while you isolate the problem is the best way to figure out what's causing the problem and ultimately fix it.

---

