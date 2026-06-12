---
title: "correct linux-image installation"
date: 2008-02-19
forum: General Help
---

### Post by Tatty on 2008-02-19
Is it a problem to have both:

linux-image-2.6.22-14-generic
and
linux-image-2.6.22-16-generic

installed at the same time?

```
tatty@MythServer:~$ uname -r
2.6.22-14-generic

```


Im trying to isolate some problems loading the gspca module and i was wondering if this could be part of it, but i dont really know what im talking about here and its a bit of a swing in the dark

---

### Post by kpkeerthi on 2008-02-19
```
Is it a problem to have both:

linux-image-2.6.22-14-generic
and
linux-image-2.6.22-16-generic

installed at the same time?

```
Nope. You can have both (and many more if you have disk space) all at the same time. Most people keep atleast two kernels so they can fall back to the old one if they find the new one problematic and/or delete the old one if not required any more.

---

### Post by Tatty on 2008-02-19
Thanks very much kpkeerthi

:)

---

