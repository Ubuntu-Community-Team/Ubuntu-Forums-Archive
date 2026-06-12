---
title: "Movies a brighter shade of green"
date: 2007-10-25
forum: General Help
---

### Post by quintok on 2007-10-25
Hi everyone,
Every movie (tried wmv, flv (in totem) and xvid) I've played today turns out green and (heavily) interlaced but not moving.  Which is weird because they all worked yesterday!  I haven't done any updating that I'm aware of.  The only package I have with codecs in it installed to my knowledge is ubuntu-restricted-extras.  I tried with VLC also and got exactly the same output as Totem.  Sound works fine however.
Thanks

---

### Post by rumli on 2007-11-04
I had a similar problem.  I was using totem-xine, and I had to edit the file: *~/.gnome2/Totem/xine_config*, and change the line:
```
#video.driver:auto
```
to
```
video.driver:OpenGL
```

---

