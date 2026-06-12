---
title: "fwupdate - Needed ?"
date: 2020-02-21
forum: General Help
---

### Post by ubuntwone on 2020-02-21
All,
Quick question..
Currently on Ubuntu 18.04.4 LTS

My apt-get update/upgrade came back with **fwupdate** and **fwupdate-signed** as held back
The current installed version is **12-3bionic2**

Do I use
 ```
 apt-get --with-new-pkgs upgrade
```

to fix this?

Also, is this update required. I suppose Im also asking why its stalled. Its not asked for any of the dependencies:
```
libc6 (>= 2.4), libefivar1 (>= 34), libfwup1 (= 12-3bionic2), libpopt0 (>= 1.14), efibootmgr, e2fsprogs
```
 
Thoughts, comments and suggestions very welcome here
Thanks.

---

### Post by oldfred on 2020-02-21
Not all systems support UEFI update from Linux.

If your system not on list you do not now need it. And most vendors are not adding older systems, just the newer ones. 
So if not on list now, it is unlikely to be on list in future. Then you may not need fwupd.

[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

