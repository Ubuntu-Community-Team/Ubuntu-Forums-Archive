---
title: "forcedeth driver for network card"
date: 2008-02-14
forum: General Help
---

### Post by Peter09 on 2008-02-14
Hi,
can any one advise me on how to get my card running at 1GB speeds. I know that it is capable of doing this using the forcedeth driver. However by default it is coming up as 100 Mb. 

Using Wicd, which shows a list of drivers, the Forcedeth driver is not shown. How can I set this up?


Doing an lspci on my system shows that my ethernet card is
**00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)**

Doing Modprobe -l | grep forcedeth
 I get
**/lib/modules/2.6.22-14-generic/kernel/drivers/net/forcedeth.ko**

Any advice appreciated.

---

### Post by kesman on 2008-02-14
using 1GB network requires a 1GB router also, do you have that?

---

### Post by Peter09 on 2008-02-14
:) I have a 1GB switch with two NAS drives attached, both with 1GB interfaces ....... the Router is 100Mb - but is not in this loop:)

---

### Post by Peter09 on 2008-02-15
Bump

---

### Post by Peter09 on 2008-02-16
bump

---

