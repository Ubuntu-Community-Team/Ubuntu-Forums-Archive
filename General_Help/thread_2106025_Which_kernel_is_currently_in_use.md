---
title: "Which kernel is currently in use?"
date: 2013-01-17
forum: General Help
---

### Post by kleenex on 2013-01-17
Hi. I'm a little confused. Today was available 3.2 kernel update for *buntu 12.04. According to the [COLOR=Green]dpkg[/COLOR] command, there is about 4 [COLOR=Green]linux-image[/COLOR] packages. That's good. My computer is 32 bit (i686) and without [COLOR=Green]pae[/COLOR] kernel. Let see:
```
[COLOR=Red]$[/COLOR] [COLOR=Green]dpkg -l |grep linux-image[/COLOR]
ii  linux-image-3.2.0-34-generic    3.2.0-34.53      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic    3.2.0-35.55      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-generic    3.2.0-36.57      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic             3.2.0.36.43      Generic Linux kernel image

[COLOR=Red]$[/COLOR] [COLOR=Green]uname -mrs[/COLOR]
Linux 3.2.0-36-generic i686
```As you can see I'm running [COLOR=SeaGreen][COLOR=Green]3.2.0-36-generic[/COLOR] [/COLOR]kernel (updated today). I'm wondering about[COLOR=SeaGreen][COLOR=Green] linux-image-generic 3.2.0.36.43[/COLOR][COLOR=Black],[/COLOR] [COLOR=Black]which is a [/COLOR][/COLOR]generic Linux kernel image. According to the output of the [COLOR=Green]uname[/COLOR] command and a result of [COLOR=Green]dpkg[/COLOR] I would like to ask, which kernel I'm using? I'm confused because of  Linux kernel image and it's version; [COLOR=Green][COLOR=Black]3.2.0.36.[/COLOR]43[/COLOR]. Especially the [COLOR=Green].43[/COLOR] number. Why such a number/version?

So, which kernel is currently in use? I hope it is a [COLOR=Green]linux-image-3.2.0-36-generic[/COLOR]    (3.2.0-36.57).
 
Thanks.

---

### Post by ibjsb4 on 2013-01-17
The running kernel

```
cat /proc/version_signature
```

---

### Post by steeldriver on 2013-01-17
Package [FONT=Courier New]linux-image-generic[/FONT] is just a metapackage I think - you should see that it depends on the actual latest kernel image e.g. for me

```
$ apt-cache depends linux-image-generic
linux-image-generic
  Depends: linux-image-3.2.0-35-generic
  Depends: linux-firmware

```For you it should depend on 3.2.0-36-generic

---

### Post by kleenex on 2013-01-19
Hi **ibjsb4** and **steeldriver**. According to yours answers it seems that I'm using a correct kernel. Let see:
```
[COLOR=Red]$[/COLOR] [COLOR=Green]cat /proc/version_signature[/COLOR]
Ubuntu 3.2.0-36.57-generic 3.2.35[COLOR=Red]
$[/COLOR] [COLOR=Green]apt-cache depends linux-image-generic[/COLOR]
linux-image-generic
Depends: linux-image-3.2.0-36-generic
Depends: linux-firmware
```I wonder why in the first command according to [COLOR=Green]version_signature[/COLOR], there is 3.2.35 version? (next to the correct 3.2.0-36.57-generic version of the kernel). 

So gentlemen, everything is okay? ;)

---

### Post by 3Miro on 2013-01-19
The first number in the kernel changes once a decade, kernel 2.6 is still in use, but most distros have switched to 3.

The second number is the major steps within version 3 that have new features and drivers.

The third number is an after release patch number. For example, once 3.2.0 has been released, developers work on new drivers and features for 3.3.0, but if a bug or security issue is discovered in 3.2.0, they will go back and fix it and release 3.2.1

Just like all major distributions, Ubuntu makes its own kernel changes and hence the last number indicating those.

dpkg will list all of the installed kernels (or you can see them installed in /boot/, you can do "ls -al /boot/)

"uname -a" will tell you which kernel is currently in use.

---

### Post by kleenex on 2013-01-20
Hi, now everything is clear. Cheers!

---

