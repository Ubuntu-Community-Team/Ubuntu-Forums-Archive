---
title: "Viewing .PS files"
date: 2007-06-19
forum: General Help
---

### Post by ubuntuubuntu on 2007-06-19
Can someone indicate me a program for viewing .ps files? I'm using Evince, which came in Ubuntu, but I don't like it. It makes the document look strange.

---

### Post by yabbadabbadont on 2007-06-19
Ghostview

Edit: OK, that isn't a real package in Ubuntu...  Try one of these instead ```
/media/music/Flac/Various $ aptitude show postscript-viewer 
No current or candidate version found for postscript-viewer
Package: postscript-viewer
State: not a real package
Provided by: bmv, evince, evince-gtk, gnome-gv, gs-afpl, gs-esp, gs-gpl, gv, kghostview

```

(the "Provided by" list)

---

### Post by kuja on 2007-06-19
kghostview works well.

---

### Post by Kent84 on 2007-06-19
When I first installed Ubuntu I found that the fonts in the PS files did look strange in evince. But after I installed ghostscript, which I presumed also installed better/working fonts, openning PS files in evince looked fine.

---

