---
title: "Grub rescue (boot partition on usb drive): can't restore grub even after 20 chroots"
date: 2014-05-07
forum: General Help
---

### Post by john214 on 2014-05-07
Hi,

I'm using 13.10. I'm struggling with a file not found/grub rescue> at startup. Grub (EFI) is on a USB stick (fsck done, no issue), and should load initramfs to boot my main partition (which is encrypted). But it doesn't.
When I [FONT=courier new]ls /[/FONT] in grub rescue, I obtain as expected the ls of my boot partition, so it can perfectly read it (and it knows it's the boot partition):

```
abi-3.11.0-19-generic           initrd.img-3.8.0-34-generic
abi-3.11.0-20-generic           lost+found
abi-3.8.0-34-generic            memtest86+.bin
backup_2014-05-07__07h1957.zip  memtest86+_multiboot.bin
config-3.11.0-19-generic        script.sh
config-3.11.0-20-generic        script.sh~
config-3.8.0-34-generic         System.map-3.11.0-19-generic
efi                             System.map-3.11.0-20-generic
efin                            System.map-3.8.0-34-generic
extlinux                        vmlinuz-3.11.0-19-generic
grub                            vmlinuz-3.11.0-20-generic
initrd.img-3.11.0-19-generic    vmlinuz-3.8.0-34-generic
initrd.img-3.11.0-20-generic
```

But insmod linux or insmod normal return* file not found*. Anyway, I've chrooted from a 13.04 usb key (as I'm going to explained) and done everything I could do if I managed to boot the system this way and the problem is still there. So I don't think that messing around with grub rescue console is a solution.

As the backup file in the list shows it, I've tried boot-repair with no success. Even though I do check separate /boot and separate /boot/efi (because it's the case), I get the message "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option." and nothing is solved. [Here is the boot repair log]("http://paste.ubuntu.com/7411837/"). sdh is the live usb. 

I've also chrooted 20 times (literally), where I've purged grub, linux-image, installed, reinstalled, update(d)-grub, grub-install(ed), in every possible order but with absolutely no success.

All I can find online is "chroot, purge grub, update-grub, and voilà" which is absolutely doing nothing here. Do you have any suggestion to fix this? It's quite frustrating (and professionally quite catastrophic) to see all my files.. but not being able to boot.

Thank you very much for your life-saving help.

---

### Post by john214 on 2014-05-08
An old fashioned bump since I'm not making any progress on my own...

Thanks for your help.

---

