---
title: "Computer will no longer boot!"
date: 2013-04-08
forum: General Help
---

### Post by gromituk on 2013-04-08
Hello.  I'm rather at my wits' end about this, so I hope that someone can help.

My father has a new PC (UEFI) on which he installed Ubuntu 12.04 64-bit from a USB stick using Startup Disk Creator.  This worked perfectly; surprisingly, he didn't even have to change the boot order to get it to install.  I told him to tell it to use the whole disk: parted reports

/dev/sda1 fat32 94MiB flags: boot
/dev/sda2 ext4 925.53Gib
/dev/sda3 swap 5.89GiB

I visited him soon after, and did some work on it including normal updates, but nothing fundamental.  It would have been rebooted several times during this process.  The first time he switched it on after I had left, it failed to boot, returning to the GRUB menu.  Trying to boot the current or any previous kernels, normal or recovery mode, results in the same thing - a blank screen, with ctrl-alt-delete not triggering a reboot.  Recovery mode reports the kernel and initrd loading messages but nothing more.  Memtest doesn't work (command not found) but I gather that UEFI doesn't support 16-bit applications so that's a red herring.  I got him to put rescatux on the stick and this can't get beyond the four-option main screen either.  Entering the "BIOS" from the grub menu works and I got him to switch off secure boot, which makes grub's ls work:

(hd0) (hd1) (hd2) (hd3) (hd3,msdos1) (hd4) (hd4,gpt3) (hd4,gpt1) (hd5)

but that makes no difference otherwise.

What does work is the live stick, so I can get into the system and examine it.  It will happily mount /dev/sda2.  Unfortunately it's all being done by remote control with him on the phone, so you can imagine it's quite painful #-o.  I got him to re-make the stick with a persistence file and to install ssh server in the hope that I could at least log into it remotely and poke around more productively, but then I realised I'd also have to assign it a static IP address like I did in the install as the ADSL router will only do virtual server mappings by IP address, so I've not crossed that hurdle yet.  (I am also not convinced about how persistent settings like that would be.)

I got him to dictate the results of "e" on the default boot menu and this (typos and mishearings notwithstanding) is what I got:

set params "ubuntu, with linux 3.5.0-26-generic"
recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_gpt
insmod ext2
set root="(hd0,gpt2)"
search --no-floppy --fs-uuid --set=root *<uuid>*
linux /boot/vmlinuz-3.5.0-26-generic.efi.signed root=UUID=*<uuid>* ro quiet splash $vt_handoff
initrd /boot/initrd.img-3.5.0-26-generic

I read that problems like this can be caused by an add_efi_memmap kernel parameter but that doesn't seem to be present.

Any ideas or requests for more info please?  Many thanks!

---

