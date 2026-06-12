---
title: "Changed default boot option, can't get to boot Ubuntu back."
date: 2023-11-27
forum: General Help
---

### Post by tahatamer on 2023-11-27
Hello fellow ubuntu users, 
I edited my grub config to boot Windows as the default boot option, then realized that the grub menu was set as "*hidden*" in the config. I get no boot menu. I updated the grub config and set it to "*menu*". However, I now can't get* update-grub *to work.
I tried chroot'ing from a live usb stick, ran the following commands:
```
sudo mount /dev/sdb2 /mnt

sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc

sudo mount /dev/sdb1 /mnt/boot
sudo chroot /mnt/

```
I was unable to succeed, as update grub-update threw an error, indicating the grub config wasn't found.
Also, /mnt/boot only contained following directories:
/mnt/boot/EFI/EFI/windows
                            ubuntu
                            grub

Any ideas?

---

### Post by oldfred on 2023-11-27
When you chroot, you have to include the ESP.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)

If you have a typo in /etc/default/grub or in 40_custom, it does not update grub and creates /boot/grub/grub.cfg.new so you can try to find typo.

---

