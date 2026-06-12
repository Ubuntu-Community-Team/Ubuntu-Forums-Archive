---
title: "config for ubuntu kernel?"
date: 2004-11-10
forum: General Help
---

### Post by adamvert on 2004-11-10
Hi

I'm trying to install fuse, so that I can use gnomevfs-mount, and I've synaptically got the linux-source-2-6-8-1 package so that I can compile it (fuse, I mean).  But the kernel source has not been config'ed, and I don't know how to config it to fit the current kernel.

So is it possible to get hold of the config for the ubuntu kernel that I'm currently using (ie. 2.6.8.1-3-386, the default)?

(Or am I barking up the wrong tree? :)

thanks
Adam

---

### Post by HungSquirrel on 2004-11-10
The config files are at /boot/config-'uname -r' .  In the case of the default, it is at /boot/config-2.6.8.1-3-386 .

---

### Post by adamvert on 2004-11-10
Ah, so it is...

And so should I symlink that into the src directory?  If so, where?

thanks
Adam

---

### Post by HungSquirrel on 2004-11-10
Rather than symlink it, I would copy it, e.g. :

```
sudo cp /boot/config-2.6.8.1-3-386 /usr/src/linux-2.6.9/.config
```

(This assumes you are going to build a custom 2.6.9 kernel and have untared the kernel in /usr/src.)  That way, you don't modify the original when you configure your kernel.  From there, configure your kernel as normal after loading the config file.  I am assuming you know how to do that.  :)

---

