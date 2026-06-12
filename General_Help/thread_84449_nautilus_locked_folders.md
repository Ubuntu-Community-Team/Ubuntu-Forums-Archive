---
title: "nautilus locked folders?"
date: 2005-10-31
forum: General Help
---

### Post by monotux on 2005-10-31
Hello everyone!
I ran into a great plugin for nautilus a month or so ago (while using arch linux), that I've been missing in ubuntu so far.
I don't know how to make debian packages, so I was wondering - has someone out there made a package for this?
[http://www.ids.org.au/~jam6/locked-folders/](http://www.ids.org.au/~jam6/locked-folders/)

---

### Post by 23meg on 2005-10-31
Looks promising. I searched for debs but none have been made so far it seems. I'll try compiling it tonight.

---

### Post by Joh_ on 2005-10-31
Not sure if it works the same, but I found this in the universe repositories I believe it was: zope-lockablefolder. With the description: "variant of the standard Folder that can restrict access to its contents".

---

### Post by suRoot on 2005-10-31
Dont' know about you, but I'd be a little uneasy encrypting anything important with a disclaimer like this:

[quote=http://www.ids.org.au/~jam6/locked-folders/]Keep in mind that there are no guarantees if you decide to use this prerelease code![/quote]

---

### Post by monotux on 2005-10-31
[QUOTE=suRoot]Dont' know about you, but I'd be a little uneasy encrypting anything important with a disclaimer like this:[/QUOTE]
I've used it for at least a few weeks, and I haven't run into any problems at all, and I think it's a pretty mature application (it doesn't matter if it's pre release, if it's done properly from the beginning).

Well, if anyone with sufficient skills can make a package of it, please post a link to the package here! :)

---

### Post by starNIX on 2005-11-01
I am having problems getting this to compile.  Here is the output:

bglade-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/freetype2 -DGLADEDIR=\"/usr/local/share/nautilus-locked-folders\" -Werror -g -O2 -MT encrypt.lo -MD -MP -MF .deps/encrypt.Tpo -c encrypt.c  -fPIC -DPIC -o .libs/encrypt.o
cc1: warnings being treated as errors
encrypt.c: In function 'lock_folder_read_dir':
encrypt.c:135: warning: pointer targets in passing argument 4 of 'EVP_CipherInit_ex' differ in signedness
encrypt.c:140: warning: pointer targets in passing argument 2 of 'EVP_CipherUpdate' differ in signedness
encrypt.c:140: warning: pointer targets in passing argument 4 of 'EVP_CipherUpdate' differ in signedness
encrypt.c:147: warning: pointer targets in passing argument 2 of 'EVP_CipherFinal_ex' differ in signedness
make[2]: *** [encrypt.lo] Error 1
make[2]: Leaving directory `/home/bpregont/Desktop/nautilus-locked-folder-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bpregont/Desktop/nautilus-locked-folder-1.0.0'make: *** [all] Error 2


Any ideas?

---

### Post by starNIX on 2005-11-05
::bump::

---

### Post by monotux on 2006-01-03
There must be a way to make this work in ubuntu :(

Anyone, please?

---

