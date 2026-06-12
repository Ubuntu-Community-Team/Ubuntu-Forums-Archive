---
title: "Xserver crash after recent updates"
date: 2007-01-23
forum: General Help
---

### Post by Webspot on 2007-01-23
Booted up computer this morning. Noticed updates. Tried to install them. 

Instalation failed on libc.

Unticked libc which also unticked libc-i686

Installed rest of updates. Before it actually started installing though, it removed loads of packages which I didn't notice until afterwards. But these other updates still wouldn't install because it kept retying to install libc which kept failing.

So I restarted my computer. And when I started it up, I received an error and the X server didn't load.

Help!! Please :)

---

### Post by scrooge_74 on 2007-01-23
Check what error messages the Xserver says when it tries to boot, then

from the command line try sudo dpkg-reconfigure xserver-xorg

---

### Post by Webspot on 2007-01-23
I've reset the xorg configuration but still have problems when loading up. An error shows up in the X server log:

```
error opening security policy file /usr/lib/xserver/SecurityPolicy
```

---

### Post by konst88 on 2007-01-23
I think the best method to reinstall the missing packages is to install the desktop again.
Assuming you have ubuntu gnome:
```
sudo aptitude install ubuntu-desktop 
```

---

### Post by Webspot on 2007-01-23
I sorted it out in the end

[https://answers.launchpad.net/ubuntu/+ticket/3308](https://answers.launchpad.net/ubuntu/+ticket/3308)

---

### Post by knn on 2007-01-24
> **Webspot said:**
> I sorted it out in the end

[https://answers.launchpad.net/ubuntu/+ticket/3308](https://answers.launchpad.net/ubuntu/+ticket/3308)
That didn't help me. I don't have libpthread20 installed, and the original libc update went smoothly on my machine. I tried reinstalling the nvidia driver, but it doesn't work. usr/lib/xserver doesn't even exist!

Edit: I fixed it.
I checked what package is supposed to be providing /usr/lib/xserver/SecurityPolicy. It's xserver-xgl. However, the file is also installed to /usr/share/doc/xserver-xorg-core by xserver-xorg-core, so I just created the missing directory, copied the file, restarted, and everything's working now. Strange

---

