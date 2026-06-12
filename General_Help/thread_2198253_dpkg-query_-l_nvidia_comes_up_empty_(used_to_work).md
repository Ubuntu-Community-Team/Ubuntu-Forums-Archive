---
title: "dpkg-query -l nvidia* comes up empty (used to work)"
date: 2014-01-07
forum: General Help
---

### Post by efflandt on 2014-01-07
Anyone know why **dpkg-query -l nvidia*** no longer shows any nvidia related packages (it used to)? That was helpful for telling versions. I do have Nvidia graphics on 12.04 desktop and 13.10 laptop (optirun works on that). Packages installed on both were originally **nvidia-experimental-310**.

```
efflandt@xps8100-1204:~$ dpkg-query -l nvidia*
No packages found matching nvidia-pkgs.txt.

efflandt@xps8100-1204:~$ ls /usr/src
linux-headers-3.2.0-56          linux-headers-3.2.0-58
linux-headers-3.2.0-56-generic  linux-headers-3.2.0-58-generic
linux-headers-3.2.0-57          nvidia-319-updates-319.32
linux-headers-3.2.0-57-generic

efflandt@xps8100-1204:~$ ssh msi-ge60.local
Welcome to Ubuntu 13.10 (GNU/Linux 3.11.0-14-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

8 packages can be updated.
8 updates are security updates.

Last login: Tue Jan  7 19:41:59 2014 from unknown78e40026b8ac.domain_not_set.invalid

efflandt@MSI-GE60:~$ dpkg-query -l nvidia*
dpkg-query: no packages found matching nvidia-pkgs.txt

efflandt@MSI-GE60:~$ ls /usr/src
bbswitch-0.7                     linux-headers-3.11.0-13-generic
linux-headers-3.11.0-12          linux-headers-3.11.0-14
linux-headers-3.11.0-12-generic  linux-headers-3.11.0-14-generic
linux-headers-3.11.0-13          nvidia-319-updates-319.60
```

---

### Post by steeldriver on 2014-01-07
Is there a file called 'nvidia-pkgs.txt' in the current directory by any chance? if so the shell may be expanding the wildcard before passing the pattern to dpkg-query

```

$ touch nvidia-pkgs.txt
$ dpkg-query -l nvidia*
No packages found matching nvidia-pkgs.txt.

```

but

```

$ dpkg-query -l 'nvidia*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  nvidia-173     173.14.35-0ubu NVIDIA binary Xorg driver, kernel module and
un  nvidia-173-mod <none>         (no description available)
un  nvidia-173-upd <none>         (no description available)
.
.
.

```

If there were really no nvidia packages I think it would say 

```

No packages found matching **nvidia***.

```

---

### Post by efflandt on 2014-01-09
I never would have guessed that. Apparently I previously redirected the output of "dpkg-query -l nvidia*" to the file nvidia-pkgs.txt on both computers when I was comparing versions in 12.04 and 13.10. Thanks.

---

