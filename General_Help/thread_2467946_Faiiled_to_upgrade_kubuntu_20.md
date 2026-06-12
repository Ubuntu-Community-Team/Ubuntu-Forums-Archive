---
title: "Faiiled to upgrade kubuntu 20"
date: 2021-10-13
forum: General Help
---

### Post by petrogromovo on 2021-10-13
I try to upgrade my kubuntu 20, but got errors :

```

    # uname -a
    Linux master-laptop 5.11.0-36-generic #40~20.04.1-Ubuntu SMP Sat Sep 18 02:14:19 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
    # sudo apt install -y libnotify-bin
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    libnotify-bin is already the newest version (0.7.9-1ubuntu2).
    The following packages were automatically installed and are no longer required:
      appmenu-gtk-module-common libappmenu-gtk3-parser0 libllvm11 libnvidia-extra-470-server libreoffice-help-common
    Use 'sudo apt autoremove' to remove them.
    0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
    1 not fully installed or removed.
    After this operation, 0 B of additional disk space will be used.
    Setting up linux-firmware (1.187.19) ...
    update-initramfs: Generating /boot/initrd.img-5.11.0-36-generic
    W: Possible missing firmware /lib/firmware/i915/skl_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/bxt_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/kbl_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/glk_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/kbl_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/kbl_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/cml_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/icl_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/ehl_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/ehl_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/tgl_huc_7.5.0.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/tgl_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/tgl_huc_7.5.0.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/tgl_guc_49.0.1.bin for module i915
    W: Possible missing firmware /lib/firmware/i915/dg1_dmc_ver2_02.bin for module i915
    I: The initramfs will attempt to resume from /dev/sdb6
    I: (UUID=28ee0d89-a0cc-45ab-bb0c-aeaee8072afa)
    I: Set the RESUME variable to override this.
    Error 24 : Write error : cannot write compressed block 
    E: mkinitramfs failure cpio 141 lz4 -9 -l 24
    update-initramfs: failed for /boot/initrd.img-5.11.0-36-generic with 1.
    dpkg: error processing package linux-firmware (--configure):
     installed linux-firmware package post-installation script subprocess returned error exit status 1
    Errors were encountered while processing:
     linux-firmware
    E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How can I fix it ?

Thanks in advance!

---

