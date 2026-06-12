---
title: "maximized window ignores panel"
date: 2008-05-14
forum: General Help
---

### Post by Halsafar on 2008-05-14
- Recently installed Ubuntu Hardy. 
- Enabled the nVidia drivers
- Used nvidia-settings to setup twinview across my multiple monitors

Now here is the problem, I prefer the default gnome panel to be on the bottom.  Whenever I put the panel on the bottom any window I maximize ignores the fact the panel is there and sizes under it.  So for example the firefox status bar is behind the panel.  Now if I move the panel back to the top, everything is fine.  

I have been using Ubuntu for 3 years with gnome and always put the panel on the bottom.  The only difference now is hardy and twinview.

Any help is appreciated.

Thanks.

---

### Post by Halsafar on 2008-05-14
Should I show my xorg.conf?  Would that help in getting a reply...

---

### Post by Halsafar on 2008-05-14
Okay going to Appearance -> Visual Effects -> None
This fixes it immediately.  Now a maximized window stops at the top of the panel, as it should.

Enabling even the most basic of compiz seems to cause it.  I cannot figure out which component.  I used the Preferences -> Advanced Desktop Effects Settings to disable every component and it still was occuring.

So no compiz I guess.

---

### Post by sdennie on 2008-05-14
One thing you could try would be to start up System->Preferences->Advanced Desktop Effects Settings and going to General Options->Focus and Raise Behavior and setting Focus Prevention Level to "low" (that's what I'm using at least).

---

### Post by jbor7755 on 2008-05-18
I have the same problem (although my gnome bar is at the top of screen).  But before yesterday the firefox window had functioning fine. Now i have to hit View -> Fullscreen and then use the now visible resize button to resize the window. Not really an acceptable fix (especially considering it was working yesterday without this run-around).

I tried
System -> Preferences -> Appearance -> Visual Effects, None 
and this also fixes the problem but removes all desktop effects (which, i have to admit, are nice) and so isn't really an acceptable fix either.

One thing I did do yesterday (the only thing I can think of which may have had an effect) was to enable laptop-mode in order to force some different hard disk management settings (due to a fast increasing load cycle count on my near new Dell laptop).

Could this have something to do with it???

---

