---
title: "Download stuck"
date: 2008-04-25
forum: General Help
---

### Post by hopefull on 2008-04-25
Hi

The problem I have is that recently I tried to load some software with synaptic but my internet connection went down and I appear to be stuck. When I try to reload synpatic I get this message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run this command I become stuck on this line and my desktop tends to freeze up
Setting up tor (0.1.2.17-1) ...
debian-tor uid check: ok
debian-tor homedir check: ok
chown: cannot access `/var/run/tor': No such file or directory
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libghc6-gtk-dev (0.9.12-0ubuntu1.1) ...
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/gtk-0.9.12/gtk.package.conf" ... done.
building GHCi library /usr/lib/haskell-packages/ghc6/lib/gtk-0.9.12/HSgtk.o...
Does this just take a long time to download -i have waited several hours- or have I made some form of mistake?

---

### Post by forestpixie on 2008-04-25
Did you run it as root

```
sudo dpkg --configure -a
```

---

### Post by hopefull on 2008-04-25
I did [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

