---
title: "Kernel Installation Question"
date: 2008-05-29
forum: General Help
---

### Post by Brando569 on 2008-05-29
When I go to install the new kernel I just compiled it says this:

```
Setting up linux-image-2.6.25 (2.6.25-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
find: /lib/firmware/2.6.25: No such file or directory
find: /lib/firmware/2.6.25: No such file or directory
find: /lib/firmware/2.6.25: No such file or directory
find: /lib/firmware/2.6.25: No such file or directory
find: /lib/firmware/2.6.25: No such file or directory
find: /lib/firmware/2.6.25: No such file or directory
```

but the installation doesnt break, the first two times i tried to run the kernel it worked but I didnt have any sound. I just tried it once again lastnight and (after a recompile) it seemed like it wouldnt load the initrd. It would just say "loading linux please wait". It seems that Ive had more problems with this new 2.6.25 kernel then Ive had with any other.

---

