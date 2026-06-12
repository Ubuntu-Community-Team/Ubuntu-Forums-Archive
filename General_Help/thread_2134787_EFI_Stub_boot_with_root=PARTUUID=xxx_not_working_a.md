---
title: "EFI Stub boot with root=PARTUUID=xxx not working any more in 3.5.0-27-generic"
date: 2013-04-12
forum: General Help
---

### Post by dmazar on 2013-04-12
I was able to boot Ubuntu 12.10 3.5.0-17-generic and 3.5.0-25-generic, direct EFI stub boot with the following cmdline:

[FONT=courier new]root=PARTUUID=d71c5811-5b68-4aef-8973-8aa9add5ec3c add_efi_memmap quiet splash vt.handoff=7[/FONT]

but this is not working any more with 3.5.0-27-generic.

I can boot it via EFI stub with specifying:

[FONT=courier new]root=/dev/sda6 ro initrd=\boot\initrd.img-3.5.0-27-generic add_efi_memmap[/FONT]
or
[FONT=courier new]root=/dev/disk/by-partuuid/d71c5811-5b68-4aef-8973-8aa9add5ec3c ro initrd=\boot\initrd.img-3.5.0-27-generic add_efi_memmap[/FONT]

but when using PARTUUID only, it's not workign any more. Any advice on this?

A reason why I am using PARTUUID:
I'm Linux newbie and have plain simple Ubuntu install on a partition on GPT disk (no RAID and similar stuff). I'm workign on Hackintosh Clover bootloader and adding some more support to it for Linux UEFI booting (via EFI stub, [here]("http://www.projectosx.com/forum/index.php?s=&showtopic=2598&view=findpost&p=26810")). I have some config file where I can specify where to search for linux kernels and which kernel boot options to use. I can use some variables in there, like ${PARTUUID} and ${Initrd} which are populated by Clover based on detected kernel.

The goal is to have kernel boot options defined as universal as possible to allow autodetection and booting of simple Linux installs (via EFI stub) and to still allow users to adopt it for their particular setup. That is why I liked booting only with this:
[FONT=courier new]root=PARTUUID=${[/FONT][FONT=courier new]PARTUUID[/FONT][FONT=courier new]} [/FONT][FONT=courier new]add_efi_memmap[/FONT]
Kernel is started directly from it's ext4 partition, PARTUUID can be easily determined by Clover and no other options were needed to get the thing started.

And few questions regarding this:
1. Why I do not need to specify initrd when booting 3.5.0-17-generic with root=PARTUUID=...? Actually, if I specify it, then system does not boot.
2. Whay is PARTUUID not working any more in 3.5.0-27-generic?
3. Is booting with "[FONT=courier new]root=/dev/disk/by-partuuid/${PARTUUID} ro initrd=${Initrd}[/FONT]"  better then just with PARTUUID and no initrd?

Thanks.

---

