---
title: "Slow text editing and refresh in browsers"
date: 2007-02-24
forum: General Help
---

### Post by Engel81 on 2007-02-24
When I write in text boxes, such as this one or even search engine fields, my cursor lags when I move it with the arrow keys ie I'll write a sentence, then move along with th arrow keys, and I get see |||||| all through my text. It eventually disappears but it is obviously very annoying. Basically text boxes are really slow. Any suggestions?

My default browser is Firefox, but I get the same problem when I use Epiphany and Mozilla. Is this a Java problem?

My apologies if this problem has been already discussed. BTW 'm running EE (though I had the same problem with Dapper) on a fairly new laptop with 1 Gig of RAM.

---

### Post by taurus on 2007-02-25
I think it is your graphic card.  You need to install a driver for your graphic card and what is it anyway?

---

### Post by Engel81 on 2007-02-25
Good point. It's a128 MB Nvidia 6200, which means, I believe, it steals some memory from the RAM.

---

### Post by taurus on 2007-02-25
In that case, you need to install nVidia driver for your card so Gnome would run smoothly.

Here's a guide.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Engel81 on 2007-02-25
Thanks. That worked. Strange. I thought I had installed the drivers with Easy Ubuntu.

---

### Post by ofek on 2007-02-25
Thats probably the most annoying problem with the nv driver and the only reason why i use nvidia's property drivers =/ hope they will decide to fix it some day.

---

### Post by TimJBart on 2007-02-27
Am I right in saying that envy installed my graphics driver for me when I ran it?  I am experiencing similar slowness in ubuntu.  Using back button in FF is slow for me as is browsing through folders.  But I installed envy so dont think it can be the graphics drivers.

---

### Post by taurus on 2007-02-27
You need to run envy to install a driver for your graphic card.  Installing envy by itself will not do anything.  Post the output of this command from a terminal?

```
cat /etc/X11/xorg.conf
```

---

