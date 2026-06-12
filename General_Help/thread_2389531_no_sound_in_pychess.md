---
title: "no sound in pychess"
date: 2018-04-18
forum: General Help
---

### Post by pnyiaart on 2018-04-18
i am using lubuntu 17.10 legacy version , i installed pychess from terminal and also installed restricted extras but still i hear no sounds in pychess , what needs to be done ?

---

### Post by again? on 2018-04-18
What is "legacy version"?
FYI pychess sounds work here in Xubuntu 17.10.

---

### Post by howefield on 2018-04-18
Do you have the two packages "*gir1.2-gstreamer-1.0* and *gir1.2-gst-plugins-base-1.0*" installed ?

---

### Post by pnyiaart on 2018-04-18
> **guber2 said:**
> What is "legacy version"?
FYI pychess sounds work here in Xubuntu 17.10.

the alternate 32 bit iso , it is even smaller .

> **howefield said:**
> Do you have the two packages "*gir1.2-gstreamer-1.0* and *gir1.2-gst-plugins-base-1.0*" installed ?

```
sudo apt-get install gir1.2-gstreamer-1.0 gir1.2-gst-plugins-base-1.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gir1.2-gst-plugins-base-1.0 is already the newest version (1.12.3-1).
gir1.2-gstreamer-1.0 is already the newest version (1.12.3-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

---

### Post by pnyiaart on 2018-04-20
any other solutions ?

---

### Post by pnyiaart on 2018-04-25
bump

---

