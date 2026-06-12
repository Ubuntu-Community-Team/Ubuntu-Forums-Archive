---
title: "configure error"
date: 2014-01-05
forum: General Help
---

### Post by apos124 on 2014-01-05
I keep getting this error: 

```
hierophant@hierophant-Satellite-C655D:~$ cd ~/Downloads
hierophant@hierophant-Satellite-C655D:~/Downloads$ ls
amd-catalyst-13.11-beta V9.4-linux-x86.x86_64.run
glibc-2.18
glibc-2.18.tar.gz
glibc-build
IYOCGwP_book1.pdf
Passware
posix_ipc-0.9.6
PythonProgrammingUnabridged_mp332_A1XY6W8EDAL0E9.aa
utorrent-server-alpha-v3_3
hierophant@hierophant-Satellite-C655D:~/Downloads$ cd glibc-build
hierophant@hierophant-Satellite-C655D:~/Downloads/glibc-build$ ../glibc-2.18/configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking for readelf... readelf
checking for sysdeps preconfigure fragments... x86_64 checking whether gcc compiles in -mx32 mode by default... no

configure: running configure fragment for add-on gawk-4.1.0
configure: WARNING: you should use --build, --host, --target
configure: WARNING: you should use --build, --host, --target
checking build system type... Invalid configuration `dummy': machine `dummy' not recognized
configure: error: /bin/bash ../glibc-2.18/scripts/config.sub dummy failed
hierophant@hierophant-Satellite-C655D:~/Downloads/glibc-build$ 
```

The configure.sub file is the latest version of the script. How can I fix this?

---

### Post by CharlesA on 2014-01-05
Try here:
[http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

It looks like you don't have build-essental metapackage installed, but try the above link before doing anything.

---

### Post by apos124 on 2014-01-06
It works Thank you very much!!!!

---

### Post by claracc on 2014-01-06
As you got fixed your problem, please mark the thread as solved with "thread tools".

Thanks

---

