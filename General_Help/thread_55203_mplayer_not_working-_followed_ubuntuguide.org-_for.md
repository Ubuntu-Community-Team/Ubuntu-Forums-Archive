---
title: "mplayer not working- followed ubuntuguide.org- for hoary"
date: 2005-08-07
forum: General Help
---

### Post by jang on 2005-08-07
Hello guys.  Followed the quide step by step.  But when I play a file, nothing would play, and it will stay stuck.  I tried to change the audio to oss, it would play with error saying no sound.  It also won't change to full screen.  I tried mplayer -ao oss -vo xv filename, it played without a hitch, and at full screen.  What gives? Any suggestions?

BTW, even after editing line with Gedit vo=xv, when actual playback, I still see vo=x11

---

### Post by Epyon on 2005-08-07
i actually had the same problem too, i couldnt resolve it, but instead of Mplayer i use Xine.

---

### Post by jang on 2005-08-07
but mplayer is the best  :grin: anyone?

---

### Post by rudiz on 2005-08-08
try this:

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)


and/or remove totemgstreamer

---

### Post by jang on 2005-08-08
hey, your suggestion WORKS!!!  Thanks.  Appreciate the help.

---

