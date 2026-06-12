---
title: "Problems with apt after installing kubuntu-desktop"
date: 2006-11-18
forum: General Help
---

### Post by threethirty on 2006-11-18
ok everything installed except
```
libavahi-compact-libnssd1
```
and I got the error
```
E: /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb: trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour

```
and now when I just ty to update ubuntu I get this
```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

and after running the above mentioned sudo apt-get install -f i get here

```
three@Raptor:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavahi-compat-libdnssd1
The following NEW packages will be installed:
  libavahi-compat-libdnssd1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/29.8kB of archives.
After unpacking 102kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

if I hit "y" I get
```
(Reading database ... 150546 files and directories currently installed.)
Unpacking libavahi-compat-libdnssd1 (from .../libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
three@Raptor:~$ 

```

and "n" just aborts

---

### Post by threethirty on 2006-11-19
I tried reinstalling and doing it all again, and I'm getting the same problem

---

### Post by threethirty on 2006-11-21
I found a way to solve this problem you have to install Kubuntu then add the ubuntu-desktop package.

---

### Post by OrganicPanda on 2006-12-17
I'm getting this error and a re-install is not an option, what can I do?

---

