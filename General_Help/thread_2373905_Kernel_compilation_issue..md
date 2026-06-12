---
title: "Kernel compilation issue."
date: 2017-10-10
forum: General Help
---

### Post by smithbox on 2017-10-10
cat /proc/version             = [COLOR=#ff0000]*Linux version 4.10.0-19-generic (buildd@lcy01-13) (gcc version 6.3.0 20170321 (Ubuntu 6.3.0-10ubuntu1) ) #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017*[/COLOR]

  
 
  cat /etc/issue                   = [COLOR=#ff0000]*Ubuntu 17.04 \n \l*[/COLOR]
  
 
  cat /etc/debian_version  =[COLOR=#ff0000] [/COLOR][COLOR=#ff0000]*stretch/sid*[/COLOR]

  
 
  uname -r                        = [COLOR=#ff0000]*4.10.0-19-generic*[/COLOR]
In spite of all my efforts (2 days) during Kernel compilation [https://www.howtoforge.com/kernel_compilation_ubuntu](https://www.howtoforge.com/kernel_compilation_ubuntu) I,am not able to create file " linux-headers - 4.13.5 new "
Instead notice:
> linux-4.13.5/debian/linux-headers-4.13.5-jack1/usr/share/doc/linux-headers-4.13.5-jack1/
install -p    -o root -g root  -m  644 REPORTING-BUGS                  /usr/src/linux-4.13.5/debian/linux-headers-4.13.5-jack1/usr/share/doc/linux-headers-4.13.5-jack1/
install: cannot stat 'REPORTING-BUGS': No such file or directory
debian/ruleset/targets/headers.mk:40: recipe for target 'debian/stamp/install/linux-headers-4.13.5-jack1' failed
make[1]: *** [debian/stamp/install/linux-headers-4.13.5-jack1] Error 1
make[1]: Leaving directory '/usr/src/linux-4.13.5'
debian/ruleset/local.mk:102: recipe for target 'kernel_headers' failed
make: *** [kernel_headers] Error 2
Who has more experience and help?

Regards.

---

### Post by sebastian-sjoholm on 2017-10-21
Hi,

I got the exactly the same issue on two different machines,

install -p    -o root -g root  -m  644 REPORTING-BUGS                  /home/ubuntu/linux-4.10/debian/linux-headers-4.10.0/usr/share/doc/linux-headers-4.10.0/
install: cannot stat 'REPORTING-BUGS': No such file or directory
debian/ruleset/targets/headers.mk:40: recipe for target 'debian/stamp/install/linux-headers-4.10.0' failed
make[1]: *** [debian/stamp/install/linux-headers-4.10.0] Error 1
make[1]: Leaving directory '/home/ubuntu/linux-4.10'
debian/ruleset/local.mk:102: recipe for target 'kernel_headers' failed
make: *** [kernel_headers] Error 2
ubuntu@6560b:~/linux-4.10$

The primary reason seem to be that the file "REPORTING-BUGS" is missing, and that the script 'headers.mk' is expecting this file to exists in the source root directory.

So I did re-create it;

ubuntu@6560b:~/linux-4.10$ touch REPORTING-BUGS
ubuntu@6560b:~/linux-4.10$

And the executed the run again, and it completed without problems, the "REPORTING-BUGS" is executed below without issues.

install -p    -o root -g root  -m  644 REPORTING-BUGS                  /home/ubuntu/linux-4.10/debian/linux-headers-4.10.0/usr/share/doc/linux-headers-4.10.0/
install -p    -o root -g root  -m  644 README                          /home/ubuntu/linux-4.10/debian/linux-headers-4.10.0/usr/share/doc/linux-headers-4.10.0/

Now, since this file has no function to the kernel itself, one can wonder if the fault is in the source (it is missing there) or in the 'headers.mk' which is referring to it.

I tried both 4.10.0 and 4.13.8, so it is clear that this file does not exists in the source anymore, so I am guessing that this should be fixed in the 'headers.mk'?

Regards,
Sebastian

---

### Post by jeremy31 on 2017-10-21
Why are you trying to compile kernels?  You can find precompiled kernels with Ubuntu patches at [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)  They aren't recommended for production machines but intended to be used in testing and for bug fixes

smithbox, I don't think it is possible to create  linux-headers - 4.13.5 new, try something like  linux-headers - 4.13.5-new without the space

---

### Post by sebastian-sjoholm on 2017-10-21
> **jeremy31 said:**
> Why are you trying to compile kernels?  You can find precompiled kernels with Ubuntu patches at [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)  They aren't recommended for production machines but intended to be used in testing and for bug fixes

My primary reason is that I need to do some changes in kernel modules so I can test and add new hardware to be supported.

-Sebastian

---

