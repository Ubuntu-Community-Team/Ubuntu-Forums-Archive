---
title: "is my system hacked?"
date: 2006-11-02
forum: General Help
---

### Post by harty83 on 2006-11-02
I noticed that my server was doing a lot of activity so I ran top and sure enough the program "find" by user "nobody" was running and consuming most of the cpu.  Is my system hacked or can there be another explanation for this?

Thanks!
Alan

---

### Post by bsussman on 2006-11-02
Ths is not proof of your system being hacked.

It is likely to be running to automatically update the slocate database.

Lots of things run automatically - look in the /etc/cron.xxxx directories

---

