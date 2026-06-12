---
title: "Ubuntu 4.4 Kernel Install fail"
date: 2016-01-31
forum: General Help
---

### Post by Redalien0304 on 2016-01-31
Have Ubuntu 14.04 4.1.5 kernel installed Works good. Only Special thing i had to do was Reinstall bcmwl-kernel-source for Wifi (Dell Latitude E6400). When i try to install Kernel 4.4 i get this "Building initial module for 4.4.0-040400-genericERROR (dkms apport): kernel package linux-headers-4.4.0-040400-generic is not supported
Error! Bad return status for module build on kernel: 4.4.0-040400-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-040400-generic
W: Possible missing firmware /lib/firmware/i915/bxt_dmc_ver1.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver4.bin for module i915"
Googled bxt_dmc_ver1.bin for module i915 got this page [http://askubuntu.com/questions/717338/installing-4-4-rc7-kernel-yields-i915-module-not-available](http://askubuntu.com/questions/717338/installing-4-4-rc7-kernel-yields-i915-module-not-available)
Tried Suggested fix "[COLOR=#111111][FONT=Consolas]sudo bash -c "echo 'i915 [/FONT][/COLOR]nvme' >> /etc/initramfs-tools/modules"  [COLOR=#111111][FONT=Consolas]sudo update-initramfs -u -k all[/FONT][/COLOR], it got rid of my wifi  on all kernels i think?? did not check all just One., solved that Reinstalling  bcmwl-kernel-source again.Wifi working again."

Any help is Appreciated Thanks.

---

### Post by Redalien0304 on 2016-01-31
Bump Anyone??

---

### Post by k-rob2 on 2016-02-09
I had this exact same problem with a Dell XPS 15 (9550). I'm in Ubuntu 15.10 with kernel 4.3... Tried to upgrade to kernel 4.4.1, I got this error and had to revert back.

Any help with this would be really appreciated. So far, google brings up nothing helpful. 

Thanks!

> **Redalien0304 said:**
> Have Ubuntu 14.04 4.1.5 kernel installed Works good. Only Special thing i had to do was Reinstall bcmwl-kernel-source for Wifi (Dell Latitude E6400). When i try to install Kernel 4.4 i get this "Building initial module for 4.4.0-040400-genericERROR (dkms apport): kernel package linux-headers-4.4.0-040400-generic is not supported
Error! Bad return status for module build on kernel: 4.4.0-040400-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-040400-generic
W: Possible missing firmware /lib/firmware/i915/bxt_dmc_ver1.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver4.bin for module i915"
Googled bxt_dmc_ver1.bin for module i915 got this page [http://askubuntu.com/questions/717338/installing-4-4-rc7-kernel-yields-i915-module-not-available](http://askubuntu.com/questions/717338/installing-4-4-rc7-kernel-yields-i915-module-not-available)
Tried Suggested fix "[COLOR=#111111][FONT=Consolas]sudo bash -c "echo 'i915 [/FONT][/COLOR]nvme' >> /etc/initramfs-tools/modules"  [COLOR=#111111][FONT=Consolas]sudo update-initramfs -u -k all[/FONT][/COLOR], it got rid of my wifi  on all kernels i think?? did not check all just One., solved that Reinstalling  bcmwl-kernel-source again.Wifi working again."

Any help is Appreciated Thanks.

---

### Post by Redalien0304 on 2016-02-10
This page here helped me solve it. 
[http://askubuntu.com/questions/466651/how-do-i-use-the-latest-gcc-4-9-on-ubuntu-14-04](http://askubuntu.com/questions/466651/how-do-i-use-the-latest-gcc-4-9-on-ubuntu-14-04)

---

