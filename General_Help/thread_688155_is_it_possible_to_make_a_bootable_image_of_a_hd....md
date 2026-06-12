---
title: "is it possible to make a bootable image of a hd..."
date: 2008-02-05
forum: General Help
---

### Post by Mia_tech on 2008-02-05
I have ubuntu installed on my hd... and I want to make a bootable image and put it on a dvd.... in case things go wrong I just can boot off from the dvd, and restore the hd content... is it possible?

---

### Post by hhhhhx on 2008-02-05
it's seems possible, seeing how there are live cd's. i'd suggest that you try it and see what happens.  just my 2 cents

---

### Post by zvacet on 2008-02-05
[Here](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Mia_tech on 2008-02-08
I followed the link above to make an image of my hd, with partimage, the image was created although it took about 4hr, and then I restore it, but after rebooting the computer gives me a blank screen with a blinking cursor.....  am I missing something, I thought it was supposed to make an exact copy of my partition

---

### Post by pointone on 2008-02-08
I can't offer any help with Partimage, but I offer an alternative: the bootcd package.

```
sudo apt-get install bootcd
sudo bootcdwrite
```

... and you're done! (Of course, this is without any customization... but the defaults are sensible.)

---

