---
title: "Rendering issue with transparent text"
date: 2008-05-25
forum: General Help
---

### Post by eduardosd on 2008-05-25
Hello,

Since Gutsy (currently I run Hardy) I've been having a problem with text rendering in some programs.  It seems to happen when a text is to be painted either (a) against a transparent background, or (b) with a transparent (foreground) color [not so sure about this one].  In the first situation, the characters are painted correctly, but the background of the bounding boxes of each letter are painted with a solid color (overriding the transparent background). This is especially noticeable in Compiz's "improved Alt-Tab", as seen in this image:

[[IMG]http://img147.imageshack.us/img147/7704/alttabjv0.th.png[/IMG]](http://img147.imageshack.us/my.php?image=alttabjv0.png)

In the second situation, the text cannot be read at all, because the whole bounding boxes of each letter are painted (instead of just the letter shapes). You can see three screen shots of it:

[[IMG]http://img384.imageshack.us/img384/4765/resolucaoci3.th.png[/img]](http://img384.imageshack.us/my.php?image=resolucaoci3.png) [[IMG]http://img384.imageshack.us/img384/3391/elisawt2.th.png[/img]](http://img384.imageshack.us/my.php?image=elisawt2.png) [[IMG]http://img210.imageshack.us/img210/1980/resizefv6.th.png[/img]](http://img210.imageshack.us/my.php?image=resizefv6.png)

I didn't check this thoroughly, but it seems that this only occurs for applications painted by Cairo (if I switch to KDE and load transparent applets in SuperKaramba, for instance, there is no such effect). It doesn't happen either if I make a window transparent using Compiz (Alt + mouse scroll). Anyway, it must have something to do with my video card: it's an onboard Intel 82945G (using the 'intel' X driver).

Could anybody give any directions here? Is there anything I can do that doesn't require waiting for somebody to fix the driver (or fixing it myself)? :)

Thanks!

---

