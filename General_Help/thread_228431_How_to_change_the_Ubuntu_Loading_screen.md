---
title: "How to change the Ubuntu Loading screen"
date: 2006-08-03
forum: General Help
---

### Post by cantormath on 2006-08-03
Does anyone know where Ubuntu loading screen, the orange and black screen image, is?  I want to change it up, but I can find it.  I know its there, help :-D

---

### Post by ciscosurfer on 2006-08-03
I like the [Serengeti Splash]("http://www.ubuntuforums.org/showthread.php?t=185538").  After you follow the directions, you can find your various usplash's under /usr/lib/usplash and can be changed via
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by cantormath on 2006-08-03
> **ciscosurfer said:**
> I like the [Serengeti Splash]("http://www.ubuntuforums.org/showthread.php?t=185538").  After you follow the directions, you can find your various usplash's under /usr/lib/usplash and can be changed via
```
sudo update-alternatives --config usplash-artwork.so
```

Thanks,

I like the serengeti splash as well.  
I was also wondering what I can use to open and or edit the .so files?

---

### Post by cantormath on 2006-08-03
I found a tutorial

[http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835)

---

### Post by frodon on 2006-08-03
If you wish you can try gfxboot instead of grub : 
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

---

### Post by cantormath on 2006-08-03
> **frodon said:**
> If you wish you can try gfxboot instead of grub : 
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

Thanks,

I will try it. Does gfxboot use more or less resources? What are the advantages beyond it looking cooler. Thanks again.

---

### Post by josys36 on 2006-08-04
Run both of these and you will be fine.

sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)

Both have to be ran otherwise the change you make with step one will not take effect.

Thanks!

Jason

---

