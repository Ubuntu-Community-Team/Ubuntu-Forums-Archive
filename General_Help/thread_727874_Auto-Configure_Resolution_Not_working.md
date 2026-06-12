---
title: "Auto-Configure Resolution Not working"
date: 2008-03-18
forum: General Help
---

### Post by PongApp on 2008-03-18
When I log into Ubuntu (7.10) it auto-detects my monitor as a 800x600 where my monitor is actually a 1440 x 900. I need some help fixing this. I tried editing usplash.conf but it did nothing and my monitor isnt on the lsit of monitors that you can choose from Screens and graphics. Is there a way to add my monitor to the lsit? When I choose Generic > 1440 x 900 (and check widescreen) it doesn't work either. I can only get it to go up to 1280 x 1024 and the screen hangs off to the elft leaving a black box on the right. Thank you very much.
-Pong

---

### Post by taurus on 2008-03-18
What kind of graphic card do you have on your machine and have you installed a driver for it?

---

### Post by Ub1476 on 2008-03-18
As taurus says it's obviously a driver problem.

Here's how you can see how Ubuntu recognize your graphic card:

```
lspci | grep VGA
```

---

