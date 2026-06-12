---
title: "Madman and Beep Media Player"
date: 2005-04-25
forum: General Help
---

### Post by mattack on 2005-04-25
Anyone get Madman to work with BMP? Normally it works with XMMS but I want to use BMP...

---

### Post by mattack on 2005-04-25
I actually got it to work by creating a symlink that points to bmp called xmms. Everything seems to work fine.
```
matt@mattack:/usr/bin $ sudo mv xmms xmms.backup
matt@mattack:/usr/bin $ sudo ln -s beep-media-player xmms
```

---

