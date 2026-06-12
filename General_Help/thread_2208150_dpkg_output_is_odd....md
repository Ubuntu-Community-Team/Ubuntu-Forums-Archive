---
title: "dpkg output is odd..."
date: 2014-02-26
forum: General Help
---

### Post by bc.haynes on 2014-02-26
I ran **dpkg** to check installed kernels and got this:
```
ben@MissionControl:~$ dpkg -l grep linux-image
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  grep           2.10-1         GNU grep, egrep and fgrep
un  linux-image    <none>         (no description available)

```
What does it mean?
Does it mean that an update got "stuck" and didn't install?

---

### Post by Frogs Hair on 2014-02-26
I get the same output but am unfamiliar with command . My system is fully updated and see no errors when running sudo apt-get update which there would be if I had partially installed packages.

Edit :I changed the command a bit. 

```
dpkg --list | grep linux-generic
ii  linux-generic-lts-raring                       3.8.0.37.37                                   Generic Linux kernel image and headers 
```

---

### Post by steeldriver on 2014-02-26
The intended command is probably

```
dpkg -l [COLOR=#0000ff]**|**[/COLOR] grep linux-image
```

i.e. [COLOR=#0000ff]pipe[/COLOR] the output of [FONT=courier new]*dpkg -l*[/FONT] to [FONT=courier new]*grep*[/FONT]

---

### Post by Frogs Hair on 2014-02-26
> **steeldriver said:**
> The intended command is probably

```
dpkg -l [COLOR=#0000ff]**|**[/COLOR] grep linux-image
```

i.e. [COLOR=#0000ff]pipe[/COLOR] the output of [FONT=courier new]*dpkg -l*[/FONT] to [FONT=courier new]*grep*[/FONT]

:D

```
dpkg -l | grep linux-image
ii  linux-image-3.8.0-37-generic                   3.8.0-37.53~precise1                          Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-raring                 3.8.0.37.37                                   Generic Linux kernel image

```

---

### Post by deadflowr on 2014-02-26
You can go without a pipe if you drop the grep
and add a *
```
dpkg -l linux-image*
```

---

### Post by bc.haynes on 2014-02-26
**+1 steeldriver**  My bad.... I should have looked at the command closer. (I had the right command in mind, just didn't implement it.)

Thanks, all you folks.

---

