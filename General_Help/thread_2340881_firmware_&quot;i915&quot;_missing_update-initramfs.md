---
title: "firmware &quot;i915&quot; missing update-initramfs"
date: 2016-10-22
forum: General Help
---

### Post by harlock593 on 2016-10-22
Hello,

i encounter a recurring issue whenever i try to install a package. i also have dpkg issues but i'll open another topic about that.

[HTML]sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-4.9.0-040900rc1-lowlatency
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915
update-initramfs: Generating /boot/initrd.img-4.9.0-999-lowlatency
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915
update-initramfs: Generating /boot/initrd.img-4.8.0-040800rc6-lowlatency
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915
update-initramfs: Generating /boot/initrd.img-4.8.0-040800rc6-generic
^C #(ctrl+c)
harlock59@EasyNote-TE11HC:~$ 
[/HTML]

---

### Post by ventrical on 2016-10-22
Same here on yakkety release. Installing nouveau-firmware does not seem to help.

regards

---

### Post by cariboo on 2016-10-22
> **ventrical said:**
> Same here on yakkety release. Installing nouveau-firmware does not seem to help.

regards

It wouldn't, because the error message states that the i915 firmware is missing. 

I'm running the 4.8.0-26-generic kernel, I just added the firmware from System Settings->Software & Updates->Additional Drivers, I'll have to wait for the next kernel update to see if it makes a difference.

---

### Post by harlock593 on 2016-10-26
Hi folks,

for some reason, my issue is already solved. i have no idea how but it seems not to show up anymore

```
sudo update-initramfs -u -k all
[sudo] Mot de passe de harlock59 : 
update-initramfs: Generating /boot/initrd.img-4.9.0-999-lowlatency
update-initramfs: Generating /boot/initrd.img-4.8.0-040800rc6-lowlatency
update-initramfs: Generating /boot/initrd.img-4.8.0-999-lowlatency
update-initramfs: Generating /boot/initrd.img-4.8.0-27-lowlatency
update-initramfs: Generating /boot/initrd.img-4.8.0-27-generic
harlock59@Aspire-chbre:~$
```

---

