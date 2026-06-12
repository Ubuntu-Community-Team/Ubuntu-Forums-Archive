---
title: "My gdm hangs.. *urgent*"
date: 2006-11-15
forum: General Help
---

### Post by spock84 on 2006-11-15
I was trying to compile the latest beryl svn, but it seemed I needed a newer version of gtk and glib to compile parts of it, so being myself, not very knowledgable but daring, I tried that, but the gtk installation didn't succeed. Apparently something was installed and messed everything up, cause now when I start up Ubuntu, it hangs before anything except the "wait" mouse cursor turns up (on an otherwise black screen).

Does anyone know what to do? I'd hate to have to reinstall everything and lose settings and crap. :-?

---

### Post by taurus on 2006-11-15
Maybe you just need to reconfigure your X again!  Boot into recovery mode from GRUB and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```

---

### Post by spock84 on 2006-11-15
Didn't work. Unfortunately I managed to accidentaly delete lots of system files as well, so I figured it'd be best if I just reinstalled, which is what I'm doing now. ](*,)

---

