---
title: "Share port"
date: 2007-04-13
forum: General Help
---

### Post by lhabjane on 2007-04-13
Can I share a port with samba? I'm using raw printing to POS printers! 
Nothing happens if I just share /dev/lp0 with samba and copy a file from windows to that shared location!

Help please

---

### Post by lhabjane on 2007-04-13
I've solved the problem. I've made an "loop" script that checks if there is new files in the directory (samba shared) and sends them to the port!

---

