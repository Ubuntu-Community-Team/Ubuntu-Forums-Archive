---
title: "exim displays 'Permission denied' gnome-keyring warning"
date: 2012-12-23
forum: General Help
---

### Post by petru.marginean on 2012-12-23
Hi,

I started to get a warning when running exim:

```
$> /usr/sbin/exim user@gmail.com
WARNING: gnome-keyring:: couldn't connect to: /run/user/petrum/keyring-iwTi9c/pkcs11: Permission denied

```Exim still works, but the warning is annoying.

I use exim version 4.80 on ubuntu 12.10:
```
$> /usr/sbin/exim --version | head -n 1
Exim version 4.80 #3 built 25-Oct-2012 14:21:06
WARNING: gnome-keyring:: couldn't connect to: /run/user/petrum/keyring-iwTi9c/pkcs11: Permission denied

$> uname -a
Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux

```Please help,
PM

---

### Post by fdrake on 2012-12-23
> **petru.marginean said:**
> Hi,

I started to get a warning when running exim:

```
$> /usr/sbin/exim user@gmail.com
WARNING: gnome-keyring:: couldn't connect to: /run/user/petrum/keyring-iwTi9c/pkcs11: Permission denied

```Exim still works, but the warning is annoying.

I use exim version 4.80 on ubuntu 12.10:
```
$> /usr/sbin/exim --version | head -n 1
Exim version 4.80 #3 built 25-Oct-2012 14:21:06
WARNING: gnome-keyring:: couldn't connect to: /run/user/petrum/keyring-iwTi9c/pkcs11: Permission denied

$> uname -a
Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux

```Please help,
PM

these are just warning not errors.. so nothing to worry about it.. probably some bug in the code...

---

