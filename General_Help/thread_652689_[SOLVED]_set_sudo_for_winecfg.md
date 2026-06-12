---
title: "[SOLVED] set sudo for winecfg"
date: 2007-12-29
forum: General Help
---

### Post by onegreenparker on 2007-12-29
I would like to make sure that users can't muck about with winecfg, is there a way I can set it up so that one must sudo winecfg? If so, how?

---

### Post by burbankmarc on 2007-12-29
```
sudo chmod 0700 /usr/bin/winecfg
```

---

### Post by onegreenparker on 2008-01-03
Perfect!
Thank you

---

