---
title: "AutoKernel broke my machine"
date: 2006-10-30
forum: General Help
---

### Post by Slace on 2006-10-30
I decided to give AutoKernel a crack, as I'm interested in learning kernel hacking but I need some help getting started ;)

I followed the install and setup instructions here: [http://www.ubuntuforums.org/showthread.php?t=222018](http://www.ubuntuforums.org/showthread.php?t=222018)

After it had all compiled and such I rebooted to try my shinny new kernel.
Well that didn't go so well...

When it tries to boot I get this:
```
intel_rng: cannont enable RNG, aborting
intel_rng: RNG registering failed(-5)
Target filesystem doesn't have /sbin/init
```

well the 1st 2 I don't think are of great concern as I may have just chosen a bad flag. What I'm troubled by is the lack of /sbin/init.
I'm then dumbed in a BusyBox shell with this error:
```
/bin/sh: can't access tty; job control turned off
(initramfs)[code]
And **(initramfs)** is my command prompt.

Ok, so now I'm getting a bit more worried.
I pull the plug and try a known working kernel and I get this upon booting it:
[code]Starting up ...
Target fulesystem doesn't have /sbin/init
```
And that lovely BusyBox again...

About now I figured I'm in a bit of trouble!

I've tried my single user mode kernels, but unsurprisingly they didn't work either.

This is my grub boot options:
```
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-386 root/dev/hda1 ro quiet
initrd /boot/initrd.img-2.6.17-10-386
quet
savedefault
boot
```

So does anyone know how I can rescue my machine?

---

### Post by xtacocorex on 2006-11-18
Well Autokernel is very alpha software and most of the people who have used it were testing for me.

Do the old kernels work when you try to boot them? I was a little confused by the problem. I am also still new to kernel compiling, so I can debug stuff with Autokernel, but when a kernel doesn't work properly, it's probably something set in it's configuration during compile.  Once Autokernel gets updated to autoconfigure the kernel, problems like that shouldn't happen.  The only problem is I haven't figured out how to do that.

---

