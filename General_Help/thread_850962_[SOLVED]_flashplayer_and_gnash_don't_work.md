---
title: "[SOLVED] flashplayer and gnash don't work"
date: 2008-07-06
forum: General Help
---

### Post by jmd9qs on 2008-07-06
hi,

im running firefox three on hardy...i cant get any flash animation to work. ive tried to install flash 3 times, and gnash once. gnash installed fine but doesnt work, and flashplayer doesn't seem to be doing anything at all. any help is appreciated.

---

### Post by linuxisfree on 2008-07-06
I'm assuming this is the nonfree flash plugin you tried to install.. am i right? there is another on called "swfdec", you could try that (it's what i use). If you want the web browser plugin only just install the "swfdec-mozilla" package.

Only thing is, i don't seem to be able to adjust the volume... (always seems to be in MAX mode). Just give it a try though.:D

---

### Post by jmd9qs on 2008-07-06
kay...i tried to install the plug-in version and the terminal told me that it was already the current version. how can i change the default from gnash to this?

---

### Post by linuxisfree on 2008-07-06
> **jmd9qs said:**
> kay...i tried to install the plug-in version and the terminal told me that it was already the current version. how can i change the default from gnash to this?

did you uninstall gnash and the nonfree plugin? If not, please do and look at it again... Thanks!

---

### Post by jmd9qs on 2008-07-06
i'm a little new at this, so how can i do this from the terminal? i don't know where gnash is stored, or flashplayer for that matter. i'd like to do it through command-line instead of gui so i can learn more.

---

### Post by linuxisfree on 2008-07-06
> **jmd9qs said:**
> i'm a little new at this, so how can i do this from the terminal? i don't know where gnash is stored, or flashplayer for that matter. i'd like to do it through command-line instead of gui so i can learn more.

type this:

```
sudo apt-get remove gnash
``` and (if you also have the nonfree plugin) ```
sudo apt-get remove flashplugin-nonfree
```That should remove them.

---

### Post by jmd9qs on 2008-07-06
thanks, that worked. i can now see flash animation and videos. 'preciate it.

---

