---
title: "Intel HD Graphics 2000, two resolutions (VGA and DVI)?"
date: 2013-12-31
forum: General Help
---

### Post by frank18 on 2013-12-31
Hi guys: i have ubuntu12.04LTS and i have Intel integrated hd VGA and
DVI outputs and I'd like to get on VGA monitor 1024x768 and on DVI  output 1920x1080 resolutions at same time, is there anyway i can have  separate resolution besides the Mirror display resolutions?thanks and  have an Happy New Year.

---

### Post by mörgæs on 2014-01-01
Which screen card are you using?

---

### Post by frank18 on 2014-01-01
> **mörgæs said:**
> Which screen card are you using?

Thanks mogaes: it's a lenovo thinkCenterM71e 3167  I5 CPU and Integrated Graphics Adapter (Intel HD                                        Graphics 2000)

---

### Post by mörgæs on 2014-01-02
Please post the output of
```
xrandr -q 
```
in CODE tags.

---

### Post by frank18 on 2014-01-02
> **mörgæs said:**
> Please post the output of
```
xrandr -q 
```
in CODE tags.

Thanks;here  a screenshot, thanks

---

### Post by chkneater on 2014-01-02
Arandr, which is a graphical Xrandr, might be easier to use to get seperate resolutions.  It will also allow you to clone the desktops or have seperate desktops.

---

### Post by frank18 on 2014-01-02
> **chkneater said:**
> Arandr, which is a graphical Xrandr, might be easier to use to get seperate resolutions.  It will also allow you to clone the desktops or have seperate desktops.


[B]Thanks bro: but Arandr  seems not to work in ubuntu!
[/B]

---

### Post by mörgæs on 2014-01-03
[http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/](http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/)

---

### Post by chkneater on 2014-01-03
> **frank18 said:**
> [B]Thanks bro: but Arandr  seems not to work in ubuntu!
[/B]

I had probs with Arandr for a while, I remember it said something to the effect "Arandr extension not found", but anyways it DOES work, just not right now for you I guess.

---

