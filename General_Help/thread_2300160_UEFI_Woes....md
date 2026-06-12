---
title: "UEFI Woes..."
date: 2015-10-24
forum: General Help
---

### Post by mattlach on 2015-10-24
Hey all,

So recently I started running out of space on my main drive, and I thought, why not buy this new fancy PCIe SSD to replace it.

Problem is, now I am stuck with UEFI, instead of the more sane MBR setup, since the PCIe SSD only supports UEFI booting.

So, it took bloody forever to figure out how to convert both my windows install (which I only use for games) and my Linux install to EFI booting, but I finally figured it out.   Or so I thought.

I followed th efollowing process to convert my linux install to an EFI boot:

```

$ sudo mount /dev/sda1 /mnt
$ sudo mkdir -p /mnt/boot/efi
$ sudo mount /dev/sda3 /mnt/boot/efi
$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /proc /mnt/proc
$ sudo mount --bind /sys /mnt/sys
$ sudo mount --bind /run /mnt/run
$ modprobe efivars
$ sudo chroot /mnt
# apt-get install grub-efi-amd64

The following extra packages will be installed:
  efibootmgr grub-efi-amd64-bin
The following packages will be removed:
  grub-gfxpayload-lists grub-pc
...
After this operation, 2,399 kB of additional disk space will be used.

# grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy --debug
```

It worked like a charm for several reboots without any problems.   

Grub came up like I am used to, and I could choose either Linux or Windows as I am used to.

And then suddenly, it didn't work anymore.  I can't even figure out what I might have changed.  Nothing I touched seemed relevant.

Now it boots directly to Windows 10, bypassing grub.

I have looked in the BIOS, and for some reason, the BIOS only sees the Windows 10 EFI entry, not the linux/grub entry that used to be there.

So I mounted the EFI partition to troubleshoot.  The grub efi file is still there in the same folder it was before.  The BIOS SHOULD be seeing it, but it just doesnt show up as a boot option.

I'm at a loss.  I have tried just about everything.   I can not figure out why the grub EFI entry is not popping up as a boot option in the BIOS.

It almost feels like this is an intentional Microsoft sabotage, and someone is having a good laugh somewhere.

I now wish I never had bought this stupid UEFI only SSD, and could just continue using the MBR system.

Any help at all would be appreciated.

---

### Post by ajgreeny on 2015-10-24
See **Boot-Repair** in my signature and follow the instruction there to run the boot-info script, then reply here with the pastebin link you get and someone will hopefully be able to help you.

Do not at this stage accept the default repair suggested, just run the boot-info script.

---

### Post by mattlach on 2015-10-24
> **ajgreeny said:**
> See **Boot-Repair** in my signature and follow the instruction there to run the boot-info script, then reply here with the pastebin link you get and someone will hopefully be able to help you.

Do not at this stage accept the default repair suggested, just run the boot-info script.

So, I actually fixed it by booting from a live CD, mounting the partition and all the system mounts, chrooting into it and reinstalling grub on the EFI partition.

I just can't seem to figure out why I had to do this.  Is it randomly going to keep losing my linux boot, making me do this over and over?

---

### Post by sudodus on 2015-10-24
I don't think that you should blame UEFI. I think Windows 10 is doing things via UEFI.

If it is a desktop computer, maybe you can install Ubuntu in a second drive (separate from the Windows drive). It should make it easier to isolate booting into Ubuntu from booting into Windows. See this link and links from it

[FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by oldfred on 2015-10-24
I have an Asus Z97 and have no issues with UEFI boot.
But I did have to change a lot of settings in UEFI to get it to work in UEFI mode. I would expect your Asus to also need a lot of settings, but do not know difference with your model.

---

