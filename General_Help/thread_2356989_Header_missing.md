---
title: "Header missing"
date: 2017-03-28
forum: General Help
---

### Post by sniper8752 on 2017-03-28
I am trying to resolve a hwloc dependency for snort 3.0 on Ubuntu 16.04.  I have been following this tutorial: [https://dangertux.wordpress.com/2011/10/12/compiling-snort-2-9-1-1-daq-0-62/](https://dangertux.wordpress.com/2011/10/12/compiling-snort-2-9-1-1-daq-0-62/)

Here is where I am at right now:

```

[COLOR=#000000][FONT=Consolas]sudo ./configure --prefix=/usr/local/snort
........
[/FONT][/COLOR]checking for wchar.h... yeschecking for dlsym in -ldl... yes
checking whether C++11 threads work without any flags... no
checking whether C++11 threads work with -pthread... yes
checking for daq_load_modules in -ldaq_static... yes
checking sfbpf.h usability... yes
checking sfbpf.h presence... yes
checking for sfbpf.h... yes
checking for sfbpf_compile in -lsfbpf... yes
checking dnet.h usability... no
checking dnet.h presence... no
checking for dnet.h... no
checking dumbnet.h usability... yes
checking dumbnet.h presence... yes
checking for dumbnet.h... yes
checking for eth_set in -ldnet... no
checking for eth_set in -ldumbnet... yes
checking for hwloc pkg-config presence... no
checking hwloc.h usability... no
checking hwloc.h presence... no
checking for hwloc.h... no
configure: error: hwloc header not found.

```

---

### Post by F3BQ3DP on 2017-03-28
*hwloc* is in the main sources repo. Have you installed it from there?

---

### Post by vasa1 on 2017-03-28
> **F3BQ3DP said:**
> *hwloc* is in the main sources repo. Have you installed it from there?
From the code posted, I think OP's trying to compile it from some source.

---

### Post by F3BQ3DP on 2017-03-28
Looks like they're compiling snort, which only seems to be asking that hwloc headers be present.

---

### Post by sniper8752 on 2017-03-29
```
sudo apt-get install hwlocReading package lists... Done
Building dependency tree
Reading state information... Done
hwloc is already the newest version (1.11.2-3).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo apt-get install hwloc-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package hwloc-dev

```

---

### Post by Impavidus on 2017-03-29
Try```
sudo apt-get install libhwloc-dev
```

---

