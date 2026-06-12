---
title: "X.org Reconfigure won't autodetect my graphics card or monitor any"
date: 2007-03-03
forum: General Help
---

### Post by BlkMagik07 on 2007-03-03
I just installed my new nVidia card and ran the X.org reconfiguration program when I noticed that it wouldn't detect the Graphics Card and the monitor like it did with my ATI card.  Anyone know what's going on?

---

### Post by taurus on 2007-03-03
Which command did you run?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by BlkMagik07 on 2007-03-03
Yup, I ran that one.

---

### Post by taurus on 2007-03-03
And which driver did you pick?  I recommend you pick **vesa** for now until you get X running again.  Then, you can install nVidia driver for your graphic card.

---

### Post by BlkMagik07 on 2007-03-03
I picked the driver named 'nvidia'.

---

### Post by taurus on 2007-03-03
You need to pick either vesa or nv for now and once you have installed nVidia driver, then you change the Driver to nvidia.  So, I think you should go back and reconfigure X again but this time, use vesa driver.

---

### Post by BlkMagik07 on 2007-03-03
The problem is that I have already installed the nVidia drivers so I don't know what's wrong. =\

Ubuntu has been giving me so many problems, I don't want to go back to Windows but if this keeps up I might just have too. >.<

---

### Post by taurus on 2007-03-03
Okay, let's try this one more time.

Please use vesa driver for now and once you have X running again, then reinstall nVidia driver for your graphic card.  Those are the steps that you need to take to get X running with the new nVidia card.

---

