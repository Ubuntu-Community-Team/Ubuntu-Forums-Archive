---
title: "compile problem"
date: 2006-10-12
forum: General Help
---

### Post by Freddy on 2006-10-12
Hi all, efter upgrading to KDE 3.5.5 I'm getting some problems while doing the make procedure.

```
grep: /usr/lib/libfam.la: No such file or directory
/bin/sed: can't read /usr/lib/libfam.la: No such file or directory
libtool: link: `/usr/lib/libfam.la' is not a valid libtool archive
```
I understand that this libfam.la is missing but when trying to install that, apt-get wants to remove most of the kde 3.5.5 install.

Is this even worth the try to solve or must i wait for the developers of Superkaramba, Ksmoothdock and Dekorator update their code. Pls help :-)   /// Freddan

---

### Post by dresnu on 2006-10-12
Exact same problem here...

---

### Post by Freddy on 2006-10-12
Found the solution. libfam is outdated get "libgamin-dev" instead :-).   /// Freddan

---

### Post by dresnu on 2006-10-13
Thanks! That did the trick ;-)

---

