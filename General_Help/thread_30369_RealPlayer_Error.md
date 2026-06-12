---
title: "RealPlayer Error"
date: 2005-04-28
forum: General Help
---

### Post by Das Ein on 2005-04-28
When I try and run RealPlayer I always get

"Cannot launch entry
Details: Failed to execute child process "realplay" (No such file or directory)"

What can I do to fix this, or can I open it up some other way.

---

### Post by Das Ein on 2005-04-28
Bump

---

### Post by Professor X on 2005-04-28
Is realplayer in your path?  If not, you'll need to set up a symbolic link by typing:

```
sudo ln -s /opt/RealPlayer/realplay /usr/bin/realplay
```

(Assuming you installed realplayer into /opt/RealPlayer)

Hope that helps.

---

### Post by Das Ein on 2005-04-28
:$ That was it.

---

