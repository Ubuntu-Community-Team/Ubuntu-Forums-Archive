---
title: "can't find gnome systray plugin"
date: 2006-11-13
forum: General Help
---

### Post by loell on 2006-11-13
hi, i was just re-arranging my panel,  i remove and add the icons i wanted.
but when i attempted to add again the previously removed systray, i can't find the systray plugin in the "Add to panel" window,
is there something i am missing here?

---

### Post by 23meg on 2006-11-13
The tray is called "Notification Area" in GNOME; maybe you're looking for the wrong name? Forgive me if systray is actually something else.

---

### Post by loell on 2006-11-13
thanks :)

 i thought notification is just a different plugin ;)

---

### Post by strabes on 2006-11-13
notification area is the correct term for that area in any OS. system tray is an incorrect term: [http://blogs.msdn.com/oldnewthing/archive/2003/09/10/54831.aspx](http://blogs.msdn.com/oldnewthing/archive/2003/09/10/54831.aspx)

just thought i would enlighten you :)

---

### Post by 23meg on 2006-11-13
The GNOME notification area, as well as the notification areas in other free desktop environments (or whatever else they're called in their respective DEs) inherits [the same freedesktop.org specification]("http://www.freedesktop.org/wiki/Standards/systemtray-spec") which does call it "tray" to begin with. H. Pennington, who wrote the spec, seems to be aware that Windows calls it "notification area", and states that the specification was inspired by KDE's decision to call it "tray". Since it's safe to assume KDE got it (inaccurately) from Windows, freedesktop.org seems to have deliberately hung on to the "incorrect" term, maybe in an effort to differentiate.

---

