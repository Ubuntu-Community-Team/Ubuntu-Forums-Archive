---
title: "Ubuntu Vertical Line Crash"
date: 2014-04-29
forum: General Help
---

### Post by kyle19 on 2014-04-29
Ive recently Installed Ubuntu and when i go to play minecraft or any other games, even the browser sometimes my ubuntu freezes up for about 10 seconds then goes to vertical lines that blend with the color of my desktop (green), Please Help Meh

---

### Post by tgalati4 on 2014-04-29
Open a terminal and post the output of:

```
lspci
```

If you are running on-board graphics, it is possible that your graphics chip is heating up and lifting off of the motherboard causing the strange graphics and the freeze.  Unfortunately there is no good fix.  If you have a discrete graphics card, then pull it out and run from from the on-board graphics.

---

