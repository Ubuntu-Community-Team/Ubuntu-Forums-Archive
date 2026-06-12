---
title: "Ubuntu 18.04 legacy pxe support kernel"
date: 2019-04-10
forum: General Help
---

### Post by taihong on 2019-04-10
Hi all,

I used to get diskless pxe boot server in Ubuntu 16.04 by using my own initrd.img with

[http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/linux](http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/linux)

as my kernel in pxe. and use /dev/ram0 as root file system.

```

LABEL Ubuntu 16.04.2
    kernel images/mfg/U16/linux
    append initrd=images/mfg/Ubuntu16_new.img.gz root=/dev/ram0 ramdisk_size=1048576 load_ramdisk=1

```

However, when I download the linux file from bionic (18.04), the /dev/ram0 doesn't initialize at all.

Has anyone try to do it and is there other way not to use /dev/ram0 as root file system? 

Thanks
Tai

---

