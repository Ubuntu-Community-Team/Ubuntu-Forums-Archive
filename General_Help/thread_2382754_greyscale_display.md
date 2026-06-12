---
title: "greyscale display"
date: 2018-01-17
forum: General Help
---

### Post by Old Jimma on 2018-01-17
Hi Ubuntu Community:

I'm 66 and I've been with Ubuntu since Hoary Hedgehog.... I learned that among the things that keep me glued to my monitor is its dazzling color: color grabs our attention and it is hard to shake loose from it.

**I want my life back so that I can spend time more meaningfully.**

There have been recent articles in the popular medial of switching phone monitors to GREYSCALE so that people can begin to break from cell phone addiction.

How can I easily get GREYSCALE for my Ubuntu display so that I can switch to color when I want.... for example, when I want to look a color photos?

Thank you,

Old Jimma from the Old Country

---

### Post by dragonfly41 on 2018-01-17
Seems that the tips here on using Unity Tweak Tool (post #3)
[https://askubuntu.com/questions/452935/how-to-change-theme-colors](https://askubuntu.com/questions/452935/how-to-change-theme-colors)
might come close to meeting your requirements.

For example ... [http://www.ravefinity.com/p/download-ambiance-blackout-colors.html](http://www.ravefinity.com/p/download-ambiance-blackout-colors.html)

---

### Post by again? on 2018-01-17
If you have an nvidia card using proprietary drivers you can lower digital vibrance.
```
nvidia-settings --no-write-config --assign DigitalVibrance=-1024
```

Revert to normal colour...
```
nvidia-settings --load-config-only
```

---

