---
title: "intel hd sound issues"
date: 2008-01-29
forum: General Help
---

### Post by speel on 2008-01-29
Hey, well my problem is the inbtel hd sound issue

I tried following method J on [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
for my Pavilion dv6000 but when i came to "make" I recieved this error"

```
In file included from /home/anthony/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /home/anthony/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:76:52: error: macro "init_utsname" passed 1 arguments, but takes just 0
In file included from /home/anthony/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /home/anthony/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /home/anthony/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
/home/anthony/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c: In function ‘snd_sndstat_proc_read’:
/home/anthony/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: ‘system_utsname’ undeclared (first use in this function)
/home/anthony/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: (Each undeclared identifier is reported only once
/home/anthony/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: for each function it appears in.)
make[3]: *** [/home/anthony/alsa-driver-1.0.16rc1/acore/info_oss.o] Error 1
make[2]: *** [/home/anthony/alsa-driver-1.0.16rc1/acore] Error 2
make[1]: *** [_module_/home/anthony/alsa-driver-1.0.16rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
anthony@anthony-laptop:~/alsa-driver-1.0.16rc1$ 

```

And so I cant seem to compile, any help would be appriciated.

---

### Post by Seisen on 2008-01-29
Have you installed the build-essentials package?

```
sudo apt-get install build-essential
```

---

### Post by codesplice on 2008-01-29
To get the HD audio working on my Pavilion dv6700, I installed the linux-backports-modules package from the repos.

---

### Post by speel on 2008-01-29
Yea build-essential is installed. :), ...but is the backports module safe?

---

### Post by codesplice on 2008-01-29
I'm using it without any problem.  

The main thing is that it includes a newer version of ALSA.

---

### Post by speel on 2008-01-29
> **codesplice said:**
> I'm using it without any problem.  

The main thing is that it includes a newer version of ALSA.

Whats the name of the backport package..i guess i'll try it.

---

### Post by codesplice on 2008-01-29
linux-backports-modules, I believe.

Might be linux-backports-modules-generic on your system.

---

### Post by speel on 2008-01-29
> **codesplice said:**
> linux-backports-modules, I believe.

Might be linux-backports-modules-generic on your system.

Thanks, any instructions after install or is that it

---

### Post by codesplice on 2008-01-29
Just install it and reboot.

If it doesn't work, you can always "sudo aptitude remove linux-backports-modules" with no harm done.

---

