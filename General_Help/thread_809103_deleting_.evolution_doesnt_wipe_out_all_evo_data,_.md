---
title: "deleting .evolution doesnt wipe out all evo data, how to?"
date: 2008-05-27
forum: General Help
---

### Post by zeltak on 2008-05-27
Hi guys

Ive searches all over but cant find how. Google calendar support doesnt work at all and i have other strange issues after upgrading to hardy so i thought about starting fresh with evolution. I deleted the .evolution folder from my home folder but i still get lots of the old settings back (including the calendars and contacts etc..).
Does anyone know how to delete ALL evolution previous setting and start fresh?

thx

Zeltak

---

### Post by justleen on 2008-05-27
hmmm not sure... there a bunch of file in /usr/share.. 

might wanna try remove/install through synaptic?

---

### Post by Nepherte on 2008-05-27
How did you remove it? Using the purge command also removes the configuration files:
```
sudo aptitude purge evolution
```

---

