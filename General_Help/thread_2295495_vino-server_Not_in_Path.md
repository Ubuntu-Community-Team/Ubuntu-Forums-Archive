---
title: "vino-server Not in Path"
date: 2015-09-19
forum: General Help
---

### Post by Jason_Hunter on 2015-09-19
I am not figuring this vino-server thing out;)

Let's start from the beginning. 

What's the reason that vino-server is not in PATH?

It's located in /usr/lib/vino

Why is the binary located in a lib path?

---

### Post by steeldriver on 2015-09-19
I think it's just because the program is intended to be controlled through dbus - rather than by the user directly

If you poke around in /usr/lib you'll see that it's actually not that uncommon for applications to place 'helper' programs of one sort or another in a /lib directory

---

