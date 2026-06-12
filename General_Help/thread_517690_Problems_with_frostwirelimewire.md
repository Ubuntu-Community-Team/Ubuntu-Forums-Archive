---
title: "Problems with frostwire/limewire"
date: 2007-08-04
forum: General Help
---

### Post by adwait on 2007-08-04
Hi,

I have a weird problem with both frostwire and limewire. Both of them freeze at the splash screen when I try to start them and if my PPPoE connection is running. On the other hand, if I disconnect from the PPPoE, then start them and then turn my connection on again there are no problems. I have the JRE version 1.5

Thanks..

---

### Post by whistlerspa on 2007-08-04
I think it's almost certain to be a Java related problem. I had similar issues a while back and finally solved it by uninstalling and then reinstalling Java.  Make sure that v 1.4 is not still installed as well.  I use V1.6 myself.

I used the *.rpm version of Frostwire over  *.tgz  version and then used Alien to turn it into a g-debi executable *.deb - but this may not be significant.

---

### Post by adwait on 2007-08-04
Alright, I solved the probelm by tiral and error. For anyone else having this problem, here's what I did:

First off got frostwire started by disconnecting the PPPoE.

In the Preferences>Advanced, selected the "Do Nothing" option for port forwarding

---

