---
title: "Installing new kernel after using Alternative Installer CD"
date: 2008-05-23
forum: General Help
---

### Post by nick cellular on 2008-05-23
Hello Ubuntu Community,

I've installed Ubuntu 8.04 via the Alternative Installer CD and chose the Guided install using an encrypted LVM. I then compiled a custom kernel and installed it. After a reboot and GRUB finishes I get a blinking cursor. If I attempt to boot off the old kernel I get an authentication error.

Heres what I did to get where I am.

I ran apt-get to install everything needed to build a new kernel. 
```
 apt-get install kernel-package libncurses5-dev fakeroot wget bzip2 linux-source

```

I decompressed the linux source that was in /usr/src and copied in my .config from /boot. 

I ran make menuconfig and setup my kernel options. Then built my kernel using.

```

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

```

And finally installed it using dpkg -i

Has anyone built a custom kernel after setting up an encrypted LVM? Any help is appreciated.

Thank you

---

### Post by nick cellular on 2008-05-24
Well I started over from scratch and this time it worked fine. Guess I must have messed up somewhere the first time.

---

