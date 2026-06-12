---
title: "Hurray for flash problems (Gutsy 64-bit)"
date: 2008-06-26
forum: General Help
---

### Post by themostunoriginalname on 2008-06-26
I tried this link:

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

and the script failed.

Output:
$ ls -al /usr/lib/mozilla/plugins/
total 7952
drwxr-xr-x 2 sebastian users    4096 2008-06-25 22:33 .
drwxr-xr-x 3 root      root     4096 2008-06-24 23:47 ..
-rwxr-xr-x 1       501 users 8115888 2008-03-24 19:02 libflashplayer.so
lrwxrwxrwx 1 sebastian users      39 2008-04-15 00:40 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 sebastian users      36 2008-04-14 09:17 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 sebastian users      37 2008-04-14 09:17 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 sebastian users      34 2008-04-14 09:17 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 sebastian users      35 2008-04-14 09:17 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 sebastian users      36 2008-04-14 09:17 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 sebastian users      37 2008-04-14 09:17 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 sebastian users      42 2008-04-14 09:17 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 sebastian users      43 2008-04-14 09:17 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 root      users      60 2008-06-25 22:33 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

$ ls -al /usr/lib/firefox/plugins/
total 12
drwxr-xr-x 2 sebastian users 4096 2008-06-25 22:33 .
drwxr-xr-x 4 root      root  4096 2008-06-24 20:46 ..
lrwxrwxrwx 1 sebastian users   39 2008-04-15 00:40 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 sebastian users   36 2008-04-14 09:17 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 sebastian users   37 2008-04-14 09:17 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 sebastian users   34 2008-04-14 09:17 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 sebastian users   35 2008-04-14 09:17 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 sebastian users   36 2008-04-14 09:17 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 sebastian users   37 2008-04-14 09:17 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 sebastian users   42 2008-04-14 09:17 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 sebastian users   43 2008-04-14 09:17 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 root      users   60 2008-06-25 22:33 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

$ uname -a
Linux h3110-w0r1D 2.6.22-15-generic #1 SMP Tue Jun 10 08:52:15 UTC 2008 x86_64 GNU/Linux

Gnash and Swfdeck were never installed and I verified it in the Synaptic.

Another thing, when I tried doing it manually by using ndisplugin or something like that, it said that it couldn't read the flash library file. I tried downloading from Adobe's site and replaced it, but it still doesn't work.

---

### Post by ajmorris on 2008-06-26
hi there,
what is the ouptut of about:plugins in the URL bar in firefox?

Also, you could try manually installing the driver by nspluginwrapper -i <driver> instead of manually letting nspluginwrapper search for the driver.


AJ

---

### Post by forger on 2008-06-26
> **themostunoriginalname said:**
> I tried this link:

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

and the script failed.


In hardy heron 8.04 amd64 all you do is install flashplugin-nonfree
```
sudo apt-get install flashplugin-nonfree
```

You might consider upgrading?

---

### Post by themostunoriginalname on 2008-06-26
about:plugin

No plugins installed

"nspluginwrapper -i <driver> i"

I actually did that. It said it couldn't read the .so file

"In hardy heron 8.04 amd64 all you do is install flashplugin-nonfree"

Tried Hardy Heron and found it to be not as stable as Gutsy.

---

### Post by ajmorris on 2008-06-26
> **themostunoriginalname said:**
> about:plugin

No plugins installed

"nspluginwrapper -i <driver> i"

I actually did that. It said it couldn't read the .so file


How did you install flash? nspluginwrapper -i <driver> should be able to read the .so file...
You could try copying the .so file manually to /usr/lib64/nsbrowser/plugins and renaming it with npwrapper out the front... so npwrapper.libflashplayer.so. However, you shouldnt need to do this, and running nspluginwrapper -i <driver> probably edits the .so file before copying it to that directory... did you use the flash from the ubuntu repos and run nspluginwrapper on the installed .so file from that?

AJ

---

