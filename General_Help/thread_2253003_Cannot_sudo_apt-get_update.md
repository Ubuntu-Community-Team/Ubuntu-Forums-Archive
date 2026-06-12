---
title: "Cannot sudo apt-get update"
date: 2014-11-16
forum: General Help
---

### Post by Guyofdoom42 on 2014-11-16
For some reason, I can't use ```
sudo apt-get update
```

Here's what is spits out:

```
XXXXXXX@XXXXXXXX:~$ sudo apt-get update
/usr/lib/apt/methods/https: error while loading shared libraries: libapt-pkg.so.4.12: cannot open shared object file: No such file or directory
/usr/lib/apt/methods/https: error while loading shared libraries: libapt-pkg.so.4.12: cannot open shared object file: No such file or directory
E: Method https has died unexpectedly!
E: Sub-process https returned an error code (127)
E: Method /usr/lib/apt/methods/https did not start correctly
E: Method https has died unexpectedly!
E: Sub-process https returned an error code (127)
E: Method /usr/lib/apt/methods/https did not start correctly
```

Please help!

---

### Post by matt_symes on 2014-11-16
Hi

libapt-pkg.so.4.12 is part of the package libapt-pkg4.12

Do you still have this package installed ?

You may want to reinstall it and see if that fixes the issue.

edit: also check if it's just the symlink that has gone. 
```

dpkg -S libapt-pkg.so.4.12
```

The above command will show the symlink and also which library versio the symlink points to. Check to see if the library exists on your PC

kind regards

---

### Post by Guyofdoom42 on 2014-11-16
I think this is good...

```
dpkg -S libapt-pkg.so.4.12
```

---

### Post by matt_symes on 2014-11-17
Hi

> **Guyofdoom42 said:**
> I think this is good...

```
dpkg -S libapt-pkg.so.4.12
```

I'm not quite sure what you mean by this.

can you post the output of this command into your next post.

Copy and paste it from this post into the terminal and copy and paste the output from the terminal into your next post.

```
while read i; do file "$i"; done < <(dpkg -S libapt-pkg.so.4.12 | cut -d" " -f2)
```

Can you also post the output of this command

```
dpkg -l libapt-pkg4.12
```

Kind regards

---

### Post by Guyofdoom42 on 2014-11-17
When I do ```
while read i; do file "$i"; done < <(dpkg -S libapt-pkg.so.4.12 | cut -d" " -f2
``` It spits out ```
while read i; do file "$i"; done < <(dpkg -S libapt-pkg.so.4.12 | cut -d" " -f2)
/usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=0xc0299002b8bfdf3bc24fc5539c941814add4a07a, stripped
/usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12: symbolic link to `libapt-pkg.so.4.12.0'
```

And ```
 dpkg -S libapt-pkg.so.4.12

```

Gives me ```
libapt-pkg4.12: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
libapt-pkg4.12: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12
```

Lastly, ```
 dpkg -S libapt-pkg.so.4.12 
``` gives me ```
 Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libapt-pkg4.12 0.8.16~exp12ub package managment runtime library


```

---

### Post by mc4man on 2014-11-17
Maybe show this to see if apt & libapt-pkg are same version (they may not have to be same version but certainly not a bad idea to be
```
apt-cache policy libapt-pkg4.12 apt
```

---

### Post by matt_symes on 2014-11-17
Hi

As well as mc4man's check please post the output of

```
ldd /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12
```

EDIT: and another check

```
ls -l /usr/lib/apt/methods
```

Kind regards

---

