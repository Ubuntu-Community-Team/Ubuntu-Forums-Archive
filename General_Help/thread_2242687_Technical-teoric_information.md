---
title: "Technical-teoric information"
date: 2014-09-03
forum: General Help
---

### Post by frupito on 2014-09-03
Hi everyone,
I wanted to know the kernels installed on my machine, so I typed 
```
dpkg -l | grep 'linux-image'
```
and a list of installed kernels appeared on my terminal, something like this
> 
rc  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-26-generic                   3.13.0-26.48                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP

My question is: 
someone can explain to me the meaning of the first column of this list? Sometime there is a 'ii' and sometime a 'rc'...
I've searched on the web, on the forum, on some technical article about the 'linux command line' but I didn't found anything.
Thanks for the help

---

### Post by Vaphell on 2014-09-03
[http://askubuntu.com/questions/18804/what-do-the-various-dpkg-flags-like-ii-rc-mean](http://askubuntu.com/questions/18804/what-do-the-various-dpkg-flags-like-ii-rc-mean)

```
First letter -> desired package state ("selection state"):

    u ... unknown
    i ... install
    r ... remove/deinstall
    p ... purge (remove including config files)
    h ... hold

Second letter -> current package state:

    n ... not-installed
    i ... installed
    c ... config-files (only the config files are installed)
    u ... unpacked
    f ... half-configured (configuration failed for some reason)
    h ... half-installed (installation failed for some reason)
    w ... triggers-awaited (package is waiting for a trigger from another package)
    t ... triggers-pending (package has been triggered)

Third letter -> error state (you normally shouldn't see a thrid letter):

    r ... reinst-required (package broken, reinstallation required)


```

---

### Post by frupito on 2014-09-03
Thank you Vaphell!
My search on askubuntu was useless...
thank you again

---

### Post by Impavidus on 2014-09-03
Or if you don't use grep but give dpkg an argument:```
$ dpkg --list linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Naam                               Versie                 Architecture           Omschrijving
+++-==================================-======================-======================-=========================================================================
un  linux-image                        <none>                 <none>                 (geen beschrijving beschikbaar)
un  linux-image-3.0                    <none>                 <none>                 (geen beschrijving beschikbaar)
ii  linux-image-3.13.0-33-generic      3.13.0-33.58           amd64                  Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic      3.13.0-34.60           amd64                  Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic      3.13.0-35.62           amd64                  Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generi 3.13.0-33.58           amd64                  Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generi 3.13.0-34.60           amd64                  Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generi 3.13.0-35.62           amd64                  Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                3.13.0.35.42           amd64                  Generic Linux kernel image

```See the brief explanation on the top three lines.

---

### Post by frupito on 2014-09-04
Thank you Impavidus!
Your solution has a better and more complete output!!

---

