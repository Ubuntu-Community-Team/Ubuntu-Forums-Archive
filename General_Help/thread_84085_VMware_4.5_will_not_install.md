---
title: "VMware 4.5 will not install"
date: 2005-10-30
forum: General Help
---

### Post by jaa1180 on 2005-10-30
I have tried a few different things but still getting this error message..
```
root@jeff1:/home/jeff/vmware45# vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl
with CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

```

Any ideas anyone?:confused:

---

### Post by JediPottsy on 2005-10-30
you may want to download and install the old gcc

use synaptic and search for 3.4.5 in version and then select gcc

---

### Post by jaa1180 on 2005-10-30
I found 
[http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware](http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware)
and that worked.. except for the kernel-headers.

It is giving a different error message.
```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-9-386

The path "/usr/src/linux-headers-2.6.12-9-386" is an existing directory, but it
does not contain at least one of these directories "linux", "asm", "net" as
expected.

```
Not sure what to do now...

---

### Post by plb on 2005-10-30
try /usr/src/linux-headers-2.6.12-9-386/include

---

### Post by jaa1180 on 2005-10-30
Nope.... that did not work..
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-9-386/include

The path "/usr/src/linux-headers-2.6.12-9-386/include" is an existing directory,
but it does not contain at least one of these directories "linux", "asm", "net"
as expected.
```

I am doing something wrong... I know.

---

### Post by jaa1180 on 2005-10-30
look at this... unusual..
```

root@jeff1:/usr/src/linux-headers-2.6.12-9-386/include# ls -l
total 28
lrwxrwxrwx    1 root root    41 2005-10-30 11:04 acpi -> ../../linux-headers-2.6.12-9/include/acpi
lrwxrwxrwx    1 root root     8 2005-10-30 11:04 asm -> asm-i386
lrwxrwxrwx    1 root root    46 2005-10-30 11:04 asm-alpha -> ../../linux-headers-2.6.12-9/include/asm-alpha
lrwxrwxrwx    1 root root    44 2005-10-30 11:04 asm-arm -> ../../linux-headers-2.6.12-9/include/asm-arm
lrwxrwxrwx    1 root root    46 2005-10-30 11:04 asm-arm26 -> ../../linux-headers-2.6.12-9/include/asm-arm26
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 asm-cris -> ../../linux-headers-2.6.12-9/include/asm-cris
lrwxrwxrwx    1 root root    44 2005-10-30 11:04 asm-frv -> ../../linux-headers-2.6.12-9/include/asm-frv
lrwxrwxrwx    1 root root    48 2005-10-30 11:04 asm-generic -> ../../linux-headers-2.6.12-9/include/asm-generic
lrwxrwxrwx    1 root root    46 2005-10-30 11:04 asm-h8300 -> ../../linux-headers-2.6.12-9/include/asm-h8300
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 asm-i386 -> ../../linux-headers-2.6.12-9/include/asm-i386
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 asm-ia64 -> ../../linux-headers-2.6.12-9/include/asm-ia64
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 asm-m32r -> ../../linux-headers-2.6.12-9/include/asm-m32r
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 asm-m68k -> ../../linux-headers-2.6.12-9/include/asm-m68k
lrwxrwxrwx    1 root root    50 2005-10-30 11:04 asm-m68knommu -> ../../linux-headers-2.6.12-9/include/asm-m68knommu
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 asm-mips -> ../../linux-headers-2.6.12-9/include/asm-mips
lrwxrwxrwx    1 root root    47 2005-10-30 11:04 asm-parisc -> ../../linux-headers-2.6.12-9/include/asm-parisc
lrwxrwxrwx    1 root root    44 2005-10-30 11:04 asm-ppc -> ../../linux-headers-2.6.12-9/include/asm-ppc
lrwxrwxrwx    1 root root    46 2005-10-30 11:04 asm-ppc64 -> ../../linux-headers-2.6.12-9/include/asm-ppc64
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 asm-s390 -> ../../linux-headers-2.6.12-9/include/asm-s390
lrwxrwxrwx    1 root root    43 2005-10-30 11:04 asm-sh -> ../../linux-headers-2.6.12-9/include/asm-sh
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 asm-sh64 -> ../../linux-headers-2.6.12-9/include/asm-sh64
lrwxrwxrwx    1 root root    46 2005-10-30 11:04 asm-sparc -> ../../linux-headers-2.6.12-9/include/asm-sparc
lrwxrwxrwx    1 root root    48 2005-10-30 11:04 asm-sparc64 -> ../../linux-headers-2.6.12-9/include/asm-sparc64
lrwxrwxrwx    1 root root    43 2005-10-30 11:04 asm-um -> ../../linux-headers-2.6.12-9/include/asm-um
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 asm-v850 -> ../../linux-headers-2.6.12-9/include/asm-v850
lrwxrwxrwx    1 root root    47 2005-10-30 11:04 asm-x86_64 -> ../../linux-headers-2.6.12-9/include/asm-x86_64
lrwxrwxrwx    1 root root    44 2005-10-30 11:04 cluster -> ../../linux-headers-2.6.12-9/include/cluster
drwxr-xr-x  490 root root 12288 2005-10-30 11:04 config
drwxr-xr-x    2 root root 16384 2005-10-30 11:04 linux
lrwxrwxrwx    1 root root    45 2005-10-30 11:04 math-emu -> ../../linux-headers-2.6.12-9/include/math-emu
lrwxrwxrwx    1 root root    42 2005-10-30 11:04 media -> ../../linux-headers-2.6.12-9/include/media
lrwxrwxrwx    1 root root    40 2005-10-30 11:04 mtd -> ../../linux-headers-2.6.12-9/include/mtd
lrwxrwxrwx    1 root root    40 2005-10-30 11:04 net -> ../../linux-headers-2.6.12-9/include/net
lrwxrwxrwx    1 root root    43 2005-10-30 11:04 pcmcia -> ../../linux-headers-2.6.12-9/include/pcmcia
lrwxrwxrwx    1 root root    43 2005-10-30 11:04 prism2 -> ../../linux-headers-2.6.12-9/include/prism2
lrwxrwxrwx    1 root root    42 2005-10-30 11:04 rxrpc -> ../../linux-headers-2.6.12-9/include/rxrpc
lrwxrwxrwx    1 root root    41 2005-10-30 11:04 scsi -> ../../linux-headers-2.6.12-9/include/scsi
lrwxrwxrwx    1 root root    42 2005-10-30 11:04 sound -> ../../linux-headers-2.6.12-9/include/sound
lrwxrwxrwx    1 root root    42 2005-10-30 11:04 video -> ../../linux-headers-2.6.12-9/include/video
lrwxrwxrwx    1 root root    41 2005-10-30 11:04 wlan -> ../../linux-headers-2.6.12-9/include/wlan

```

very strange... links back to themselves...

---

### Post by jaa1180 on 2005-11-12
Fixed it..
Uninstalled the kernal image and reinstalled it... then it wanted to install another peice... BAM! 
It would work then.

---

