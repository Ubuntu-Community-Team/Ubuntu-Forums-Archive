---
title: "Ubuntu / Kubuntu Splashscreen"
date: 2006-12-12
forum: General Help
---

### Post by clucas on 2006-12-12
Had installed Ubuntu 6.10. Then I wanted to mess with Kubuntu. Why is it that when I start up the Kubuntu screen appears and not the Ubuntu screen. I mean it's the screen that appears before I sign in. After I sign in (I use Ubuntu as the default) the Ubuntu screen appears. When I shut down, the Ubuntu screen appears. Hope I phrased the question correctly.

---

### Post by talbain on 2006-12-13
yeah, im having the same ... "problem" if you find our how to fix it let me know :p

---

### Post by tragicglee on 2006-12-13
I'd link you to the info but I failed to bookmark it when I needed it after running into a similar prob. I  did write it down though >> you can type the following to configue the splash artwork after it changes due to adding desktop environments or updating the kernel

```
sudo update-alternatives --config usplash-artwork.so
```

and this will build your choice into the intramfs. 

```
sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by clucas on 2006-12-14
That did it!

Thanks!

---

