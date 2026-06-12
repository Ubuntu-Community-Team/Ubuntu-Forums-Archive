---
title: "Ran apt-get upgrade and now can't boot."
date: 2006-12-13
forum: General Help
---

### Post by tarkus on 2006-12-13
Hi everyone.  This morning I ran an apt-get upgrade on my existing, working Edgy system.  It then asked me to reboot (presumably because it upgraded libc) but the system will not come back up.  If I turn off splash, I can watch the kernel messages.  It prints out all the RAID information (md: assembling array, etc) followed immediately by the message "Done."

Then the system hangs.  I let it run for half an hour or so and when I came back, it was at the (initramfs) prompt.

My root filesystem is on lvm.  So from there, I tried to run vgchange -ay.  I get the error: "lvm: relocation error: lvm : symbol _dm_tree_add_new_dev_mode, version Base not defined in file libdevmapper.so.1.02 with link time reference" and it does not activate my LVM volumes.

pvs and lvs show all my physical and logical volumes fine.

Any ideas?
Thanks,
Steven

---

### Post by .t. on 2006-12-13
OK. At the GRUB menu, press Escape. Then press "e" to edit the selected menu item, then move down to the "kernel" line. Press "e" again to edit this line (don't worry, it's not permanent), and remove "quiet", "silent" and "splash" from the list provided there. Leave everything else as it is. Then, press enter to save that for this boot, and press "b" to boot this kernel. Post any error messages it throws up at you. Thanks, .t.

---

### Post by tarkus on 2006-12-13
There were no error messages.  It just configured RAID, then hung.


Turns out that somehow in the upgrade one of the libraries/binaries in the initrd got fouled up.  I reinstalled the lvm-common and lvm2 packages and rebuilt the initrd.  Looks good now.

As an aside, working from the Desktop Livecd is a real pain with lvm.  Each time you reboot, you have to apt-get install --reinstall the kernel packages to get the proper lvm modules, and then install lvm2 and such to get the apps.  Why don't they come installed by default?  Seems like it would be useful for recovery...

Ah, well.

---

