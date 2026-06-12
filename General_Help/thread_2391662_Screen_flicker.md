---
title: "Screen flicker"
date: 2018-05-11
forum: General Help
---

### Post by jeo7 on 2018-05-11
I am running Ubuntu 18.04 on a laptop with AMD Radeon R7 series integrated graphics, and I am having all sorts of problems with the video driver. I thought I had it solved, but other problems popped up and I had to return to the default Ubuntu drivers.

One problem I am dealing with is a screen flicker. It's not all the time and one might say it is relatively rare, but not so rare that it doesn't drive me nuts. Is there anything that can be done to correct it?

Thanks.

---

### Post by helotbc-0 on 2018-05-12
I'm experiencing flicker as well. The frequency is about every 5 sec. It does not matter the brightness of the screen. I am running a Lenovo Yoga 720 with a Intel® UHD Graphics 620 (Kabylake GT2). - Thanks

---

### Post by jeo7 on 2018-05-12
> **helotbc-0 said:**
> I'm experiencing flicker as well. The frequency is about every 5 sec. It does not matter the brightness of the screen. I am running a Lenovo Yoga 720 with a Intel® UHD Graphics 620 (Kabylake GT2). - Thanks

Whoa! My flickering is about once every one or two minutes. Every 5 sec would drive me batty.

Since I posted this, I found the following on the internet which might have solved my problem but the jury is still out. Try:

1. Gmome Tweaks ---> Appearance ---> Turn off animations  (Gnome tweaks is software you can get in the software center.)

2. ```
sudo g3dm -reset
```

---

### Post by jeo7 on 2018-05-12
Ok, I spoke too soon. I still have the screen flicker, but it seems to be less prominent and it only happens when the mouse is in motion.

---

