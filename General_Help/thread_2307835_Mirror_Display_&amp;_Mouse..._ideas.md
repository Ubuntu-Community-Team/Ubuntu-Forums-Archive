---
title: "Mirror Display &amp; Mouse... ideas?"
date: 2015-12-28
forum: General Help
---

### Post by clalian on 2015-12-28
Hello everyone,
Any idea if I could "mirror" my monitors?
So they display as if I was looking at them from behind?  
  
Then to match, any way to "flip" the pointing device (mouse/trackball) on its x-axis?

Thank you!

---

### Post by clalian on 2016-01-03
Just bumping this...
Any idea if this is possible?

Invert the image left-to-right,... and the mouse?

---

### Post by clalian on 2016-01-17
Hello,
Giving a bump here.
Any thoughts if this is possible?

---

### Post by Autodave on 2016-01-17
What graphic card are you using? Do you have any display drivers installed other than what installed w/ubuntu?

---

### Post by clalian on 2016-01-17
Hello Autodave,
Thank you for the reply!

The video card I have is:
```
*-display               
   description: VGA compatible controller
   product: GT218 [GeForce 210]
   vendor: NVIDIA Corporation
*-display
   description: VGA compatible controller
   product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
   vendor: Intel Corporation
```

I obtained that by running
```
lshw -c video
```
Another option I saw was:
```
lspci -v | less
```

I am running two displays... yet I will happily switch to one if this means getting the "mirror display" up and running.

Any thoughts?

Thanks again!

---

### Post by clalian on 2016-01-23
Hello,
Bumping this question.

If need be, I have a laptop I can use (so only one video card).

---

### Post by clalian on 2016-01-29
Hello,
Any thoughts if I would modify the video drivers to "mirror" the display?
Or would it be at the X11 level?

---

### Post by clalian on 2016-01-29
Found this:
[http://askubuntu.com/questions/19936/how-can-i-mirror-flip-display-output](http://askubuntu.com/questions/19936/how-can-i-mirror-flip-display-output)

---

