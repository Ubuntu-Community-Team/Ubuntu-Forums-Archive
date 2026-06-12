---
title: "/usr/bin/ld: cannot find -lz"
date: 2013-02-08
forum: General Help
---

### Post by omid123 on 2013-02-08
Hi,
When i compile GPGPU-sim ,  i get this error:

/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make[2]: *** [obj_opt/mcpat] Error 1
make[2]: Leaving directory `/home/omid/Gpgpu-sim/v3.x/src/gpuwattch'
make[1]: *** [opt] Error 2
make[1]: Leaving directory `/home/omid/Gpgpu-sim/v3.x/src/gpuwattch'
make: *** [mcpat] Error 2

Appreciate any help. Thanks!

---

### Post by schragge on 2013-02-08
```
sudo apt-get install zlib1g-dev
```

---

### Post by omid123 on 2013-02-09
> **schragge said:**
> ```
sudo apt-get install zlib1g-dev
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
zlib1g-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 591 not upgraded.
:roll::roll::roll::roll:

/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make[2]: *** [obj_opt/mcpat] Error 1
make[2]: Leaving directory `/home/omid/Gpgpu-sim/v3.x/src/gpuwattch'
make[1]: *** [opt] Error 2
make[1]: Leaving directory `/home/omid/Gpgpu-sim/v3.x/src/gpuwattch'
make: *** [mcpat] Error 2
](*,)](*,)](*,)](*,)

---

### Post by schragge on 2013-02-11
Look at the output of
```
ld --verbose|grep SEARCH_DIR
```and compare it with
```
find /usr/lib -name libz.so -exec dirname {} \;
```

If nothing else helps, try to build the program with
```
LIBRARY_PATH=[color=green]/usr/lib/x86_64-linux-gnu[/color] make
```
Adjust the [color=green]green[/color] part to what the *find* above shows.

---

