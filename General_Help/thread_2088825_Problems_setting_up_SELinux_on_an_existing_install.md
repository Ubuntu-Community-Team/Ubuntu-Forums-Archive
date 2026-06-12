---
title: "Problems setting up SELinux on an existing install"
date: 2012-11-27
forum: General Help
---

### Post by Kellman on 2012-11-27
I'm trying to set up SELinux but have been hitting roadblocks repeatedly.  I finally found and followed these instructions since they have specific Ubuntu notes: [http://wiki.debian.org/SELinux/Setup](http://wiki.debian.org/SELinux/Setup)

It's still not working, but after playing with the custom initrd script  they give, I think I'm tracking it down.  I still get this error during  the init:

load_policy:  Can't load policy:  No such device

It  does this when I try to run it at the command line as well.  Attempting  to mount /selinux also still gives 'mount: unknown filesystem type  'selinuxfs''.  I'm using the stock kernel, but it's almost like it's  missing a kernel module or something.

Ideas anyone?  This is on Lucid running as Xen guest, btw.

---

