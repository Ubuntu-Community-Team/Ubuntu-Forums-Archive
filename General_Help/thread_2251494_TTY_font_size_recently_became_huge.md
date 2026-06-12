---
title: "TTY font size recently became huge"
date: 2014-11-04
forum: General Help
---

### Post by Tristan_Williams on 2014-11-04
The font size in TTY1-6 recently became so huge that it only displays 25 lines. It used to display around 60 lines.

How can I change it back so that the font isn't ridiculously huge?

---

### Post by sudodus on 2014-11-04
Did you switch to a proprietary graphics driver? Or can you remember changing something else related to graphics or grub (booting)?

-o-

See this link for control of the graphics during booting:

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

```
***#GRUB_TERMINAL=console*** 
...
***#GRUB_GFXMODE=640x480*** 

```

---

### Post by Tristan_Williams on 2014-11-04
> **sudodus said:**
> Did you switch to a proprietary graphics driver? Or can you remember changing something else related to graphics or grub (booting)?]

Yes, I am using Nvidia-331-updates as the graphics driver.

---

### Post by sudodus on 2014-11-05
It is also my experience that nvidia proprietary drivers cause the text screen to get 'big' text (80 columns x 25 lines). I don't know any way to avoid it (except to use nouveau, and lose the advanced features of the nvidia proprietary driver). [COLOR=#696969]Maybe someone else can give us a tip ...[/COLOR]

---

