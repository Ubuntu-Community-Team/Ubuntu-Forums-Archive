---
title: "Live booting from a squashfs image packed into initrd.lz"
date: 2013-08-07
forum: General Help
---

### Post by marqmike2 on 2013-08-07
Hey folks,

This may seem like an awfully odd requirement, but I'm interested in netbooting a stripped down live precise install without needing to serve up an image over nfs.  I followed this guide [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch) in order to create a live cd that I can netboot and it works great if I pxe boot with the initrd.lz and vmlinuz passing parameters to do a netboot over nfs, but I was wondering if it would be possible to do this without needing nfs by just throwing the filesystem.squashfs image into the initrd.lz and modifying the init script to mount this instead.

So, I tried blowing up the initrd.lz file, adding the squashfs image, and packing it back up and booting with that.  Without any kernel parameters it threw me into an ash shell in the initramfs stage.  I thought I might be able to just mount the squashfs image onto /root with "mount -o loop -t squashfs filesystem.squashfs /root" and then just run the init script, but it really didn't like that (it just displayed the ubuntu startup animation forever and likely kernel panic'd in the background).  I figured this was because the filesystem wasn't writable, so I tried mounting a tempfs at /root that was big enough to hold the filesystem, mount the squashfs image and then copy the contents over to /root, but it didn't seem to like this either when I ran the init script (again, startup animation forever).

At this point I figure there's something that I'm not quite doing correctly with the way the init script is calling do-init, but I'm at a loss as to where to look.  If anyone has managed to do this successfully I'd love to know how you did it.  Otherwise, I'm mainly looking for information on how I can get some more info on how exactly do-init works and how I might be able to accomplish this.

Thanks!

---

