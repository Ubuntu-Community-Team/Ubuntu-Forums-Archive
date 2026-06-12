---
title: "Save for web"
date: 2005-05-08
forum: General Help
---

### Post by art on 2005-05-08
Hi forum
Anyone knows an application which reduces the size of the image, like the Photoshop's "Save for Web" feature. I installed the ImageMagick but can't find how to reduce the size of the image ](*,) . 
Thanks a lot.

---

### Post by tread on 2005-05-08
I can't speak about Imagemagick, but in Gimp, when you save as a jpeg, you get an option to choose quality, and the size and the image are updated realtime so you can decide when you have the correct balance of quality and size.

---

### Post by Professor X on 2005-05-08
[QUOTE=art]Hi forum
Anyone knows an application which reduces the size of the image, like the Photoshop's "Save for Web" feature. I installed the ImageMagick but can't find how to reduce the size of the image ](*,) . 
Thanks a lot.[/QUOTE]
 Well you can do this with the gimp, but that's a bit overkill.  Imagemagick is a great app for manipulating images.  Install it by using 'sudo apt-get install imagemagick'.  Then use the mogrify option at the console to resize your image:

```
mogrify -geometry 50x50 picture.jpeg
```

---

### Post by art on 2005-05-08
Wow, great!!!
I don't know how I missed this one, I think I have tried it... Anyway... 
Thanks a lot!!!

---

