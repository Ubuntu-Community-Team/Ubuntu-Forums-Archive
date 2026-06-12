---
title: "Error when doing and update in synaptic"
date: 2008-03-10
forum: General Help
---

### Post by Raul LH on 2008-03-10
I've been trying to install the updates in downloaded by synaptic and I get this error message, could any one tell me what is it about, what I could guess is that it has something to do with the kernel
The message is:
E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb: lectura insuficiente en buffer_copy (error en dpkg-deb durante `./lib/modules/2.6.22-14-generic/kernel/fs/xfs/xfs.ko')

---

### Post by Oldsoldier2003 on 2008-03-10
> **Raul LH said:**
> I've been trying to install the updates in downloaded by synaptic and I get this error message, could any one tell me what is it about, what I could guess is that it has something to do with the kernel
The message is:
E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb: lectura insuficiente en buffer_copy (error en dpkg-deb durante `./lib/modules/2.6.22-14-generic/kernel/fs/xfs/xfs.ko')

that looks like the boot partition full message in spanish... if thats the case you need to gain some space in the root partition. some things that might help are

sudo apt-get clean
rebooting to clear your /tmp directories
uninstalling old kernels, keep at least the one prior to what you are using now
removing any unused or unnecessary software

---

