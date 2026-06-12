---
title: "Unable to remove line from source list."
date: 2013-10-07
forum: General Help
---

### Post by CRAlmsFan on 2013-10-07
Hello,

 I messed something up, and now i cannot use update manager or the software center. I tried to edit the source list through the terminal. But it does not appear. Is thier a way to get rid of stebbins-handbrake?

[IMG]http://i41.tinypic.com/2dlm0s9.png[/IMG]

---

### Post by oldos2er on 2013-10-07
```
sudo rm /etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list

sudo apt-get update
```

---

### Post by CRAlmsFan on 2013-10-08
Thank you oldos2er.

---

### Post by oldos2er on 2013-10-08
Welcome. If your problem is fixed please mark the thread as 'Solved' under Thread Tools. Thanks.

---

