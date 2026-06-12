---
title: "Dependency Problem with Java Installation (gcj &amp; gcj-4.2)"
date: 2008-06-28
forum: General Help
---

### Post by AhBok on 2008-06-28
Hi, I'm very new to Linux and currently I'm using Wubi Ubuntu. I'm trying to install the package gcj to be able to use Java but I keep getting this error message.

```
Setting up gcj-4.2 (4.2.3-2ubuntu6) ...
install-info: No such file or directory for Development
dpkg: error processing gcj-4.2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gcj:
 gcj depends on gcj-4.2 (>= 4.2.3-1); however:
  Package gcj-4.2 is not configured yet.
dpkg: error processing gcj (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gcj-4.2
 gcj
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Since I'm new to Linux, I don't really know what this means. I've been looking around the forum to find solution. I've already tired the sudo apt-get -f install but it's not working. I tried installing it in the Synaptic package manager but it didn't work either. The worse part is that I can't even remove gcj and gcj-4.2 from my computer.

Any kind of help would be appreciated. I'm doing a robotics project and the first step is to build a cross-compiling toolchain. I'm trying to build Java into it but this error is preventing it from happening.

Thanks!

---

### Post by minhmeoke on 2008-06-29
Interesting error message. You could try removing and reinstalling it:
```
sudo apt-get remove gcj
sudo apt-get install gcj

```

You could also try openjdk, which is like Sun's official version of Java, but without the restricted parts. Just install it using ```
sudo apt-get install openjdk-6-jdk
```.

---

### Post by AhBok on 2008-06-29
Thanks for the advice. But my problem is that I can't remove gcj right now. The command you mentioned stops with the similar error message, something to do with dependencies. I've tried removing it both from terminal and synaptic package manager but neither worked.

As for the other version, it's also preventing me to install other versions of java. Very strange. Any other versions of Java would stop half way with some error with gcj-4.2.

This is really confusing me. Can't install, reinstall, or even remove.

---

### Post by AhBok on 2008-07-01
Just to give more information, here's the error give when I use the Synaptic package manager.

E: gcj-4.2: subprocess pre-removal script returned error exit status 1

So this file/package/whatever is stuck on my computer and I have no way of removing it. And without having this, the regular gcj would give me dependency problem.

Help Please!

---

