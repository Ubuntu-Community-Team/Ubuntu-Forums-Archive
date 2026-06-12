---
title: "How to create an AVI from Images"
date: 2006-11-04
forum: General Help
---

### Post by Jojodi on 2006-11-04
I have a series of PPM images that I would like to put into an avi or gif. What program will allow me to take  alist of images and make them into a video with user-selectable framerate (like 5 images a sec etc)

Thanks!

---

### Post by jordilin on 2006-11-04
First of all install the package imagemagick,
then try sth like
```
convert -delay 150 *.jpg  animated.gif
```
and view the animated.gif file to see the results,
have fun

---

