---
title: "Howto restore administrative access"
date: 2007-05-29
forum: General Help
---

### Post by lordorient on 2007-05-29
I have mistaken with usermod -G and now I cannot do sudo on my machine. Is any way to restore correct group associations?

---

### Post by fanatik on 2007-05-29
for sudo access you need to be in the admin group, but obviously you will have to do this as root! so reboot back to single user mode or recovery mode, which should drop you at a root prompt and type:

# adduser <your userid> admin

that adds you tot he admin group. you can then reboot and use sudo again. you will also need to add yourself into any other groups you may have removed.

---

