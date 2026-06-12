---
title: "loopback module - Linux 2.6.22-rc3"
date: 2007-05-27
forum: General Help
---

### Post by Xubus on 2007-05-27
The Gentoo forums never seem to be able to help, these forums seem much more active.

Okay, down to business:

Has anyone gotten loopback devices working with 2.6.22? I get complaints that loopback is not supported, yet lsmod confirms that I've loaded it:
```
lsmod
Module                  Size  Used by
loop                   13956  0 

```

Mounting a disc image doesn't work, which depends on loopback::
```
mount: could not find any device /dev/loop#
```

I restarted udevd after loading loop, though I doubt that could make a difference. It works fine with 2.6.21.

Edit: Solved.
It's definitely a fault, but only so far as creation of the devices fails. Solve it with
```
mknod /dev/loop0 b 7 0
```

---

