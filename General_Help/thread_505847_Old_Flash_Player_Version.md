---
title: "Old Flash Player Version?"
date: 2007-07-20
forum: General Help
---

### Post by sixfoottallrabbit on 2007-07-20
Hey,

So I just updated my Flash Player to version 9. That all seemed to go ok, but still, I get a plethora (including now even Youtube) of websites telling me that I have either Javascript turned off or an older version of flash player. Neither of those are true! I think the fault may lie, however, in something else.

If I check my "about:plugins" page on firefox, I can see TWO entries for Shockwave Flash.

The first one says:
    File name: libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

The second one says:
    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

The second one seems to the be the correct one. Or maybe I'm wrong and they're just different things. But if I have two different versions installed, could it be mistaking one version for another?

Any idea about what I could do?
Thanks.

PS. Ubuntu Feisty Fawn, using Firefox 2.0.0.5

---

### Post by kevinlyfellow on 2007-07-20
I think you do have an old version installed.  Plugins for firefox are found in /usr/lib/firefox/plugins  Take a look in there and see if you have more than the necessary number of flash plugins

---

### Post by sixfoottallrabbit on 2007-07-20
I have both of those two files I mentioned earlier in that folder.

I have also noticed since I tried to update to version 9, that when I try to view any flash video, Firefox just suddenly closes.

Should I delete one of those plugin files?

---

### Post by fragos on 2007-07-20
I'd remove the 1st one.  As a precaution you could move it to another directory rather than deleting it.

---

