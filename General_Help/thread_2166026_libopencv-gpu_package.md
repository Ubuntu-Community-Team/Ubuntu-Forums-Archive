---
title: "libopencv-gpu package?"
date: 2013-08-07
forum: General Help
---

### Post by akos.maroy on 2013-08-07
Hi,

I wonder what happened to the libopecv-gpu and libopencv-gpu-dev packages for ubuntu 13.04? I see references to them online, but my apt-cache search or apt-get install is not finding anything about them :(


Akos

---

### Post by slickymaster on 2013-08-07
> **akos.maroy said:**
> Hi,

I wonder what happened to the libopecv-gpu and libopencv-gpu-dev packages for ubuntu 13.04? I see references to them online, but my apt-cache search or apt-get install is not finding anything about them :(


Akos
 That's strange:```
~$ apt-cache search libopencv-gpu-dev
libopencv-gpu-dev - development files for libopencv-gpu
``````
~$ sudo apt-get install --dry-run libopencv-gpu-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libopencv-core-dev libopencv-core2.4 libopencv-gpu2.4 libtbb2
The following NEW packages will be installed:
  libopencv-core-dev libopencv-core2.4 libopencv-gpu-dev libopencv-gpu2.4
  libtbb2
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Inst libtbb2 (4.0+r233-1 Ubuntu:13.10/saucy [i386])
Inst libopencv-core2.4 (2.4.5+dfsg-0ubuntu2 Ubuntu:13.10/saucy [i386])
Inst libopencv-core-dev (2.4.5+dfsg-0ubuntu2 Ubuntu:13.10/saucy [i386])
Inst libopencv-gpu2.4 (2.4.5+dfsg-0ubuntu2 Ubuntu:13.10/saucy [i386])
Inst libopencv-gpu-dev (2.4.5+dfsg-0ubuntu2 Ubuntu:13.10/saucy [i386])
Conf libtbb2 (4.0+r233-1 Ubuntu:13.10/saucy [i386])
Conf libopencv-core2.4 (2.4.5+dfsg-0ubuntu2 Ubuntu:13.10/saucy [i386])
Conf libopencv-core-dev (2.4.5+dfsg-0ubuntu2 Ubuntu:13.10/saucy [i386])
Conf libopencv-gpu2.4 (2.4.5+dfsg-0ubuntu2 Ubuntu:13.10/saucy [i386])
Conf libopencv-gpu-dev (2.4.5+dfsg-0ubuntu2 Ubuntu:13.10/saucy [i386])
```

---

### Post by akos.maroy on 2013-08-07
interesting, I still don't have it:

```

$ lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

$ apt-cache search libopencv-gpu-dev

```

---

### Post by timredfern on 2013-12-02
this is missing for me too

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
$ apt-cache search libopencv-gpu-dev

---

### Post by timredfern on 2013-12-02
also, on the page

[https://launchpad.net/ubuntu/raring/amd64/libopencv-gpu-dev/2.3.1-11ubuntu2](https://launchpad.net/ubuntu/raring/amd64/libopencv-gpu-dev/2.3.1-11ubuntu2)

"Downloadable files
amd64 build of opencv 2.3.1-11ubuntu2 in ubuntu quantal RELEASE produced these files:
libopencv-gpu-dev_2.3.1-11ubuntu2_amd64.deb (84.9 KiB)"

why is a file produced by quantal here in the raring repo page?

---

