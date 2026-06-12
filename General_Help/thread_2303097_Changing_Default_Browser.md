---
title: "Changing Default Browser"
date: 2015-11-16
forum: General Help
---

### Post by steve234 on 2015-11-16
Hi there,

I use Midori on my Lubuntu box because it's snappy-fast. Problem is, it seems like it's not my default browser. For example thunderbird links open in Firefox.

I've done the below and selected Midori:

```
sudo update-alternatives --config x-www-browser
```

The output of which is:

```
   Selection    Path                       Priority   Status
------------------------------------------------------------
  0            /usr/bin/chromium-browser   40        auto mode
  1            /usr/bin/chromium-browser   40        manual mode
  2            /usr/bin/firefox            40        manual mode
* 3            /usr/bin/midori             39        manual mode

```

What gives? Is there a preference I am missing in T-bird?

---

### Post by raketax on 2015-11-16
Tried to change default browser in the normal Lubuntu settings, maybe LXDE uses that as a reference to what to open links with?

---

### Post by steve234 on 2015-11-16
I'm confused as to what you mean by the "normal Lubuntu settings" where would I find those?

---

### Post by vasa1 on 2015-11-16
Take a look here: [http://askubuntu.com/a/172883](http://askubuntu.com/a/172883)

---

### Post by steve234 on 2015-11-16
That did the trick - didn't find that one googling - ta

---

