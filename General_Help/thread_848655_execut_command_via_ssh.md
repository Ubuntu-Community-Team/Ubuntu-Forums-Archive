---
title: "execut command via ssh"
date: 2008-07-03
forum: General Help
---

### Post by dapim on 2008-07-03
how can i execute commanda via ssh

this doesn't ssems to work
sshk nameserver | ls

---

### Post by milosz.galazka on 2008-07-03
*ssh server command*
for example:
*ssh localhost ls*

---

### Post by HermanAB on 2008-07-03
Or the pointy clicky way:
ssh -C -c blowfish -X user@server gnome-panel
ssh -C -c blowfish -X user@server kicker

---

