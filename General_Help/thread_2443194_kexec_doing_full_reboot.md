---
title: "kexec doing full reboot"
date: 2020-05-12
forum: General Help
---

### Post by steven43 on 2020-05-12
On Ubuntu 16.04 - I could reboot into a new using kexec and bypass the BIOS and grub menus.

Doing something like:

[FONT=courier new]kexec -u
kexec -l /boot/vmlinuz-5.4.0-29-generic --initrd=/boot/initrd.img-5.4.0-29-generic --reuse-cmdline
reboot[/FONT]

Would unload any previously loaded kexec target (which probably didn't exist) and then load a new kexec target.  Replacing vmlinuz with the correct path to the correct path to the new kernel and replacing the initrd image with the correct initrd image for that kernel.

The reboot command would do a proper shutdown.  The shutdown sequence would follow:

[FONT=courier new][  OK  ] Reached target Shutdown.
[70109.380628] kexec: Starting new kernel[/FONT]

And immediately load the new kernel.

Now with Ubuntu 20.04 it seems that when it gets to [FONT=courier new][  OK  ] Reached target Shutdown.[/FONT] - the system is doing a full reboot, to the BIOS, through grub.  Any clues as to why that may be happening?

[FONT=courier new][/FONT]This is a new physical machine different from the Ubuntu 16.04 machine - I suppose it's possible that it's something within that machine that is causing this to happen.  Or did something change in the way kexec operates from 16.04 to 20.04 that would cause this?

Does anybody else use kexec to quickly reboot into new kernels?  Are you seeing this behavior with Ubuntu 20.04?

---

