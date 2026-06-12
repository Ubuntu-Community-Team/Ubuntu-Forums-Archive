---
title: "3Ddesk"
date: 2005-08-05
forum: General Help
---

### Post by chadwick359 on 2005-08-05
Okay, another question. i have 3ddesk working perfectly, except on startup. Since 3ddesk requres sudo to bein the daemon, just putting 3ddesk in the startup, doesn't work. And without a prompt, sudo 3ddesk in startup still doesn't do anything. Is there an argument to sudo to automatically apply the password?

//Edit

I got this to work, from a tip from the firestarter thread. I added 'user ALL= NOPASSWD: /usr/bin/3ddesk' to /etc/sudoers.

---

