---
title: "qiv won't load next/previous image"
date: 2005-05-14
forum: General Help
---

### Post by 23meg on 2005-05-14
i've installed the nice image viewer app [qiv](http://www.klografx.net/qiv/) from the repositories, but when i try to view the next/previous image using a shortcut key or the mouse, it won't load it. anyone else having this problem? it doesn't report any errors on the terminal.

---

### Post by IdoMcFly on 2005-05-15
[QUOTE=23meg]i've installed the nice image viewer app [qiv](http://www.klografx.net/qiv/) from the repositories, but when i try to view the next/previous image using a shortcut key or the mouse, it won't load it. anyone else having this problem? it doesn't report any errors on the terminal.[/QUOTE]
 how do you launch qiv ?

---

### Post by 23meg on 2005-05-15
i've tried associating it with mime types, as well as launching it from the command line. it fails the same way in both.

---

### Post by IdoMcFly on 2005-05-15
associating it is not a good idea as qiv a command line util. you need to launch it like
```
qiv *.jpg
``` to allow him to go to next pic

good luck

---

### Post by 23meg on 2005-05-15
command line util? come on, it's an x app! and when i launch it with an extension  wildcard it will just accept it as a filename and display a blue blank screen with "cannot load image *.jpg" in the title bar.

---

### Post by IdoMcFly on 2005-05-15
[QUOTE=23meg]command line util? come on, it's an x app! and when i launch it with an extension  wildcard it will just accept it as a filename and display a blue blank screen with "cannot load image *.jpg" in the title bar.[/QUOTE]
 it does this when you launch "qiv *.jpg" from the command line ???

---

### Post by 23meg on 2005-05-15
exactly. i've heard of (other) problems with the packaged version with hoary from others; i'll try building from source.

---

### Post by IdoMcFly on 2005-05-15
[QUOTE=23meg]exactly. i've heard of (other) problems with the packaged version with hoary from others; i'll try building from source.[/QUOTE]
 strange, I'm using it without problem.

---

### Post by 23meg on 2005-05-15
sorry, it turned out my file extensions were messed up and perhaps that was the reason (.JPG,  vs .jpeg, vs .jpg...) i reinstalled from a debian package, and now it's behaving as you describe. but obviously, all it recognizes is images in the home folder. is there any way of making it select among all images in the folder in which the associated file resides? in other words, just using it in mime associated mode like gqview and the like?

---

