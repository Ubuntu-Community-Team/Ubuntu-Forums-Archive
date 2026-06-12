---
title: "What is the difference between /opt and /usr in the linux filesystem?"
date: 2007-09-24
forum: General Help
---

### Post by Doughy on 2007-09-24
Can anyone explain to me the difference between the following directories in the linux filesystem:

/opt
/usr/local
/usr/share

In reading some tutorials online, I don't understand why linux has so many places that contain installed binaries.

---

### Post by tszanon on 2007-09-24
> **Doughy said:**
> Can anyone explain to me the difference between the following directories in the linux filesystem:

/opt
/usr/local
/usr/share

In reading some tutorials online, I don't understand why linux has so many places that contain installed binaries.
First thing I do after installing Ubuntu:
```
cd /
sudo rmdir opt
sudo ln -s /usr/local /opt

```
If the application wants /usr/local, it's there. If the application wants /opt, it's there too. And I keep the filesystem clean. :)

But I don't know about /usr/share. I just leave it alone.

---

