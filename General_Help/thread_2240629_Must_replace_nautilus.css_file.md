---
title: "Must replace nautilus.css file"
date: 2014-08-21
forum: General Help
---

### Post by victorw26 on 2014-08-21
I am running ubuntu 14.04.  I accidently removed the file 'nautilus.css' from /usr/share/themes/Ambiance/gtk-3.0/apps/

Is there a simple way to replace this file without having to re-install 14.04?

---

### Post by steeldriver on 2014-08-21
Hello and welcome to the forums

The /usr/share/themes/Ambiance/gtk-3.0/apps/nautilus.css file appears to be part of a package called light-themes - so it should be sufficient to reinstall that, either from the software center or from a terminal using

```

sudo apt-get install --reinstall light-themes

```

---

### Post by victorw26 on 2014-08-21
Thanks!  Got it!

---

