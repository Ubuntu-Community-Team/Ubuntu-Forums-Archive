---
title: "evince command line error: libffi shared object error"
date: 2023-12-12
forum: General Help
---

### Post by umut-tabak on 2023-12-12
Dear all,

I have upgraded to ubuntu 22.04 on my old laptop. However, evince on the command line fails with the following error:

evince: error while loading shared libraries: libffi.so.8: failed to map segment from shared object

This library is installed under /usr/lib/x86_64-linux-gnu. I also tried to add this directory to LD_LIBRARY_PATH, which I think is not necessary, but that does not help as well.

 I also pasted the output of dpkg -S below:

dpkg -S libffi
libffi8:amd64: /usr/share/doc/libffi8/changelog.Debian.gz
libffi8:amd64: /usr/lib/x86_64-linux-gnu/libffi.so.8.1.0
libffi8:amd64: /usr/share/doc/libffi8/copyright
libffi8:amd64: /usr/share/doc/libffi8
libffi8:amd64: /usr/lib/x86_64-linux-gnu/libffi.so.8

Strangely enough, I can open a document by using the graphical user interface with the default document viewer which is also using evince. So with the file browser, I can click the file and open the file without problems. But with the command line, I have the above mentioned problem.

How can I fix this error with evince?

Thanks in advance.

---

