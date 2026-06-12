---
title: "sort images by dimensions in nautilus"
date: 2007-12-16
forum: General Help
---

### Post by jimmy the saint on 2007-12-16
I would like to sort a folder of images by dimensions.  I figure that if i can enable a column like that it would be cool.  If nautilus cant do it, does anyone know of similar file manager that can?

Thank You for any suggestions!

---

### Post by @)--',------- on 2008-05-07
I need this feature as well. I have not found a way to do this.  This is a common feature in OS X and Windows XP, Vista.

---

### Post by @)--',------- on 2008-05-12
I still have not found a solution. I would like to batch process a series of images (I use phatch) to maximum width and height of 500 x 500, or add canvas to equal those dimensions, but I do not want to process any images that are already 500 x 500. If I could sort by dimension, it would make this task very easy.

---

### Post by Mr A Mouse on 2008-05-12
I'm afraid you may have to write a script that checks the dimensions before it hands them off to phatch. This is not a function that I know of in Nautilus.

---

### Post by stylishpants on 2008-05-14
You could use the "imageinfo" program to print the geometry of each image, and sort on that.

```

fraser@ged:/data/avatars$ for f in *; do imageinfo --geom "$f"; echo -e " \t$f"; done | sort -n
127x130 	jeremy2.gif
130x130 	doqmqe.jpg
150x112 	brombor6gh.jpg
150x135 	skeletonrt5.jpg
150x150 	lc-bear.jpg
163x153 	dancebear.gif
170x229 	bob_carolgees.jpg
240x200 	sachabaroncohen_borat_240_001.jpg
303x404 	02.jpg
420x319 	Angel5x1.jpg


```

You could also use the "identify" program in the imagemagick package to print image data, but it seems much slower and more verbose.

---

