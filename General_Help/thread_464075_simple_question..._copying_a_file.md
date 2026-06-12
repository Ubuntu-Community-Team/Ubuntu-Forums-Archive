---
title: "simple question... copying a file"
date: 2007-06-04
forum: General Help
---

### Post by vj air on 2007-06-04
i need to copy this file    **mjpegtools.pc**        from this folder  **/home/vj/Desktop/mjpegtools-1.9.0rc2**

to this folder    **/usr/local/lib/pkgconfig**  but the destination folder is not letting me paste in to it. how do i do it via the terminal? (im assuming id need to put sudo in front of it?)

---

### Post by Ub1476 on 2007-06-04
```
cd /home/vj/Desktop/mjpegtools-1.9.0rc2
sudo cp mjpegtools.pc /usr/local/lib/pkgconfig

```

---

### Post by taurus on 2007-06-04
> **vj air said:**
> i need to copy this file    **mjpegtools.pc**        from this folder  **/home/vj/Desktop/mjpegtools-1.9.0rc2**

to this folder    **/usr/local/lib/pkgconfig**  but the destination folder is not letting me paste in to it. how do i do it via the terminal? (im assuming id need to put sudo in front of it?)

Use

```
gksudo nautilus
```
or
```
sudo cp /home/vj/Desktop/mjpegtools-1.9.0rc2/mjpegtools.pc /usr/local/lib/pkgconfig
```

---

### Post by vj air on 2007-06-04
cheers, its done :)

---

### Post by vj air on 2007-06-04
what does the **nautilus** command do in taurus's method?

---

### Post by ajgreeny on 2007-06-04
It just opens nautilus as root for that particular usage of the program.  Next time it will be user only again.  **gksudo** is the same as **sudo** but should be used for gnome programs, for kde programs it's kdesu instead.  **sudo** is only for terminal utilities, such as nano or vi, etc.

---

