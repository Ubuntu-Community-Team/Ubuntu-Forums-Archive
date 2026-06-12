---
title: "automatic updates failing"
date: 2017-03-20
forum: General Help
---

### Post by schmitta on 2017-03-20
As you know Ubuntu sends automatic updates. Lately all automatic updates sent to my machine end up failing (I have no error code) and I think it is stuck this way until I find from someone what is wrong and correct it. Please help. Thank you.

---

### Post by deadflowr on 2017-03-20
Look at your unattended-upgrades logs in */var/log/unattended-upgrades*
Also look at your apt logs in */var/log/apt *(both the histroy and term logs.
As well as the dpkg logs at /*var/log/dpkg.log*

---

### Post by schmitta on 2017-03-21
I do not know what I am looking for

---

