---
title: "Screen resolution on server"
date: 2007-07-29
forum: General Help
---

### Post by Peque on 2007-07-29
Hey Forum.

I have just installed a server on a Shuttle XPC which have this Graphic card: 
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter


Well my bootconf looks like this: 
title           Ubuntu, kernel 2.6.15-28-server
root            (hd0,0)
kernel          /vmlinuz-2.6.15-28-server root=/dev/hda3 ro quiet vga=791
initrd          /initrd.img-2.6.15-28-server
savedefault
boot

But each time I want to use 1024x768 resolution - It'll go into out of resoution. 
The screen is a Viewsonic 20.5"" and can go to 1600X1200 - but all I want is 1024x768. 

But I have made a much higher resolution earliere on windows on that machine. 
I do not run any kind of desktop - It's only a server, but still it should be able to go to that resolution??? 

Does anybody have an vlue about that??? 
Thanks

P

---

