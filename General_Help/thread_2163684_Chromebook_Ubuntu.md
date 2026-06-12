---
title: "Chromebook Ubuntu"
date: 2013-07-19
forum: General Help
---

### Post by destroy116 on 2013-07-19
Hey guys, I'm planning to setup ubuntu to my samsung chromebook and I want to know that does the developing tools like java or c ++ work on chrubuntu and the other question is how much space does chrubuntu take and is it working stable and fast as chrome os ? Hope you'll answer it...:KS

---

### Post by TheFu on 2013-07-19
So, I looked at the specifications for that machine. "Samsung Exynos 5 Dual Processor" is not x86 compatible, it is ARM.  That means it will be slower than old C2D processors and you will not want to run compiles on it.  OTOH, it would be a good remote desktop device into a normal, cheap desktop.

I have no idea how much space chrubuntu takes, but a desktop install for normal x86 Ubuntu is 5-8GB.  I've been running an LXDE desktop since 2010 in 14G of disk storage - I put large media files on the network, not local.

C++ development isn't as hungry for storage as Java is.  Java development for Android needs about 20G of disk, just to get started.  Sure, these will work, provided you want to compile for ARM environments.  Some binary tools will not work on ARM at all, just be aware that you've changed from x86 to ARM processors. When you are new, doing this means you'll need to learn how to cross compile C/C++ code for other platforms.  I've used cross-compilers extensively, just never C/C++.  It also makes debugging harder when you don't have the platform to test on that 99.9999% of your users have.

So, looking over the spec again - it has 16G local storage. I don't see anyone doing Java development in that limited storage.  I think you could do python, ruby, perl (pick 1) in that space, however.

Also, there wasn't any mention of RAM.  Java development tools run slow on my 6G-RAM Core i5 laptop.  I think 8-16G of RAM is what most java devs have.  For C/C++, 2G is probably fine.  Java development seems to be a hog, IME.

Summary:
Chrombook for remote access, email, lite surfing - Fabulous!  
Chrombook for development machine - not so good.

---

### Post by destroy116 on 2013-07-19
> **TheFu said:**
> So, I looked at the specifications for that machine. "Samsung Exynos 5 Dual Processor" is not x86 compatible, it is ARM.  That means it will be slower than old C2D processors and you will not want to run compiles on it.  OTOH, it would be a good remote desktop device into a normal, cheap desktop.

I have no idea how much space chrubuntu takes, but a desktop install for normal x86 Ubuntu is 5-8GB.  I've been running an LXDE desktop since 2010 in 14G of disk storage - I put large media files on the network, not local.

C++ development isn't as hungry for storage as Java is.  Java development for Android needs about 20G of disk, just to get started.  Sure, these will work, provided you want to compile for ARM environments.  Some binary tools will not work on ARM at all, just be aware that you've changed from x86 to ARM processors. When you are new, doing this means you'll need to learn how to cross compile C/C++ code for other platforms.  I've used cross-compilers extensively, just never C/C++.  It also makes debugging harder when you don't have the platform to test on that 99.9999% of your users have.

So, looking over the spec again - it has 16G local storage. I don't see anyone doing Java development in that limited storage.  I think you could do python, ruby, perl (pick 1) in that space, however.

Also, there wasn't any mention of RAM.  Java development tools run slow on my 6G-RAM Core i5 laptop.  I think 8-16G of RAM is what most java devs have.  For C/C++, 2G is probably fine.  Java development seems to be a hog, IME.

Summary:
Chrombook for remote access, email, lite surfing - Fabulous!  
Chrombook for development machine - not so good.

Thanks man this was very helpfull for me, as for now I'm using the cloud coding like codenvy, cloud9. Again thank you for your answer :)

---

