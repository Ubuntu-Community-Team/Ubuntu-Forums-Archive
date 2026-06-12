---
title: "Error in installing tcpreplay"
date: 2007-05-08
forum: General Help
---

### Post by entr0py401 on 2007-05-08
I am getting an error from the tcpreplay package. Not sure if its missing a library or what.

Here's the error:

root@attackinject:~# tcpreplay
tcpreplay: error while loading shared libraries: libopts.so.25: cannot open shared object file: No such file or directory


I have the packages autogen, libopts25, libopts25-dev installed so i should have the proper libraries installed.

Anyone experience this before?


thanks!

---

### Post by entr0py401 on 2007-05-08
Looks like the package installed libopts.so.24.3.5 and tcpreplay was expecting libopts.so.25.

symlink FTW.

I created a symlink and it appears to be working

libopts.so.25 -> /usr/lib/libopts.so.24

---

