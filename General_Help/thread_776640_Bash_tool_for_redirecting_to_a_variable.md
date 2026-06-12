---
title: "Bash tool for redirecting to a variable?"
date: 2008-04-30
forum: General Help
---

### Post by spiritfox on 2008-04-30
I was just wondering if there was a bash tool for redirecting stdout or a file to a variable.  I'm fairly new at bash scripting, so if I'm asking in the wrong place or if there is an obvious answer, I apologize.

---

### Post by Dr Small on 2008-04-30
"cat" perhaps?
It depends on your stdout.

For example:
```
newvar=$(cat /boot/grub/menu.lst)

echo $newvar
```

---

### Post by spiritfox on 2008-04-30
Thanks a ton for that amazingly fast and easy answer!

---

