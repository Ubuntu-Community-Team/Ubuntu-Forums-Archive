---
title: "libstartup-notification-1.la"
date: 2007-05-12
forum: General Help
---

### Post by 3saul on 2007-05-12
I'm running 7.04. However ever since upgrading I've had trouble building apps that require libstartup notification. I get this error. Any ideas?

```
/bin/sed: can't read /usr/lib/libstartup-notification-1.la: No such file or directory
libtool: link: `/usr/lib/libstartup-notification-1.la' is not a valid libtool archive
```

I've rebuilt libstartup from source.

```
/usr/lib$ ls -l libstart*
-rw-r--r-- 1 root root 41230 2007-03-27 04:58 libstartup-notification-1.a
lrwxrwxrwx 1 root root    34 2007-05-12 22:37 libstartup-notification-1.so -> libstartup-notification-1.so.0.0.0
lrwxrwxrwx 1 root root    34 2007-05-12 22:37 libstartup-notification-1.so.0 -> libstartup-notification-1.so.0.0.0
-rw-r--r-- 1 root root 31308 2007-03-27 04:58 libstartup-notification-1.so.0.0.0
```

---

### Post by 3saul on 2007-05-12
Anybody have ant ideas?

---

### Post by 3saul on 2007-05-12
Is no one else having this issue?

---

