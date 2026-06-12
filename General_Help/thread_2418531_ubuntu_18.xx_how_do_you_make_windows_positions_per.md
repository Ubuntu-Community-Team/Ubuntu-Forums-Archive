---
title: "ubuntu 18.xx how do you make windows positions persist?"
date: 2019-05-07
forum: General Help
---

### Post by jebi on 2019-05-07
hi,

this is making me pull my hair out how do i get ubuntu to remember the size and position i last had things open?

all i have found is the mutter setting to center all new windows/apps/whatever.

there must be a way to do this? i would prefer a GUI to do it or at least a simple way to do it?

why does ubuntu just open windows, apps where ever it likes? is this a gnome thing?

thx

---

### Post by TheFu on 2019-05-07
Different DE and differ WMs have different support for X/Windows geometry options.  I don't know if Wayland supports them at all.

Try this:
**uxterm  -sb -geometry 80x25+760+355**
The geometry should work on any proper X/Windows application.  That sets the location and the size for the window.

---

### Post by Claus7 on 2019-05-09
Hello,

you could check my posts about a window that I wanted to have fixed size and position. I finally managed to do it efficiently using compiz under flashback. In case you use the same DE then things will be easier for you.
[https://ubuntuforums.org/showthread.php?t=2393879](https://ubuntuforums.org/showthread.php?t=2393879)

If not, you could check the settings options specifically for the applications you are interested in, which I suppose that will be easier to handle since the window I wanted to fix I consider it a special case due to the many different rules that had to be declared in order to identify.

Regards!

---

