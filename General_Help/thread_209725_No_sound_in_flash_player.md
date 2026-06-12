---
title: "No sound in flash player"
date: 2006-07-05
forum: General Help
---

### Post by ubunturules on 2006-07-05
I can't play any sound in flash player and I have all the codecs installed.  Any ideas?

---

### Post by aysiu on 2006-07-05
Try this:
1. Close Firefox or whatever browser you're using
2. ```
sudo aptitude update
sudo aptitude install alsa-oss
```
3. Open your browser

Incidentally, which browser are you using?

---

### Post by doris.houng on 2006-07-05
[https://help.ubuntu.com/community/RestrictedFormats#flashtrouble](https://help.ubuntu.com/community/RestrictedFormats#flashtrouble)

---

### Post by ubunturules on 2006-07-05
I got it to work.  Thank you doris for the wiki you sent me.  I have a little bit of trouble getting it to work because I forgot to restart my browser. lol  Thank you

---

