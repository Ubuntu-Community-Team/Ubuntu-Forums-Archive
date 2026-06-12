---
title: "Compz won't start?"
date: 2008-07-02
forum: General Help
---

### Post by Ki11ah on 2008-07-02
I have installed compiz on my earOS(Ubuntu based media centre) but when I start it via terminal I get the following error message

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4152 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

What do I need to do?

---

### Post by isaacj87 on 2008-07-02
The error output is telling you to try it with indirect rendering. Try this command in terminal:

```
 compiz --replace --indirect-rendering
```

Did that work? If not, tell me what video card you have and what drivers.

---

### Post by Ki11ah on 2008-07-02
It's ok my friend, I got it working.

Thanks anyway

---

