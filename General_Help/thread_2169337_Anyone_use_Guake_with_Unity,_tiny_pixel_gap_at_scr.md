---
title: "Anyone use Guake with Unity, tiny pixel gap at screen edge"
date: 2013-08-21
forum: General Help
---

### Post by CaptainMark on 2013-08-21
I've only just decided to give Unity another trial after pretty much the full 2 years away from it. A minor aesthetic niggle I have when using Guake is that there is a strip of maybe a couple of pixels at the sides of the screen that Guake doesn't cover, (as per screenie)
Does anyone else have this issue?

Regards
Mark

EDIT: Okay so the low quality screenshot doesn't really help, especially against a white background but basically there is a small gap of a couple of pixels at each edge of the screen that the Guake terminal doesn't cover, where anything underneath shows through

---

### Post by art_gl2 on 2013-08-25
I've solved the same problem with Guake with following steps:
1) Added Guake into ~/.config/autostart (I've got some sizing problems when starting it from gnome terminal)
2) Replaced <property name="decorated">False</property> with <property name="decorated">True</property> in /usr/share/guake/guake.glade
3) Disabled decoration for guake window in window decoration section in CompizConfig Settings Manager

Now I have no annoying one pixel gap between opened guake and launcher panel, and I'm able to resize guake window exactly to the bottom of the screen

---

