---
title: "Package problem"
date: 2007-03-02
forum: General Help
---

### Post by auskento on 2007-03-02
I have been trying to get VLC media services and now the ability to do WMV -> AVI conversions on my linux server (no desktop)

I have for a while been getting this error when trying to get it functioning

```

Unpacking libwxgtk2.6-0 (from .../libwxgtk2.6-0_2.6.1.2ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libwxgtk2.6-0_2.6.1.2ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libwx_baseu-2.6.so.0', which is also in package libwxbase2.6

```

I am not sure how to resolve this.

All i want to be able to do is run mencoder on this box now :/

---

### Post by chggr on 2007-03-02
Reading the error message, I think that you should unistall libwx_baseu-2.6 and then try installing libwxbase2.6 again.

---

