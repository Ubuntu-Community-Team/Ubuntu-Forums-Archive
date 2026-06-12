---
title: "How to add iptable support to the kernel (for Wheezy/Sid release)"
date: 2014-05-21
forum: General Help
---

### Post by jared20 on 2014-05-21
Hey guys,

I am running an ARM processor (similar to the raspberry pi) and my kernel doesnt natively support iptables. If I run apt-get install iptables, it successfully installs but NAT tables are unable to be created and the more advanced stuff cannot be used. When I try add a NAT table, it specifically mentions that I might not have support for iptables in my kernel.

My question: How do I just add the ARM iptables support to my kernel?

My details:

Welcome to Linaro 12.11 (GNU/Linux 3.4.29+ armv7l)
Wheezy/Sid (cat /etc/debian_version)
Already installed the iptables package (apt-get install iptables), just need kernel support.

Thanks a mil!

Jared

---

### Post by ian-weisser on 2014-05-23
Please show us exactly how you are trying to add a NAT table, and the exact error message you get in response.

'Just' adding iptables support isn't flipping a switch - it could mean compiling a custom kernel.
And that seems unnecessary; iptables support has been included in the kernel for a very long time.

---

### Post by Zorael on 2014-05-23
And it's not merely a permissions issue, aye? Also do note that the **iptable_nat** module needs to be running, if for whatever reason it hasn't been loaded automatically.
```
$ iptables -t nat -nvxL
iptables v1.4.21: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.  *# <-- pish posh*

$ **sudo** iptables -t *nonsensetable* -nvxL
iptables v1.4.21: can't initialize iptables table `*nonsensetable*': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

$ sudo modprobe iptable_*nonsensetable*
$ sudo iptables -t *nonsensetable* -nvxL
*[...]*
```

---

