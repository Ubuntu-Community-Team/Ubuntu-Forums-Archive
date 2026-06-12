---
title: "Help with multiple versions of Firefox"
date: 2008-05-13
forum: General Help
---

### Post by Anveo on 2008-05-13
I would like to run multiple versions of Firefox for testing. I figured it might be as simple as downloading the binaries from the website and extracting them.

./firefox-bin
./firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

ls -l libmozjs.so
-rwxr-xr-x 1 bracer bracer 631676 2008-04-04 17:02 libmozjs.so

ls -l /usr/lib/libmozjs.so
lrwxrwxrwx 1 root root 14 2008-05-12 23:13 /usr/lib/libmozjs.so -> libmozjs.so.0d

So libmozjs.so definitely exists in the binary's directory and the system lib. Any ideas?

I am running Hardy x64 Ubuntu

---

### Post by khughitt on 2008-10-10
In case anyone is still having trouble with this. There is a command-line argument "-no-remote" that should do the trick. e.g.

```
firefox -no-remote -ProfileManager
```

or

If you want to create separate profiles for each instance (you can do this either with the above command, or by closing all instances of firefox and running "firefox -ProfileManager"), and then have them loaded automatically, just specify the exact profile to use for each command:

```
firefox -no-remote -p "debug-3.1"
```

Found the solution at [http://onlinedev.blogspot.com/2008/01/run-multiple-versions-of-firefox.html](http://onlinedev.blogspot.com/2008/01/run-multiple-versions-of-firefox.html).

Cheers,

---

