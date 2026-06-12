---
title: "msttcorefonts terribly pixelated"
date: 2008-05-12
forum: General Help
---

### Post by dmsuperman on 2008-05-12
The best explanation involves pictures, so here they are:
[[IMG]http://img301.imageshack.us/img301/3862/screenshotbuddylistvd2.th.png[/IMG]](http://img301.imageshack.us/my.php?image=screenshotbuddylistvd2.png)
[[IMG]http://img183.imageshack.us/img183/9310/screenshotubuntuforumsmto8.th.png[/IMG]](http://img183.imageshack.us/my.php?image=screenshotubuntuforumsmto8.png)

The first one is of Pidgin, which uses my system fonts (Gentium and BitStream Charter).
The second is Firefox. In the page is the ubuntu forums, which use such fonts as Verdana, Tahoma, and Times New Roman. Any application that uses such fonts (ones from the msttcorefonts package) render them terribly pixelated. I've tried every patch, hack, mod, and tweak you can think of, and it doesn't fix it. I've tried without and without subpixel smoothing, and with and without full hinting. The really odd thing is, this started out of nowhere the other day. The only thing I can think of that may have caused this is me upgrading to FreeType, but I'm pretty sure they were around different times. I had to update FreeType to 2.2.0 for a requirement for an application, which then broke all other applications (because they changed the API in that release, not too intelligent). I then updated to 2.3.5.

I'm using CRT monitors, so that's not the issue. Can anybody help me figure this issue out?

---

