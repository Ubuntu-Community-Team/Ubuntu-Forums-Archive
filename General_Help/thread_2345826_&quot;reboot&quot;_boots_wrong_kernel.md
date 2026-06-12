---
title: "&quot;reboot&quot; boots wrong kernel?"
date: 2016-12-08
forum: General Help
---

### Post by David_Partridge on 2016-12-08
> Some weeks ago I installed the following upstream kernel:

linux-headers-4.8.7-040807_4.8.7-040807.201611101131_all.deb
linux-headers-4.8.7-040807-generic_4.8.7-040807.201611101131_amd64.deb
linux-image-4.8.7-040807-generic_4.8.7-040807.201611101131_amd64.deb

to my LTS 16.04 system.

Today I connected to the system after reboot and it cheerily informed me the system was running Linux 4.4.0-53-generic!

When I shutdown and powered off and cold booted, the kernel that booted was the 4.8.7 kernel.

However when I issue a reboot command it boots to 4.4.0-53!!!!!!!

How do I get things set so reboot will also boot the 4.8.7 kernel, and how to prevent this recurring?


I did some digging and found:

```
amonra@Charon:~$ ll /vmlinuz
lrwxrwxrwx 1 root root 1K Dec  6 00:14 /vmlinuz -> boot/vmlinuz-4.4.0-53-generic
amonra@Charon:~$ ll /initrd.img
lrwxrwxrwx 1 root root 1K Dec  6 00:14 /initrd.img -> boot/initrd.img-4.4.0-53-generic
```

so I did:

```
root@Charon:/# rm /vmlinuz
root@Charon:/# ln -s /boot/vmlinuz-4.8.7-040807-generic /vmlinuz
root@Charon:/# rm /initrd.img
root@Charon:/# ln -s /boot/initrd.img-4.8.7-040807-generic /initrd.img
root@Charon:/#
```

which appears to have solved the immediate problem of rebooting to the upstream kernel.

However I don't understand how to prevent this happening again, so some help would be appreciated.

Thanks
Dave

---

### Post by Keith_Helms on 2016-12-08
My guess would be that the ubuntu kernel updates change the softlinks while the deb files that you downloaded from somewhere else don't.  You'll probably have to make the same manual changes each time the ubuntu updates install a new kernel version.

---

### Post by David_Partridge on 2016-12-22
Any suggestion on how to prevent this happening gratfully received, as I just got another 4.4 kernel update which overrode the 4.8 kernel.

Thanks
Dave

---

