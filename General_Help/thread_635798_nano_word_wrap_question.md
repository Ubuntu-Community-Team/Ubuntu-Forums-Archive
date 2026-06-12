---
title: "nano word wrap question"
date: 2007-12-09
forum: General Help
---

### Post by jointstereotype on 2007-12-09
Here's one for all you nano gurus: Is there wrap-to-screen option in nano, one that doesn't actually modify the text? I like the idea of using nano fullscreen (less clutter, fewer distractions, etc.), but I don't like the way nano's standard wrapping options add line breaks to the text.

---

### Post by dagnabit dang doohickey on 2007-12-09
You can disable the text wrap by running nano with the -w option:
```
nano -w *filename*
```
To set this behavior as a default, add the following line to your ~/.nanorc file:
```
set nowrap
```

As for keeping the text wrap sans the line break, I don't think that's possible.

---

### Post by jointstereotype on 2007-12-09
> As for keeping the text wrap sans the line break, I don't think that's possible.

That's a shame. gedit does this, although it doesn't have a full screen mode. I do like gedit's Oblivion color scheme, though, so I guess I'll stick with that for now.

Thanks anyway. :)

---

