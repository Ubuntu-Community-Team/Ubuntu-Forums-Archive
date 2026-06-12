---
title: "Converting a ps file to an image files (jpg, png, svg)?"
date: 2006-10-22
forum: General Help
---

### Post by brynjarh on 2006-10-22
What software can convert a ps(post script) file into an image? jpg, png and svg.

---

### Post by uncreative on 2006-10-22
can you open it up in a pdf viewer and take a screencap?

---

### Post by metalheart on 2006-10-22
Ghostscript. You have it in your system.

```
gs -dBATCH -sOutputFile=myfile.jpg -sDEVICE=jpeg myfile.ps
```

should work.

---

