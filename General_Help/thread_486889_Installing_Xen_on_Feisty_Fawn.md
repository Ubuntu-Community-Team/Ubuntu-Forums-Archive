---
title: "Installing Xen on Feisty Fawn"
date: 2007-06-28
forum: General Help
---

### Post by Frankenbean on 2007-06-28
Hello all,
  I've been struggling with installing Xen on my machine running Feisty Fawn.  I've read several "how to" articles, but all of them seem to reference packages that don't exist in my repository. 

here's what I've done so far.

Enabled universe in my /etc/apt/sources.list
Downloaded and installed the xen0-linux-2.6.16-11.2-generic package
Downloaded and installed xen-tools-3.0 and xen-utils-common
ran sudo mkinitramfs -o initrd.img-xen0-2.6.16-11.2-generic to create an initrd image

So now in /boot I have the xen0-linux-2.6.16-11.2-generic kernel and the initrd.img referenced above.

I cannot for the life of me figure out how to boot to this kernel.

When I try to start xend right now, I get " Could not obtain handle on privileged command interface" which indicates to me that I'm not booting to the Xen kernel.  Can anyone help?

---

### Post by Doc_symbiosis on 2007-06-28
Perhaps give it a try and just install ubuntu-xen-desktop. Worked for me

---

