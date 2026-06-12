---
title: "[SOLVED] Nvidia drivers saying I have xen installed but I can't find it"
date: 2008-05-14
forum: General Help
---

### Post by kuyote on 2008-05-14
Here's the story up to this point.

Hardware is:
Asus U6s
4GB ram
Nvidia 8400 video

So I just installed 8.04 desktop on my asus laptop, I had the nvidia drivers working everything was great. Then I noticed only 3GB of memory were usable. I found a work around to my problen here 

[http://www.softwarevoices.com/archives/53-Only-seeing-3GB-of-RAM-on-Ubuntu-7.04-Feisty-when-4GB-are-installed-SOLUTION.html]("http://www.softwarevoices.com/archives/53-Only-seeing-3GB-of-RAM-on-Ubuntu-7.04-Feisty-when-4GB-are-installed-SOLUTION.html")

So I install linux-server and linux-headers-server, and 4GB are now usable, except my nvidia drivers no longer work. I then try to use the provided work around, but when installing the nvidia drivers, it tell's me I'm using a xen kernel. I can't find what I'm using that has xen, unless the server kernel has it precompiled. If so is there any way to turn it off? Or any work around for this?

Thanks

---

### Post by cdenley on 2008-05-14
No need to compile it yourself. You just need to install the restricted kernel modules for the server kernel.
```

sudo apt-get install linux-restricted-modules-2.6.24-16-server

```
I'm not sure if running a server kernel will have a negative effect on performance of desktop functions. Are you running 64-bit or 32-bit ubuntu?
```

uname -m

```

---

### Post by kuyote on 2008-05-14
I'm running the i686 version. The only reason for running the server kernel was to be able to use all the ram, I used apt to grab it so I didn't have to compile

```
apt-get install linux-server linux-headers-server
```


I didn't really check for another work around which I should have, I can uninstall the server, and try to enable HIGHMEM in the generic

---

### Post by kuyote on 2008-05-15
Well I'm not sure what exactly fixed it, but after purging all kernels, and sources, and reinstalling the server kernel, and linux-restricted, the nvidia drivers started working. Must have been something left over from the generic kernel conflicting with the server.

---

### Post by lordViN on 2008-06-16
hello kuyote,

what exactly you did to resolve the issue??   I,m having the same problem with a clean install of ubuntu server 8.04 i386. When installing the nvidia driver it tells me that I'm using a xen kernel and the installation fails.

---

### Post by chrroessner on 2008-06-16
Same problem here

4GB RAM, therefor linux-image-server

I would like to run the newest nvidia driver for my 9800GTX card to have full features.

The installer tells me that the kernel is build with Xen support. And it is saying right.

So what can I do?

Kind regards
Christian

---

