---
title: "Concerning custom-built kernel size"
date: 2008-05-09
forum: General Help
---

### Post by Trail on 2008-05-09
```

trail@trail-kubuntu:/boot$ ls -lh
-rw-r--r-- 1 root root  74K 2008-02-12 12:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root  88K 2008-05-09 21:05 config-2.6.25-custom

-rw-r--r-- 1 root root 6.9M 2008-05-04 14:16 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root  40M 2008-05-09 22:36 initrd.img-2.6.25-custom

-rw-r--r-- 1 root root 1.7M 2008-02-12 12:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1.7M 2008-05-09 22:16 vmlinuz-2.6.25-custom

trail@trail-kubuntu:/usr/src$ ls -lh
-rw-r--r--  1 root  src   8.6M 2008-05-09 22:31 linux-headers-2.6.25-custom.deb
-rw-r--r--  1 root  src   182M 2008-05-09 22:24 linux-image-2.6.25-custom.deb

trail@trail-kubuntu:/usr/src$ ls -lh /var/cache/apt/archives/linux-*
-rw-r--r-- 1 root root 7.5M 2008-02-12 18:06 /var/cache/apt/archives/linux-headers-2.6.22-14_2.6.22-14.52_all.deb
-rw-r--r-- 1 root root  18M 2008-02-12 18:06 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb

```

I've built a few kernels using some tutorials (using make-kpkg) and I was wondering why I get such large versions of the images. I've been using the configuration of the default ubuntu .config file.

Do ubuntu maintainers further process their images or is there something done specifically to keep a low size? (Maybe the binaries need stripping of symbols afterwards or such? But 181Mb->40Mb seems to me a bit much for just symbols).

I've been using tutorials similar to this ([http://howtoforge.com/kernel_compilation_ubuntu_p2](http://howtoforge.com/kernel_compilation_ubuntu_p2)). I am compiling specifically for k8 though I don't think it has a great impact on filesize (and will go on heavier modifications later).

Any ideas/pointers?

---

