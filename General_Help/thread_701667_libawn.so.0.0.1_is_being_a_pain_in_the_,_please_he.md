---
title: "libawn.so.0.0.1 is being a pain in the ***, please help!"
date: 2008-02-19
forum: General Help
---

### Post by Muscar on 2008-02-19
I started to install the AWN pacages from SPM, and it wanted to update, i got this error:

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

So i did: ```

 sudo apt-get install -f
```

then i got this error:

```
Unpacking libawn0 (from .../libawn0_0.2.1-0ubuntu1~gutsy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
Errors were encountered while processing:
 /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help me!! :confused:

---

### Post by Muscar on 2008-02-19
hello?

---

### Post by nilarimogard on 2008-02-19
Go to /var/cache/apt/archives/ and try to delete libawn0_0.2.1-0ubuntu1~gutsy1_i386.deb. If that doesn't work, try to delete /usr/lib/libawn.so.0.0.1. Then reinstall avant-window-navigator and all it needs to run. I had that problem too, and i don't remember how, but solved the problem somehow.

---

### Post by chaddaniels on 2008-02-26
I got that message after installing the awn-curves branch and then trying to uninstall it sometime later.  I am unsure what I did wrong, but I received the same message as you.  To resolve the issue, I had to use:

```
sudo apt-get remove libawn-bzr python-libawn-bzr avant-window-navigator
```

I hope that helps solve the issue for someone else.

---

