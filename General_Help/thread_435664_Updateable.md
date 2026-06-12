---
title: "Updateable?"
date: 2007-05-07
forum: General Help
---

### Post by Flavian on 2007-05-07
I have installed beryl through a HOWTO posted in the "Tips & Tricks" section.
I can not find it anymore though, through the search. I remember that the one who made the howto said that one should NOT update Beryl through the ubuntu repos because it brakes Beryl! (I think there was a bug in it or something...) So my question is, is it NOW safe to update or will the packages in the normal ubuntu repo brake beryl ?

Thanks for any help:
Ps: I don't have hybernate, and shutdown buttons in system -> shutdown, I remember there being a solution for that in the same thread and I can't find it anymore. Can someone maybe help me with that little issue as well? :)

---

### Post by Flavian on 2007-05-08
Is there really NO ONE who knows that? :-k

---

### Post by mcduck on 2007-05-08
The package in Ubuntu repositories doesn't work if you are using XGL, but otherwise it should not be a problem.

For the shutdown buttons, if you are using XGL, you need to modify the XGL start script to something like this:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

---

### Post by Flavian on 2007-05-09
Thank you for your answer :)
Yes, I am using XGL.
Is there any chance that it will work when the next update comes? - Cause at some point I'd like to update :(

Thanks in advance.
Florian

---

