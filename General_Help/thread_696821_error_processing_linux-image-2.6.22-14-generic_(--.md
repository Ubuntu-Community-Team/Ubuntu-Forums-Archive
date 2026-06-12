---
title: "error processing linux-image-2.6.22-14-generic (--configure):"
date: 2008-02-14
forum: General Help
---

### Post by samuraiche on 2008-02-14
Hi!

When am trying to install something via Synaptic or apt-get I always get this message:

Setting up linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Failed to symbolic-link boot/initrd.img-2.6.22-14-generic to initrd.img.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-2.6.22-14-generic

I've tried to remove corresponding file from /var/cache/apt/archives 
and after that running "apt-get install -f" and "sudo dpkg --configure -a"

but still getting this annoying message

I do get the app's I wanted installed but this message really bothers me 

Any help would be appreciated :)
thnx

---

### Post by sercz on 2008-02-15
Hi,

I had exactly the same problem. It turned out, that the /initrd.img link pointed do an image of a kernel which I had installed manually by compiling from source. I had already deleted this kernel and the corresponding initrd image, but forgot to delete the links.

So a

```

sudo rm /initrd.img /vmlinuz
sudo dpkg --configure -a

```

solved the problem.

---

