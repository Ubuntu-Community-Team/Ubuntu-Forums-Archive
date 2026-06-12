---
title: "Trying to follow Boot to RAM guide"
date: 2014-12-07
forum: General Help
---

### Post by buntuluxx on 2014-12-07
I am attempting to create a custom Ubuntu Live CD with UCK and have it boot to RAM entirely.

This guide provides instructions on how to enable the boot to RAM option.
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

I let UCK do the squash stuff, extract the iso and create the directories

It created /home/ubuntu/tmp/remaster-root (with all following direcories)
              /home/ubuntu/tmp/remaster-iso (with /casper , /boot etc.)

I am using the UCK console option to enter commands.

I was able to edit the boot script at /usr/share/initramfs-tools/scripts/casper

However now I am stuck at this stage of the guide:
**Regenerate initrd.gz** (in my case it is called initrd.lz which is located at  /home/ubuntu/tmp/remaster-iso/casper/initrd.lz

 Since we edited bootup scripts, we need to regenerate the file we know as /casper/initrd.gz to incorporate these changes: 
```
sudo cp -L /etc/resolv.conf /casper/chroot/etc/
sudo mount -t proc none /casper/chroot/proc
sudo mount -o bind /dev /casper/chroot/dev
sudo chroot /casper/chroot /bin/bash
```

The /casper/chroot/etc/ directory shown in the guide should be the equivalent to my /home/ubuntu/tmp/reamster-root/etc , which was created by UCK.
But it won't work and return the following:

```
root@ubuntu:/# sudo cp -L /etc/resolv.conf /home/ubuntu/tmp/remaster-root/etc/
sudo: unable to resolve host ubuntu
cp: target '/home/ubuntu/tmp/remaster-root/etc/' is not a directory

```

I also tried to start with /remaster-root, but it failed as well.

```
root@ubuntu:/# sudo cp -L /etc/resolv.conf /remaster-root/etc/
sudo: unable to resolve host ubuntu
cp: target '/home/ubuntu/tmp/remaster-root/etc/' is not a directory

```


Can somebody help me out?

---

