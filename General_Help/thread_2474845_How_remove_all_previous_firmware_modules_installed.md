---
title: "How remove all previous firmware modules installed in system ?"
date: 2022-05-09
forum: General Help
---

### Post by aug7744 on 2022-05-09
Hello.
Installed Lubuntu 20.04.3 kernel 5.11.
After installed kernel update 5.17.

I see
/usr/lib/modules/5.11.0-27-generic/
/usr/lib/modules/5.17.5-051705-generic/

Is secure remove all modules in /usr/lib/modules/5.11.0-27-generic/ ?

and in when computer is power on in OS menu have option to choice start using kernel 5.11 or the default 5.17.
I not want start using kernel 5.11.

How remove all files related with the previous kernel 5.11 ?
I see several commands to remove previous kernel files, but not remove all kernel 5.11 files.

In /boot is secure remove all files *.old ?
initrd.img.old
vmlinuz.old
initrd.img-5.17.5-051705-generic.old-dkms
I not want to return to previous kernel files or configuration done by dkms.

Thanks for read.

---

### Post by Bashing-om on 2022-05-09
aug7744 - Hello

Depending on IF linux-generic is also installed -
try:
```

sudo apt --purge autoremove

```

the command:
```

dpkg -l | grep linux-

```
to see if we the removal of the Generally available kernel components are required ( linux-generic).

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by aug7744 on 2022-05-09
@[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508")
Thanks for your reply.
Running the commands above not remove the modules and show not files to be removed.

[**[COLOR=#DD4814][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508")

---

### Post by Bashing-om on 2022-05-09
aug7744; Ho-kay

No step for a stepper :D

post back - between code tags - the return from terminal command:
```

dpkg -l | grep linux-

```

so we see what it is that we are going to do.

[INDENT][INDENT]it is in the process
[/INDENT][/INDENT]

---

### Post by aug7744 on 2022-05-09
ii  binutils-x86-64-linux-gnu                     2.34-6ubuntu1.3                                    amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                    4.5ubuntu3.7                                       all          Linux image base package
ii  linux-firmware                                1.187.30                                           all          Firmware for Linux kernel drivers
ii  linux-generic-5.17                            5.17.5                                             amd64        Meta-package which will always depend on the latest packages in a mainline series.
ii  linux-generic-hwe-20.04                       5.11.0.27.29~20.04.11                              amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.11.0-27-generic               5.11.0-27.29~20.04.1                               amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.17.5-051705                   5.17.5-051705.202204280727                         all          Header files related to Linux kernel version 5.17.5
ii  linux-headers-5.17.5-051705-generic           5.17.5-051705.202204280727                         amd64        Linux kernel headers for version 5.17.5 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04               5.11.0.27.29~20.04.11                              amd64        Generic Linux kernel headers
ii  linux-hwe-5.11-headers-5.11.0-27              5.11.0-27.29~20.04.1                               all          Header files related to Linux kernel version 5.11.0
ii  linux-image-5.11.0-27-generic                 5.11.0-27.29~20.04.1                               amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04                 5.11.0.27.29~20.04.11                              amd64        Generic Linux kernel image
ii  linux-image-unsigned-5.17.5-051705-generic    5.17.5-051705.202204280727                         amd64        Linux kernel image for version 5.17.5 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                          5.4.0-109.123                                      amd64        Linux Kernel Headers for development
ii  linux-modules-5.11.0-27-generic               5.11.0-27.29~20.04.1                               amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.17.5-051705-generic           5.17.5-051705.202204280727                         amd64        Linux kernel extra modules for version 5.17.5 on 64 bit x86 SMP
ii  linux-modules-extra-5.11.0-27-generic         5.11.0-27.29~20.04.1                               amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                               all          base package for ALSA and OSS sound systems

---

### Post by Bashing-om on 2022-05-09
aug7744; Hey hey -

You only have the 2 kernels installed - the system expects to keep at least 2 kernels. One for a backup just in the event of a problem booting.

I strongly advise that you follow this principle. Once a later  kernel becomes available and is installed - I do expect that the system will automagically purge the old 5.11.0-27 kernel.

see the result:
```

ls -al /boot/

```
where "vmlinuz.old" points to the 5.11 kernel.

How about we follow this path of least resistance ?

[INDENT][INDENT]Let us not try and fool mother Linux
[/INDENT][/INDENT]

---

### Post by aug7744 on 2022-05-11
That avoid problems for users.
Your reply does good sense.

Hey the files in /usr/lib/modules/5.11.0-27-generic/ are written in / or are in /boot files related with kernel 5.11 ?

---

### Post by Bashing-om on 2022-05-11
aug7744; Uh Huh

> 
files related with kernel 5.11 


The components of the kernel build are in:
/usr/src/
/lib/modules/
/boot/

[INDENT]as we step up on the learning curve
[/INDENT]

---

### Post by aug7744 on 2022-05-11
If deleting files related with kernel 5.11 in /usr/src/ and /lib/modules/ break OS boot start if selecting to start using kernel 5.11 ?

---

### Post by Bashing-om on 2022-05-11
aug7744; Ouch !

No - do not do that :(
> 
boot start if selecting to start using kernel 5.11

As the 7.11 kernel is built removing the modules will not effect booting - *HOWEVER* removing any of the modules will prevent any added modules ( read that as a driver) from building.

[INDENT]no, don't do that
[/INDENT]

---

