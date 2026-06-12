---
title: "Ubuntu 20.04 with PREEMPT_RT - Loading initial ramdisk..."
date: 2021-05-13
forum: General Help
---

### Post by meta-chan on 2021-05-13
Hello

I am trying to change the kernel of Ubuntu from `5.8.0-53` to `5.9.1-rt20`, but the initialization freezes after `Loading initial ramdisk...`. Adding `loglevel=7 ignore_loglevel verbose` produced no additional output. `dis_ucode_ldr nomodeset` did not help too. Update of BIOS had no effect.

The PC is Fujitsu celsius m770power with Intel Xeon and Nvidia [https://sp.ts.fujitsu.com/dmsp/Publications/public/ds-CELSIUS-M770-power.pdf](https://sp.ts.fujitsu.com/dmsp/Publications/public/ds-CELSIUS-M770-power.pdf) .

fstab:
```
UUID=e2eb5f55-700e-4180-a24a-19512b64316e /               ext4    errors=remount-ro 0       1
UUID=13B6-F4CA                            /boot/efi       vfat    umask=0077        0       1
/swapfile                                 none            swap    sw                0       0
```

I need RT to operate with hardware. Ubuntu was not my choice. Ubuntu 16.04 did function with real-time kernel. GRUB 2.04 is used.

Thank you.

---

### Post by meta-chan on 2021-05-21
[COLOR=#242729][FONT=-apple-system]Grub's "initrd" could not load ramdisk image. The problem was solved by installing and configurating of [/FONT][/COLOR][systemd-boot]("https://wiki.archlinux.org/title/Systemd-boot")[COLOR=#242729][FONT=-apple-system].[/FONT][/COLOR]

---

