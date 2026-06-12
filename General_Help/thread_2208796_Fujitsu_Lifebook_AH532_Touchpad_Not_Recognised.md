---
title: "Fujitsu Lifebook AH532 Touchpad Not Recognised"
date: 2014-03-02
forum: General Help
---

### Post by JackW24 on 2014-03-02
Ubuntu 13.10, Fujitsu Lifebook AH532

Touchpad appearing as PS/2 Mouse under xinput --list, so no multi-touch or scroll support or anything like that.

Have tried installing alternate driver as described in this link:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1041916](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1041916)

(this comment: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1041916/comments/14](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1041916/comments/14))

but it fails on the build step (sudo dkms build psmouse/alps-dst-1.0) with 

```

Error! Bad return status for module build on kernel: 3.11.0-15-generic (x86_64)
Consult /var/lib/dkms/psmouse/alps-dst-1.0/build/make.log for more information.

```

make.log mentioned contains the following:

```

DKMS make.log for psmouse-alps-dst-1.0 for kernel 3.11.0-15-generic (x86_64)
Sun Mar  2 14:17:16 GMT 2014
make: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
scripts/Makefile.build:44: /var/lib/dkms/psmouse/alps-1.3/build/src/Makefile: No such file or directory
make[1]: *** No rule to make target `/var/lib/dkms/psmouse/alps-1.3/build/src/Makefile'. Stop.
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'

```

Any help greatly appreciated, I'm stumped!

---

