---
title: "Mouse pointer problems when dragging photos"
date: 2015-01-31
forum: General Help
---

### Post by neilajarn on 2015-01-31
Got a weird problem with an old Dell Inspiron 1545 laptop that I recently installed Xubuntu on for my cousin.

Apperently, when dragging and dropping a photo within Thunar the mouse pointer changes to a thumbnail view of the photo and won't change back even after the file has been copied. The only resolution is to restart.

Presumably this is a problem with the graphics driver, am going to take a look at it tomorrow. 

Anyone else had this problem ?

---

### Post by bapoumba on 2015-01-31
Well, not exactly. Sometimes when I click and drag by accident, I get 2 mouse pointers next to each other, or a thumbnail as you describe. It does not appear on a screenshot. Locking and unlocking the screen reverts the mouse pointer back to normal. Intel video, I have looked around but not found anything relevant.

---

### Post by neilajarn on 2015-02-01
Thanks, that'll have to do for now because there's nothing in Additional Drivers with regards to graphics drivers.

---

### Post by bapoumba on 2015-02-01
No additional drivers here either. Is this an Intel video chip ?
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by neilajarn on 2015-02-01
Yep :
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by bapoumba on 2015-02-01
[https://bugs.launchpad.net/unity/+bug/1379499](https://bugs.launchpad.net/unity/+bug/1379499)
If you have a look at the attachment in post #8, this is exactly what I see (without the thumbnail or half thumbnail, but the two mouse pointers).

---

