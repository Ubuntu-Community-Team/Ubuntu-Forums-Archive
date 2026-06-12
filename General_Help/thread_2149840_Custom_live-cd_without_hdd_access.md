---
title: "Custom live-cd without hdd access"
date: 2013-05-30
forum: General Help
---

### Post by algoe on 2013-05-30
Hi,

I need to create a live-cd (preferrably Ubuntu Desktop) where the user cannot access the hdd. The reason for this is for users to be completely "sandboxed" while performing certain tasks.

I found the guide for LiveCD customization here: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
But is there an easy way to change it so it cannot access the hdd? I was hoping it would be as easy as to remove the default user from some group, thereby removing privileges to access the hdd, but I have a hard time finding any information on the topic.

Any ideas?

//Martin

---

### Post by 2F4U on 2013-05-30
Mounting usually requires root or sudo privileges. I guess you could remove the autologin according to the description in the article and create your own user with just standard privileges (no sudo capability). However, be aware of that as long as the users are allowed to boot from a cd, they can boot from any cd. And another cd may allow them to mount and access the hdd.

---

