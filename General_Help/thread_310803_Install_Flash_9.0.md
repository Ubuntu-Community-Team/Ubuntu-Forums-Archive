---
title: "Install Flash 9.0"
date: 2006-12-01
forum: General Help
---

### Post by Alexandre Berger on 2006-12-01
Hi everybody

I would like to install flash 9.0. 
How I do this with Synaptic?

Alexandre Berger

---

### Post by LLRNR on 2006-12-01
Hi and welcome !

For Flash 9 plugin, see [this](https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3).

LLRNR

---

### Post by bruenig on 2006-12-01
See my signature if you want to install it via deb so apt can track it.

---

### Post by pay on 2006-12-01
```
wget http://distfiles.gentoo.org/distfiles/FP9_plugin_beta_112006.tar.gz
wget http://distfiles.gentoo.org/distfiles/FP9_standalone_beta_112006.tar.gz
sudo tar zxvf FP9_plugin_beta_112006.tar.gz /opt/netscape-flash
sudo tar zxvf FP9_standalone_beta_112006.tar.gz /opt/netscape-flash
sudo  ln -s /opt/netscape-flash/libflashplayer.so /usr/lib/mozilla-firefox/plugins/
```Your firefox might not exactly be at /usr/lib/mozilla-firefox, you can find it with sudo find / -iname firefox. And it's probably better to use the above debian format

---

### Post by Alexandre Berger on 2006-12-01
> **LLRNR said:**
> Hi and welcome !

For Flash 9 plugin, see [this](https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3).

LLRNR

Thank. How I can give you a point?

---

### Post by LLRNR on 2006-12-01
> **Alexandre Berger said:**
> Thank. How I can give you a point?
My pleasure ;) Just prey that I'll pass my exams :lol:

---

