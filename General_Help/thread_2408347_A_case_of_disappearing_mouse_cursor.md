---
title: "A case of disappearing mouse cursor"
date: 2018-12-17
forum: General Help
---

### Post by jgw on 2018-12-17
My mouse cursor sometimes just goes away.  However, if I move the mouse to either the top, or bottom of the page (when this happens) it appears again.  I can, for instance, have the mouse cursor in the dock and then move it to the browser or even background and it will mysteriously go away again.  If I do that several times it will, eventually, reappear.  There is nothing I am doing special when this happens.  Sometimes I can actually press control key and it will show me where the invisible mouse is, then, again, sometimes not.  In other words there seems to be nothing consistent with this thing at all.  I have checked other postings on this and they all seem to be about a year old.  

I should also mention that I cannot change my cursor size on this machine.  I have another machine where I can and another that allows size change sometimes.  The settings on all are the same. (have no idea if this has anything to do with anything):
Theme:                         radiance
Cursor:                         red glass
Icons:                           gnome
I have messed with these to exhaustion.  My available Themes are: adwaita, radiance, ambience and high contrast

Thank you....................

---

### Post by #&amp;thj^% on 2018-12-17
@jgw give this a shot:
```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```
EDIT: _This may not not work if you are running a wayland session_ so you will have to login under a X11 session.

---

### Post by jgw on 2018-12-19
Thanks for reply!

Did as you suggested.  I haven't had the cursor go away but it, apparently did something as there was no error, no notification, just went back to the terminal prompt so I guess I will see in the fullness of time.  One thing that did happen is that my cursor changed color from red to black and then shrunk itself so its barely seeable.  This is an ongoing problem and, I think, a firefox problem.

---

### Post by mawex on 2018-12-19
This was really helpful for me, had same issue and tried the same thing, got lucky. Thank you.

---

### Post by jgw on 2019-01-04
What its doing now is repeatable on all my machines (I have 4).  Whilst in Firefox my cursor is a tiny black cursor irregardless of any settings I can find.  When, however, I move the cursor out of firefox, say, to the top line or to the dock on bottom of screen the cursor goes to a larger sized redglass cursor.  I cannot figure out how to resize either cursor.   (settings doesn't do it)

---

