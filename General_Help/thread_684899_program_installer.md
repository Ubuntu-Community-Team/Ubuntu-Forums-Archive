---
title: "program installer?"
date: 2008-02-01
forum: General Help
---

### Post by fedex1993 on 2008-02-01
Okay i have a question is there anyway that i can install yum on ubuntu and use it instead of apt-get? i just have lost taste in apt and yum is very nice.

---

### Post by aysiu on 2008-02-01
Even if you could install Yum on Ubuntu, I doubt it would work properly, since Fedora's software management is slightly different from Ubuntu's.

What exactly have you had problems with in Apt?

---

### Post by fedex1993 on 2008-02-01
The slowness of the downloads and no it is not my internet beacuse i have 2 computers my laptop and my desktop so the speed is fine. also that i have noticed more resources are on yum than apt and yum seems to be 10x faster to me than apt

---

### Post by aysiu on 2008-02-01
> **fedex1993 said:**
> The slowness of the downloads and no it is not my internet beacuse i have 2 computers my laptop and my desktop so the speed is fine. also that i have noticed more resources are on yum than apt and yum seems to be 10x faster to me than apt
The speed might have to do with what repositories you're using. Perhaps using a local mirror might help? As for the resources (more software available, you mean?), you need to enable extra repositories for that.

Follow [these instructions](http://www.psychocats.net/ubuntu/sources#key) to get more software available. After you paste in the new sources.list, though, modify it to mirror something local before you save the file. For example, if a line says: ```
deb http://archive.ubuntu.com/ubuntu gutsy main restricted
``` change it to say ```
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted
```

---

