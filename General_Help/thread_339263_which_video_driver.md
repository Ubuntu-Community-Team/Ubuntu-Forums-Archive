---
title: "which video driver"
date: 2007-01-15
forum: General Help
---

### Post by naseem on 2007-01-15
Hello:D
I'm tring to know which video driver is installed, anyone can tell me which command to lounch in shell?

---

### Post by hikaricore on 2007-01-15
```
cat /ect/X11/xorg.conf | grep Driver
```

will show you what driver you're using in your xorg.conf, it will usually be the one at the bottom of the output list :P

```
glxinfo
```

Should give you further information on the drivers you're using at the moment

---

### Post by naseem on 2007-01-15
thank you for fast replay
so code n.1 did not work
 cat: /ect/X11/xorg.conf: Nessun file o directory
code n.2 worfked well
server glx vendor string: SGI
server glx version string: 1.2
I guess that is the name and version right?

---

### Post by hikaricore on 2007-01-15
Sorry that was a typo >.<

> cat /**etc**/X11/xorg.conf | grep Driver

And yes that should be the name and version.  Mine has three sets like this:

> 
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

client glx vendor string: NVIDIA Corporation
client glx version string: 1.4

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6200/PCI/SSE2
OpenGL version string: 2.1.0 NVIDIA 96.31


Mine obviously supports opengl, which not all cards do fully so you may not see that one.

---

### Post by naseem on 2007-01-15
Thanks hikaricore! :)

---

