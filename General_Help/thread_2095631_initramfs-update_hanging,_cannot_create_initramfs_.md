---
title: "initramfs-update hanging, cannot create initramfs for any kernel"
date: 2012-12-17
forum: General Help
---

### Post by quequotion on 2012-12-17
Just a few minutes ago I noticed a very serious problem with my system.

update-initramfs hangs forever and does not complete the initramfs creation process.

I had thought this was a problem with my kernel, so I purged it and installed an earlier version. I recall this happening in the past and the fix being something along those lines. It didn't work this time.

I didn't realize that I'd purged the ***only*** kernel currently installed and it's original initramfs with it. Yes there was a warning, but I underestimated it's importantce. Oops.

I found that dpkg had made a backup of my kernel's initramfs at some time. I hope that it is bootable.*

I tried update-initramfs with -vvv and found that it hangs at certain modules. The first one was cirrus.ko, which I moved out of the tree. Then it hung on another module. I have yet to try moving every bad module out of the tree to see if it's just a random set of modules that are suddenly and in inexplicably  corrupted, or if the problem is with initramfs-update itself, or with the currently running kernel.

I've also made two changes today that could be problematic: I installed the intel-microcode package and microcode.ctl and I updated my EFI bios. Both seemed to go reasonably well, with no errors whatsoever from the microcode update and only the usual frustrations from the bios update (all BIOS settings reset).

*edit:

It was!

---

### Post by quequotion on 2012-12-17
OK, deep breath in, deep breath out.

I figured it out.

The problem was not the cirrus gpu module, but the one to be loaded next: **i915**

I have just about had it with this buggy module. I'm just happy I have another GPU and I'm not using a laptop. This is just one more on a list of problems I have with this module.

I already had this blacklisted, *in grub*, because of it causing boot failure. I didn't have it blacklisted in /etc/modprobe.d/blaclist.conf because it still caused boot failure if it wasn't blacklisted from grub anyway and once it's blacklisted in grub it shouldn't affect the system any more... right? *wrong*.

I am not entirely certain of this, but I suspect: If a module is blacklisted in grub, but not in /etc/modprobe.d/blacklist.conf, update-initramfs doesn't know what to do about it and so just *stops*. It doesn't throw any errors, it doesn't freeze the computer, and it doesn't exit.

It probably would have taken much longer to figure this out if I wasn't already extremely suspicious of i915. I've had this blacklisted in grub for weeks without any problems until today, including various installs and upgrades that required initramfs updates.

---

### Post by quequotion on 2012-12-17
In case anyone else gets caught by this one: 

My interm workaround was to remove the i915.ko module from **/lib/modules/`uname-r`/kernel/drivers/gpu/drm/i915/** (and put it in /root/badmod/). update-initramfs works without any trouble after this. This also means I have absolutely no way to use my Intel GPU, but that's not a problem for me since I have an nvidia card and only one monitor.

A better solution might be to remove the i915.blacklist option from grub, but then I probably don't get to boot my computer.

Another theoretical solution would be to remove the i915.blacklist from grub, boot into ubuntu, add "blacklist i915" to /etc/modprobe.d/blacklist.conf, update-initramfs -c -k `uname -r`, reboot, and cross my fingers.

---

