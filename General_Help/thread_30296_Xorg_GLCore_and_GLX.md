---
title: "Xorg GLCore and GLX"
date: 2005-04-28
forum: General Help
---

### Post by nocturn on 2005-04-28
I saw in my xorg.conf file that I load both GLCore and GLX.

Do I need both?  What is the difference between them?

---

### Post by condormcs on 2007-10-04
GlCore could be used by nvidia?

just a wild guess.

---

### Post by bwallum on 2007-10-31
I read that glx is the nVidia specific 'GLcore'. You probably don't need GLcore if you are running glx and have the nvidia-glx-new (or even nvidia-glx) driver installed.

If you have the nvidia-glx-new driver installed run 
```
sudo nvidia-xconfig
```
then glx is added to the load command in xorg.conf and GLcore is not.

I have re-asked the question in a new thread. If you have discovered the answer could you let me know please.

Regards
Bob

UPDATE If you are running the nvidia-glx(-new) driver then you only need glx to run OpenGL. I have removed GLcore and get a much faster machine in return.

---

