---
title: "dual screen issues"
date: 2015-06-28
forum: General Help
---

### Post by iceman30ad on 2015-06-28
ok my issue is i have 2 monitors the one on left is connected by  vga the one on right is hdmi. the hdmi is saying it is only 7 inch display  when it is a 27 inch display  and even a small  notification is taking up a huge amount of screen. is there any  way  to  get the size to reflect accurately.

---

### Post by tgalati4 on 2015-06-28
What is the make and model of your 27 inch display?  What is your graphics card?

Open a terminal and post the output of:

```
lspci | grep VGA
```

and

```
xrandr
```

---

