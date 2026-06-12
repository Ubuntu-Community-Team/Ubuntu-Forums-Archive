---
title: "Created new home partition - lost some configs"
date: 2007-05-04
forum: General Help
---

### Post by Nobby on 2007-05-04
Hi,

I created a new partition for my home folder & shifted it over using the instructions here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome).

On rebooting into the system, it seems some config files were not carried over and I was just wondering if this was normal.  

For example, firefox had lost all bookmarks & extensions, my desktop background had reverted back to default, and my startup programs went back to default.  I've been able to restore some stuff by simply copying the config files from my home backup.

---

### Post by taurus on 2007-05-04
Did you also copying over all the hidden files, the ones that start with a period, .?

---

### Post by Nobby on 2007-05-04
well that page had this command:

find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

I assumed that this copied over everything.  When I compare files of my home backup with my new home inculding the hidden files, it appears that everything copied over.

---

