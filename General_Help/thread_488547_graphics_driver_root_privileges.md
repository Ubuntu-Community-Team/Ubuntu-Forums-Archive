---
title: "graphics driver root privileges"
date: 2007-06-30
forum: General Help
---

### Post by joeyea on 2007-06-30
hi, i have a unichrome graphics card and ive managed to set up the driver but with one problem. when i want to do something that uses the graphic card in a certain way like most 3d programs and wine it only works if i do it through the command line with sudo. i can run glxgears but it only works fast and properly if i do sudo glxgears. is there any way that i can make it have the privileges automaticly?
thank you
Joe

---

### Post by tpg on 2007-06-30
Yes, add the following to your xorg.conf, and restart X. It should allow all users to get 3D privileges.

```
Section "DRI"
Mode	0666
EndSection
```

---

### Post by joeyea on 2007-07-01
Thank you, thats great it solves alot of problems.

---

