---
title: "Yet Another lirc Install Problem"
date: 2006-11-10
forum: General Help
---

### Post by igb on 2006-11-10
I am trying to install lirc as per [https://help.ubuntu.com/community/Install_Lirc_Edgy]("https://help.ubuntu.com/community/Install_Lirc_Edgy")

It all seems to work up to the point where I try to start lircd, when I get the following error:

```
I couldn't load the required kernel modules     ##"
                echo "## You should install lirc-modules-source to build ##"
                echo "## kernel support for your hardware.
```

I have built and installed the kernel modules as described in the wiki without error. I can also modprobe lirc_mceusb2 OK.

I guess the init script is not looking in the correct place for the kernel modules. How can I fix it?

Ian.

---

### Post by igb on 2006-11-11
I have made some progress. Since I removed superm1 modified deb's, since I don't need them for mceusb2. Re-installed and recompiled and now I can start lircd. Howver, when I run irw to try and see if it works I get no output. It appears as though irw is killing the lirc process, since it disappears as soon as I run irw.

Any ideas what's happening?

Ian.

---

