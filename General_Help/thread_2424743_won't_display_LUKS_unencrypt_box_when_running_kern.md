---
title: "won't display LUKS unencrypt box when running kernel 4.15.0-58 or higher."
date: 2019-08-13
forum: General Help
---

### Post by cowlitzron on 2019-08-13
I have an install of Lubuntu 18.04 Bionic with a LUKS encrypted LVM.  This works fine when running kernel 4.15.0-54.  But, when running the latest 4.15 at this time which is 4.15.0-58, the unencrypt box fails to appear and it boots to a busybox prompt.  I tried installing the latest kernel 5.0 and I have the same problem.  I have to keep kernel 4.15.0-54 around even though it doesn't have the latest security update.

---

### Post by cowlitzron on 2019-08-13
An error message I got when I booted into recovery mode with kernel 4.15.0-58 is 
> Gave up waiting for root file system device.  Common problems:
 - Boot args (cat /proc/cmdline}
   - Check rootdelay= (did the system wait long enough?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/mapper/ubu-root does not exist. Dropping to a shell!

---

### Post by cowlitzron on 2019-08-15
I didn't have lvm2 and some of its dependencies installed.   I had uninstalled the lvm2 packages earlier not realizing they were needed to detect lvms in new kernels.  I reinstalled lvm2 and needed dependencies then in a terminal typed in a root shell:  update-initramfs -c -k all .  I can now unencrypt the lvm using any kernel.

---

