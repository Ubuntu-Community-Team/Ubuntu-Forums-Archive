---
title: "update-grub setting wrong root partition  Ubuntu 14.04 LTS"
date: 2014-05-20
forum: General Help
---

### Post by mcvickj on 2014-05-20
When I run update-grub this it the output I see...

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04 LTS (14.04) on /dev/sda1
done



Output of fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda2        39065598   625141759   293038081    5  Extended
/dev/sda5        39065600    46876671     3905536   82  Linux swap / Solaris
/dev/sda6        46878720   625141759   289131520   83  Linux


/dev/sda1 = /bak
/dev/sda5 = swap
/dev/sda6 = /

/bak is a full rsync of /.  This computer is setup for a public station.  If something were to ever happen to the live file system I can execute a command that runs an rsync from /bak to / to restore it.  My problem is Ubuntu is booting using the grub.cfg it sees on /dev/sda1 instead of /dev/sda6.  How do I get grub to ignore /dev/sda1 and use /dev/sda6?

---

### Post by LastDino on 2014-05-20
Are you been presented a different option for both / and /bak in grub menu or it is showing only one? If you can see both and can boot into /, you can simply install grub there and it should be preferred one, then you can install grub customization and remove the /bak entry if you absolutely must.

To install grub.
> sudo update-grub
sudo grub-install /dev/sda6

---

### Post by grahammechanical on 2014-05-20
My advice would be to double check that you do indeed have this problem. update grub is finding this

> Found linux image: /boot/vmlinuz-3.13.0-24 generic

and that is Ubuntu 14.04 on sda6. This must be the case otherwise update-grub would not say

> Found Ubuntu 14.04 LTS (14.04) on /dev/sda1

It would say

> Found Ubuntu 14.04 LTS (14.04) on /dev/sda6

update grub always shows the linux images and the initrd images for the Ubuntu we are running update-grub from and then references other installations of Ubuntu by something like Ubuntu 14.04 LTS (14.04) on /dev/sda?   This is what I get

> Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.13.0-23-generic
Found initrd image: /boot/initrd.img-3.13.0-23-generic
Found linux image: /boot/vmlinuz-3.13.0-21-generic
Found initrd image: /boot/initrd.img-3.13.0-21-generic
Found linux image: /boot/vmlinuz-3.13.0-16-generic
Found initrd image: /boot/initrd.img-3.13.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda10
Found Ubuntu 14.04 LTS (14.04) on /dev/sda2
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda5
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda6
Found Ubuntu Trusty Tahr (development branch) (14.04) on /dev/sda7
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda9
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sdb1
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sdb5
Found Ubuntu 14.04 LTS (14.04) on /dev/sdb9

I am running Utopic Unicorn (14.10) on sdb8 but you will not see it listed. But it is there as vmlinuz-3.13.0-24-generic. It still has the same Linux version as 14.04 but that will change and the list will get even longer.



Regards.

---

### Post by oldfred on 2014-05-20
If your are doing a full rsync, did you do a full image copy originally.

You may have duplicate UUID, or the install in sda1 has same fstab & grub files as sda6.

Post link to BootInfo report, then we can see details of UUIDs and grub.cfg, fstab etc between two installs.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

