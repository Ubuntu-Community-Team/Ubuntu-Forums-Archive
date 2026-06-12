---
title: "Help with device driver input type"
date: 2021-02-09
forum: General Help
---

### Post by lymando on 2021-02-09
I need help editing this driver to get the ABS_X and ABS_Y to show up as a mouse0 input as opposed to part of the joystick js0 input. I thought that by defining them as ABS would do it. Any thoughts?
Here is a link to the drivers source, [guncon3.c]("https://github.com/pcnimdock/guncon3/blob/master/guncon3.c").

---

### Post by HermanAB on 2021-02-10
Uhmm... you should consult Greg Kroah-Hartman and Jonathan Corbet: [https://www.amazon.com/Linux-Device-Drivers-Jonathan-Corbet/dp/0596005903](https://www.amazon.com/Linux-Device-Drivers-Jonathan-Corbet/dp/0596005903)

---

