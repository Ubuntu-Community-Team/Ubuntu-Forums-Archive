---
title: "X server not working correctly from a Solaris machine"
date: 2008-04-04
forum: General Help
---

### Post by joper90 on 2008-04-04
If I ssh -X to another linux machine, i can then just xclock and the clock pops up.

If i ssh -X (supported?) to a Solaris machine xclock will not work i get:

$ /usr/X/bin/xclock
Error: Can't open display: 10.100.83.86:0.0
$ uname -a
SunOS galatea 5.8 Generic_117350-53 sun4u sparc SUNW,Ultra-4 Solaris
$ 

even though i have my display set, xhost give the same issue.. However I know this works, as it works from my windows machine using Xvision or CygwinX.

Any ideas?

---

### Post by Rocket2DMn on 2008-04-04
Hey joper90,
I just tested this out, and it seems to be working on the host I'm connecting to.  Are you sure the Solaris machine you are connecting to has X enabled?  Is it set to allow X to be tunneled through SSH?

---

