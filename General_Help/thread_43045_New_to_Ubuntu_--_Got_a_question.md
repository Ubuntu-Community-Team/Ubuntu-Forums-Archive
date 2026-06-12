---
title: "New to Ubuntu -- Got a question"
date: 2005-06-20
forum: General Help
---

### Post by feld on 2005-06-20
Hey this is my first install of Ubuntu and I have a question -- how do I manage my daemons? I came from Gentoo and we used rc-update to change daemons starting runlevels and if they even started by default, and rc-status to view which ones are currently running. How do you do this in Ubuntu?

Thanks


-Feld

---

### Post by desdinova on 2005-06-20
You can use

/etc/init.d/daemonname start:stop:status:reload

---

### Post by ltmon on 2005-06-20
There's a graphical tool called BUM (Boot Up Manager) that is meant to do this.

---

### Post by feld on 2005-06-21
[QUOTE=][/QUOTE]
 any pointers as to of where I can find BUM? And any reason why the only way to manage your daemons is thru a graphical interface? I find that kind of ridiculous.... how can you run a server and manager your daemons with no X? It wouldnt be possible. Certainly there must be a way to do it!



-Feld

---

### Post by feld on 2005-06-21
[QUOTE=][/QUOTE]
 nevermind... i asked a debian user who actually knows what they're doing and they told me

update-rc.d is the command


-Feld

---

