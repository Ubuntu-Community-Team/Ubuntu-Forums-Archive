---
title: "Missing header files"
date: 2007-04-18
forum: General Help
---

### Post by peloquin on 2007-04-18
Hi,

I'm very new to Ubuntu (using Edgy) and I'm having trouble figuring out, what I hope is a very basic problem. I'm trying to compile a program I wrote, and it appears I'm missing some header files I thought were fairly standard, like /usr/include/asm/processor.h, /usr/include/asm/system.h, etc. It seems the /usr/include/asm folders are very sparsely populated. I've installed kernel-build and linux-header packages, but this has not led to any more files being placed in /usr/include/asm. My program includes <asm/atomic.h> which itself include other files that are missing. I don't know how to figure out what other packages I need to get the missing header files installed. Can anyone educate a newbie?

Thanks

---

### Post by tkjacobsen on 2007-04-18
Have you installed the build-essential package? It contains some compilers and c and c++ standard libraries, maybe the ones you look for are included as well.

---

### Post by beerorkid on 2007-04-18
Build-essential for sure
also you might have to download and install the headers.  it is purdy simple.  

two ways to do it

1.
open a terminal and enter
```
uname -r
```
it will spit out something like this:
2.6.20-15-generic

then enter this
```
sudo apt-cache search whateveruname-rspitout
```
you will get some output like this:
linux-backports-modules-2.6.20-15-generic - Backported modules package
[COLOR="Red"]linux-headers-2.6.20-15-generic[/COLOR] - Linux kernel headers for version 2.6.20 on x86/x86_64
linux-image-2.6.20-15-generic - Linux kernel image for version 2.6.20 on x86/x86_64
linux-image-debug-2.6.20-15-generic - Linux kernel debug image for version 2.6.20 on x86/x86_64
linux-restricted-modules-2.6.20-15-generic - Non-free Linux 2.6.20 modules on x86/x86_64

I highlited the header in red.  So in my case I would enter this:
```
sudo apt-get install linux-headers-2.6.20-15-generic
```

2. you could find them through synaptic as well.  Would help to search with the output of uname -r

---

### Post by peloquin on 2007-04-19
Appreciate the replies. :) 

Yes, I had already installed both the build-essentials and linux-headers-'uname -r' packages. Other packages I might investigate?

---

### Post by raul_ on 2007-04-19
libc6-dev or lib6c-dev...i'm not sure where the '6' is

---

