---
title: "Calibre no longer working after updates..."
date: 2015-03-17
forum: General Help
---

### Post by timgood on 2015-03-17
Following some security updates, Calibre will no longer start. Starting from a terminal gives me:

```
/opt/calibre/bin/calibre: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0: undefined symbol: g_type_check_instance_is_fundamentally_a

```

Output of ls -l /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0 is:

```
lrwxrwxrwx 1 root root 27 Jan 21 19:06 /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.2400.25
```

Ideas as to what I can do to make Calibre run again would be much appreciated.

---

### Post by sandyd on 2015-03-17
Is that calibre from the repos?

Had the same issue, simply removed calibre and installed the binaries using the [script from the calibre site]("http://calibre-ebook.com/download_linux").

---

