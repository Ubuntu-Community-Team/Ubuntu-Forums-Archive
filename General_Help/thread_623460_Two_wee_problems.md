---
title: "Two wee problems"
date: 2007-11-25
forum: General Help
---

### Post by dunkyp on 2007-11-25
First off when I get my GDM for login the font in the imput box is massive like 70+pt and the same if I try to use the options menu. This continues until I login and turn desktop effects off and on again. It also happens however if I turn them off completely and restart.[s] Along with this every so often while installing software with apt it requests that I insert the ubuntu cd before it will continue.[/s]

any ideas as to what my problems could be??

---

### Post by PeterJS on 2007-11-25
Can't help you with the gdm font thing, but for the install bit open up a terminal and start gedit with sudo privileges:
```

sudo gedit

```
When that loads up open /etc/apt/sources.list, and comment out, by putting a # at the beginning of the line, any line that makes mention of your cd, save, close, and you should be good to go on that front.

---

### Post by dunkyp on 2007-11-25
cheers that really helped with that problem

---

### Post by wooster on 2007-11-26
Hi. I'll try to help with the large gdm font problem.  Your situation looks a lot like [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/151311]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/151311") this bug.  One of the suggestions was to put Option "DDC" "no" in your xorg.conf.

```
sudo gedit /etc/X11/xorg.conf
```
Look for this section of the Xorg.conf.
```

Section "Monitor"
       ...
EndSection

```

Add Option "DDC" "no" to that section.
```
Section "Monitor"
       ...
Option "DDC" "no"
EndSection
```

See if that works. There are other suggestions there also. Good luck.

---

