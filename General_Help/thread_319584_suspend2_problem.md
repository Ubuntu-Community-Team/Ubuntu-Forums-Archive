---
title: "suspend2 problem"
date: 2006-12-15
forum: General Help
---

### Post by hovnatan on 2006-12-15
Hi

I have compiled a new kernel(2.6.19.1) with suspend2. dmesg gives that everything looks ok,

hovo@hovo-laptop:~$ dmesg | grep Suspend2
Suspend2 Core.
Suspend2 Userspace UI Support module loaded.
Suspend2 Checksumming module loaded.
Suspend2 Userspace Storage Manager module loaded.
Suspend2 Compressor module loaded.
Suspend2 Encryptor module loaded.
Suspend2 Block I/O module loaded.
Suspend2 Swap Allocator module loaded.
Suspend2 File Allocator module loaded.


but when trying to run  sudo hibernate -F /etc/hibernate/suspend2-ram.conf it gives some errors
Your kernel does not appear to have Software Suspend 2 support compiled in.
Please follow the HOWTO linked from [http://www.suspend2.net/](http://www.suspend2.net/) for instructions
on how to compile Software Suspend into your kernel.
hibernate: Aborting.


Do you know how to fix this?

Thanks 
Hovo

---

