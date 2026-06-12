---
title: "Firefox/flash sound working, but unstable."
date: 2006-07-05
forum: General Help
---

### Post by musther on 2006-07-05
I've looked around the forums and found stuff about getting sound working with flash and firefox, and now it is, using this:

```
FIREFOX_DSP="aoss"
```

in firefox rc.  Problem is that firefox is unstable when running flash things, sometimes it just locks up.  For example, if I'm watching a youtube vid and hit the full screen button, firefox freezes.

Anyone had this problem and got it working well?

Thanks

-----EDIT-----

The problem is package 'alsa-oss' without it flash is stable but has no sound, with it, unstable but with sound....

---

### Post by dmizer on 2006-07-05
[http://ubuntuforums.org/showthread.php?t=187752&highlight=flash+sound](http://ubuntuforums.org/showthread.php?t=187752&highlight=flash+sound)

see post number 5

---

### Post by musther on 2006-07-05
Interestingly I followed the suggestion in post 6, but it woked!

---

