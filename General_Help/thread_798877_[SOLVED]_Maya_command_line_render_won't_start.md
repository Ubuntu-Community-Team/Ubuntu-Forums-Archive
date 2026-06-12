---
title: "[SOLVED] Maya command line render won't start?"
date: 2008-05-18
forum: General Help
---

### Post by worc on 2008-05-18
Hi people.

I just got my Ubuntu 8.04 setup and played a while with Maya on it.

Maya runs perfect except one thing, the command line render won't start:
```
$ Render file.mb

Starting "/opt/autodesk/maya2008/bin/maya"
Cannot start maya
$
```

Anyone knows what is wrong here?

---

### Post by worc on 2008-05-19
Bump It Up!

---

### Post by worc on 2008-05-20
Found the reason, the /opt/autodesk/maya2008/bin/maya executable was missing.

A simply 'sudo ln -s /opt/autodesk/maya2008/bin/Maya2008 /opt/autodesk/maya2008/bin/maya' fixed it.

So this seems to be a Maya problem cause the installation is broken!

---

