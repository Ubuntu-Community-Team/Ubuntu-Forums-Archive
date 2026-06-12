---
title: "logrotate: rotate vs maxage"
date: 2008-05-16
forum: General Help
---

### Post by jbulcher on 2008-05-16
Hi,

I'm trying to set up a logrotate configuration file. Its my first time, and it seemed pretty straightforward; I wanted to rotate some files and delete the ones that were older than 30 days. However, using 'maxage 30' doesn't seem to do the trick. Actually, instead of keeping any old logs, it deletes them right away; only rotate seems to keep the files - but I want to go by date, not the number of times I've rotated the files previously.

Am I using maxage the way it was intended, and if not, how can I accomplish what I'm trying to do?

Thanks for your help!

---

