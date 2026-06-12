---
title: "Teaching Ubuntu to produce thumbnails"
date: 2008-05-06
forum: General Help
---

### Post by csoler on 2008-05-06
Hi there,

Is there any way to teach Ubuntu to produce thumbnails for a given file format which is not known yet ?

For instance I'm using OpenEXR ([http://www.openexr.org](http://www.openexr.org)) images, and these are only displayable using the appropriate tool, and certainly not displayed as thumbnails in nautilus but only as data files. I do have a program to convert these files into thumbnails, but how to tell my beloved Ubuntu to use it ?

Thanks!
Cyril

---

### Post by roaldz on 2008-05-06
> **csoler said:**
> Hi there,

Is there any way to teach Ubuntu to produce thumbnails for a given file format which is not known yet ?

For instance I'm using OpenEXR ([http://www.openexr.org](http://www.openexr.org)) images, and these are only displayable using the appropriate tool, and certainly not displayed as thumbnails in nautilus but only as data files. I do have a program to convert these files into thumbnails, but how to tell my beloved Ubuntu to use it ?

Thanks!
Cyril

Maybe you could use nautilus-scripts/nautilus-actions? If your tool is a commandline tool, it´s not so hard.
[http://g-scripts.sourceforge.net](http://g-scripts.sourceforge.net),
[nautilus-actions]("apt:nautilus-actions")

---

### Post by csoler on 2008-05-06
> **roaldz said:**
> Maybe you could use nautilus-scripts/nautilus-actions? If your tool is a commandline tool, it´s not so hard.
[http://g-scripts.sourceforge.net](http://g-scripts.sourceforge.net),
[nautilus-actions]("apt:nautilus-actions")

Maybe you misunderstood me: what I need is to have nautilus automatically produce little preview images for files of type OpenEXR, just as he does for .jpeg images (using convert I guess). For now, it only displays an icon which does not reflect the content of each image specifically.

---

