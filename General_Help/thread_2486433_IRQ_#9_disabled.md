---
title: "IRQ #9 disabled"
date: 2023-04-30
forum: General Help
---

### Post by threedope on 2023-04-30
Hello forum members,

About 1-2 months ago I made the switch to Ubuntu after learning of debootstrap and its potential for building a  system on top of ubuntu-minimal. I waited to seek community support in hopes this issue would be fixed by changes from 22.10 -> 23.04, but unfortunately it persists.

I'm fairly certain that as a result of my encrypted boot process the acpi_irq interrupt handler, IRQ #9, is being flooded with requests thus the kernel disables it. I believe this because when booting from a live USB of Ubuntu or Debian, IRQ #9 is **not **disabled and the one major change I've made is to the way these OSes typically handle FDE booting. To be clear, despite IRQ #9 being disabled the OS boots and everything I've tested seemingly works fine.

Boot overview: an efibootmgr created entry in the Lenovo UEFI system boots a modified version of systemd-boot-efi on the ESP  into a LUKS encrypted btrfs subvolume mounted at /dev/mapper/ that's unlocked via password prompt.

The tools used are btrfs-progs, cryptsetup, cryptsetup-initramfs, initramfs-tools, and a postinst/post-update binutils script to to modify the UKI. Possibly relevant, I'm using zram for swap space.

Here's the output of journalctl -b: [https://pastebin.com/0C4rKN8y](https://pastebin.com/0C4rKN8y)
I've attached my fstab, crypttab, and cmdline in case this is a configuration mistake.
I've also kept a document that details every step taken to create this system which I can post if needed.

Thanks!

---

### Post by MAFoElffen on 2023-05-01
Line #782
```

Apr 30 11:37:46 olgaflow kernel: irq 9: nobody cared (try booting with the "irqpoll" option)

```
Try adding what the error suggests, which is to add 'iurqpoll' as a boot prameter in the GRUB_CMDLINE_LINUX_DEFAULT...

The irqpoll boot parameter option does, is when an interrupt is not handled, to search all known interrupt  handlers for the appropriate handlers and also check all handlers on  each timer interrupt. This is sometimes useful to get systems with  broken firmware running. It has to do with ACPI handling in the BIOS.

Strange that when researching this, it seems to happen more frequently on Lenovo machines. The explanations on this center around talking about suspected buggy frimware, so what I would try first is to see if there is an update to your BIOS firmware, and see if there is a newer version. This has a few bug reports in kernel.org

RE: [https://groups.google.com/g/linux.debian.user/c/KD3w3gXBIeo?pli=1](https://groups.google.com/g/linux.debian.user/c/KD3w3gXBIeo?pli=1)

---

### Post by threedope on 2023-05-01
I've already tried adding irqpoll to the cmdline. Turned booting into a gamble - sometimes it would crash during boot, sometimes it would boot with lockups and slowdowns. Didn't help with troubleshooting, either. I've also updated the BIOS (which required making a Win11 live USB). No change :(

Everything I've read points to the same thing; buggy Lenovo firmware. Super surprising considering they have a reputation for being the 'Linux friendly' OEM.

---

