---
title: "Want to backup using rsync"
date: 2020-03-02
forum: General Help
---

### Post by robertcull1 on 2020-03-02
I would like to backup my files to an off site data service. Presently I backup to my hostgator domain. But I get a broken pipe if I try to upload a file over 1G. Does anyone know of a service I can use that would not hang like hostgator does? I may also need a little help with the command.

---

### Post by MoebusNet on 2020-03-03
I can't help you with the off-site data storage; I won't use them. I believe ```
 man rsync 
``` would give you the commands and usage for rsync, but allow me to suggest that if you are running a GUI, you might be happier with grsync which is a graphical frontend for rsync It's what I use for my backups; it is well-suited for most common backup tasks.

---

### Post by HermanAB on 2020-03-03
You can get your own $5 per month server at Linode.  Then you can do whatever you want with it.

---

### Post by robertcull1 on 2020-03-04
That should do it. Thanks!

---

