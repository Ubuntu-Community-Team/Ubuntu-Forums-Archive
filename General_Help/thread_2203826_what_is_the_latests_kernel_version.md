---
title: "what is the latests kernel version"
date: 2014-02-05
forum: General Help
---

### Post by J_Me on 2014-02-05
Can someone tell me what the latests kernel version is, I googled and got this from kernel.org
```

The latest mainline 3 version of the Linux kernel is:         3.14-rc1
The latest stable 3.13 version of the Linux kernel is:        3.13.1
The latest stable 3.12 version of the Linux kernel is:        3.12.9
The latest stable 3.11 version of the Linux kernel is:        3.11.10 (EOL)
The latest longterm 3.10 version of the Linux kernel is:      3.10.28
The latest longterm 3.4 version of the Linux kernel is:       3.4.78
The latest longterm 3.2 version of the Linux kernel is:       3.2.54
The latest longterm 3.0 version of the Linux kernel is:       3.0.101 (EOL)
The latest longterm 2.6.34 version of the Linux kernel is:    2.6.34.14
The latest longterm 2.6.32 version of the Linux kernel is:    2.6.32.61
The latest linux-next version of the Linux kernel is:         next-20140205


```
and this
```
mainline:     3.14-rc1     2014-02-03 
stable:     3.13.1         2014-01-29 
stable:     3.12.9         2014-01-25 
stable:     3.11.10 [EOL]     2013-11-29 
longterm:     3.10.28     2014-01-25 
longterm:     3.4.78         2014-01-29 
longterm:     3.2.54         2014-01-03
longterm:     3.0.101 [EOL]     2013-10-22 
longterm:     2.6.34.14     2013-01-16 
longterm:     2.6.32.61     2013-06-10 
linux-next:     next-20140205     2014-02-05 


```
Looks a bit confusing don't you think. I'm running kubuntu 12.04 LTS

---

### Post by Dave_L on 2014-02-05
For Ubuntu 12.04, the latest kernel in the standard repositories is 3.11.0. If you want to install it, install the package "linux-generic-lts-saucy".

This applies to Ubuntu. I suppose it applies to Kubuntu too, but I'm not sure.

---

### Post by J_Me on 2014-02-05
Thanks for the quick reply but does'nt EOL stand for End Of Life
```

stable:     3.11.10 [EOL]     2013-11-29

```

---

### Post by Dave_L on 2014-02-05
Yes, but that's the "upstream" kernel.  There's an Ubuntu Kernel Team that continues to apply fixes to the supported kernels in the Ubuntu repositories.

[https://wiki.ubuntu.com/Kernel/FAQ#Kernel.2BAC8-FAQ.2BAC8-GeneralUbuntuDelta.What_differentiates_the_Ubuntu_Kernel_from_the_upstream_Linux_Kernel.3F](https://wiki.ubuntu.com/Kernel/FAQ#Kernel.2BAC8-FAQ.2BAC8-GeneralUbuntuDelta.What_differentiates_the_Ubuntu_Kernel_from_the_upstream_Linux_Kernel.3F)

Actually, according to [https://wiki.ubuntu.com/Kernel/FAQ#Kernel.2BAC8-FAQ.2BAC8-GeneralVersionRunning.How_can_we_determine_the_version_of_the_running_kernel.3F](https://wiki.ubuntu.com/Kernel/FAQ#Kernel.2BAC8-FAQ.2BAC8-GeneralVersionRunning.How_can_we_determine_the_version_of_the_running_kernel.3F) :
```
$ cat /proc/version_signature
Ubuntu 3.11.0-15.25~precise1-generic **3.11.10**
```

So the kernel provided by the package "linux-generic-lts-saucy" is based on the upstream kernel 3.11.10, not 3.11.0 as I stated in my post above.

---

### Post by grahammechanical on 2014-02-05
Please do not confuse what Linux kernel developers mean by End Of Life and what Ubuntu Developers mean by it.

> [COLOR=#33290A][FONT=oxygen][SIZE=2]As kernels move from the "mainline" into the "stable" category, two things can happen:[/SIZE][/FONT][/COLOR]

[LIST]
[*][SIZE=2]They can reach "End of Life" after a few bugfix revisions, which means that kernel maintainers will release no more bugfixes for this kernel version, or[/SIZE]
[*][SIZE=2]They can be put into "longterm" maintenance, which means that maintainers will provide bugfixes for this kernel revision for a much longer period of time.[/SIZE]
[/LIST]
[COLOR=#33290A][FONT=oxygen][SIZE=2]If the kernel version you are using is marked "EOL," you should consider upgrading to the next major version as there will be no more bugfixes provided for the kernel version you are using.[/SIZE][/FONT][/COLOR]


[https://www.kernel.org/category/faq.html](https://www.kernel.org/category/faq.html)

A Ubuntu Long Term Support (LTS) version will get 4 major upgrades to the kernel hardware enablement stack in the first 2 years of its support period. This keeps the LTS release up to date with Linux hardware support for the latest hardware. By which time the next LTS has been released.

In a few days Ubuntu 12.04.4 will be released and it will have the Linux kernel hardware enablement stack that is in Ubuntu 13.10 and that includes the kernel (whatever version that is).

> [SIZE=2][COLOR=#000000][FONT=Ubuntu]We have uploaded a new 3.13.0-7.25 Trusty kernel to the archive. This includes a rebase to the first v3.13.1 upstream stable release. We have also merged the powerpc and lowlatency flavors back into our main repo. I would also like to note that the 12.04.4 release comes out this Thurs. This will officially introduce the Saucy hardware enablement kernel back into Precise.[/FONT][/COLOR][/SIZE]

[http://discourse.ubuntu.com/t/kernel-team-meeting-minutes-february-04-2014/1445](http://discourse.ubuntu.com/t/kernel-team-meeting-minutes-february-04-2014/1445)

The latest kernel as far as Ubuntu developers are concerned is Kernel 3.13.0-7.25 and that is based upon Linux kernel 3.13.1. Ubuntu developers add a designation of their own as a means of identifying which bugs belong to which kernel update.

It remains to be seen if Ubuntu 14.04 will release with kernel 3.14.

Regards.

---

### Post by J_Me on 2014-02-05
Okay thanks Dave_L and grahammechanical

---

