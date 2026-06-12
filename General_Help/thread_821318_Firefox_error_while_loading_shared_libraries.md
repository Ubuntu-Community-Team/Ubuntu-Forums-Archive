---
title: "Firefox error while loading shared libraries"
date: 2008-06-07
forum: General Help
---

### Post by ciberknibal on 2008-06-07
Hi!
I´m new in ubuntu. I´ve a problem with shared libraries.
I desinstall firefox-3 and install FF2.
If run firefox-2 in console appears this error: /usr/lib/firefox/firefox-2-bin: error while loading shared libraries: libplc4.so.0d: cannot open shared object file: No such file or directory

I locate the librarie in \usr\lib. I download the firefox in my personal directory and this works correctly. If i install and desintall with symantic i´ve the same problem.

If i run rhythmbox appears this error:
error while loading shared libraries: libnss3.so.1d: cannot open shared object file: No such file or directory.

How can fix it?
Thanks and sorry for my bad English.

---

### Post by y-lee on 2008-06-07
Just a (semi educated) guess open a terminal and try the following three commands:

```
cd /usr/lib
sudo ln -s libplc4.so.0d libplc4.so
sudo ln -s libnss3.so.1d libnss3.so
```

---

