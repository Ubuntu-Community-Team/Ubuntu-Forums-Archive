---
title: "Need to restore GRUB, OR I WILL ERASE MY HARD DRIVE AND START FROM SCRATCH TOMORROW."
date: 2019-06-26
forum: General Help
---

### Post by nerv-agent on 2019-06-26
My GRUB got corrupted ("thanks" CloneZilla, for messing up both hard drives), and now I gotta reinstall. My Linux computer as been reduced to a useless brick.  I followed these instructions:  [https://www.youtube.com/watch?v=8lod8sRb_6I](https://www.youtube.com/watch?v=8lod8sRb_6I)  [https://www.youtube.com/watch?v=ajs9rO5upZA](https://www.youtube.com/watch?v=ajs9rO5upZA)  But after:   ```
grub-install /dev/sda *****Using your boot device instead of /dev/sda
```  I get:  ```
Installing for x86_64-efi platform. grub-install: error: cannot find EFI directory. 
```  Please help. **I'm about ready to nuke this hard drive and start all over  again from scratch if I don't find a solution by tomorrow.**

---

### Post by dino99 on 2019-06-26
Ubuntu community propose many wiki/kowto about maintenance; avoid untrusted source.

[https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
[https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition](https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition)

---

### Post by nerv-agent on 2019-06-26
That's another weird thing: GParted isn't on my live image.

It's a Dell Ubuntu 16.04 restore image given to me by their customer service....

---

### Post by Rubi1200 on 2019-06-26
The restore image is probably custom.

"normal" liveCD images all have GParted.

I recommend booting a liveCD, even the image, and use the first link in my signature to create a boot info summary. Note, do not run the repair. Just create a report and paste here so we can take a look and try and help you figure out what is going on.

A simple repair might be needed and could fix things but it might also be more complicated than that.

Thanks.

---

### Post by oldfred on 2019-06-26
Do you have multiple drives?
Is system after 2012, so then is UEFI.

The error is because you have booted in UEFI boot mode, but do not have the required ESP - efi system partition (FAT32 with boot flag) on drive seen as sda.
Is first drive really NVMe not sda or formatted MBR, so would not have an ESP.

---

### Post by nerv-agent on 2019-06-27
> **dino99 said:**
> Ubuntu community propose many wiki/kowto about maintenance; avoid untrusted source.

[https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
[https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition](https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition)

The 2nd link *seems* to have worked. 

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.4 GiB, 1479708672 bytes, 2890056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 70EF62F0-9A2D-4258-AA52-668B616E3259

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048    8802829   8800782   4.2G EFI System
/dev/nvme0n1p2   8804352   12023807   3219456   1.5G Linux swap
/dev/nvme0n1p3  12023808  933806079 921782272 439.6G Linux filesystem
/dev/nvme0n1p4 933806080  964258176  30452097  14.5G EFI System
/dev/nvme0n1p5 964259840 1000214527  35954688  17.1G Linux filesystem


Disk /dev/sda: 29.9 GiB, 32080200192 bytes, 62656641 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1        2048 62656511 62654464 29.9G  c W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p3 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p4 /mnt/boot/efi
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/nvme0n1
Installing for x86_64-efi platform.
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-5.0.2-050002-generic
Found initrd image: /boot/initrd.img-5.0.2-050002-generic
Found linux image: /boot/vmlinuz-4.4.0-150-generic
Found initrd image: /boot/initrd.img-4.4.0-150-generic
Found linux image: /boot/vmlinuz-4.4.0-148-generic
Found initrd image: /boot/initrd.img-4.4.0-148-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Adding boot menu entry for EFI firmware configuration
done
root@ubuntu:/# 
```

But now I am stuck in "emergency mode". I can't access the GUI at all.

Yes, I tried to bring up "journalctl -xb", but I can't copy and paste it (because, stuck in GUI mode), and the log is HUGE. Even if I took a picture of it, it would be tons of pictures.

"fsck" shows that "/dev/nvme0n1p3" is "clean". What the --?!?

Please help. I'll extend the "death sentence" to this weekend, but if I can't fix it by then, it's the death penalty for this hard drive.

---

### Post by oldfred on 2019-06-27
You are showing two efi system partitions (ESP), most systems only work with one. And both are very large.
Windows uses 100MB which can work for dual boot, but we normally suggest 300 to 500MB, for future use.

Remove boot flag from p4. If one of boot loaders installed files to p4 & it is FAT32, you will have to reinstall grub to have correct UEFI entry and may need to remove extra entries in UEFI that refer to incorrect ESP.

---

### Post by nerv-agent on 2019-06-27
How do I remove the boot flags? Do I just have to reformat the partition to ext4 or fat32?

---

### Post by nerv-agent on 2019-06-27
I found time out of my busy schedule to head to the store, buy another USB stick, and used Etcher to flash Ubuntu 16.04 LTS Live CD on it.

> **Rubi1200 said:**
> The restore image is probably custom.

"normal" liveCD images all have GParted.

I recommend booting a liveCD, even the image, and use the first link in my signature to create a boot info summary. Note, do not run the repair. Just create a report and paste here so we can take a look and try and help you figure out what is going on.

A simple repair might be needed and could fix things but it might also be more complicated than that.

Thanks.

I used Boot-Info, and it generated this link:

[http://paste.ubuntu.com/p/PF4Pm7pGSr/](http://paste.ubuntu.com/p/PF4Pm7pGSr/)

A timely reply before Saturday morning would be appreciated.

---

### Post by ccor58 on 2019-06-28
You might try boot repair program  at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have a YUMI thumb drive with a few diagnostics tools on it you can add the boot repair program iso as well. It will repair windows/msdos boot sectors as well as Grub systems. Be careful to specify where you want the boot loader placed especially if you are using the repair program on a dual boot system.

I keep Linux hard drives with grub boot on it only; windows drives have windows boot only so that you can remove the sata linux drives when doing windows updates as some updates fail if a grub loader is detected.

Note the program will also install GRUB on all hard drives if one is not careful to read instructions for default operation and/or advanced optional operation. I have used it many many times and works like a charm saving restarting clean installs.
:D:):D

---

### Post by toon37 on 2019-06-28
What you could also try is making a bootable Super Grub2 Disk (see [here](https://www.supergrubdisk.org/category/download/supergrub2diskdownload/super-grub2-disk-stable)). It doesn't repair your Grub, but you may be able to boot your system from it. Better try this first before erasing everything.

---

### Post by nerv-agent on 2019-06-29
> **ccor58 said:**
> You might try boot repair program  at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have a YUMI thumb drive with a few diagnostics tools on it you can add the boot repair program iso as well. It will repair windows/msdos boot sectors as well as Grub systems. Be careful to specify where you want the boot loader placed especially if you are using the repair program on a dual boot system.

I keep Linux hard drives with grub boot on it only; windows drives have windows boot only so that you can remove the sata linux drives when doing windows updates as some updates fail if a grub loader is detected.

Note the program will also install GRUB on all hard drives if one is not careful to read instructions for default operation and/or advanced optional operation. I have used it many many times and works like a charm saving restarting clean installs.
:D:):D

This seems to have worked! I'm gonna see if I can actually USE my computer tomorrow to back-up files. Hopefully there will be no issues.

---

### Post by nerv-agent on 2019-06-30
Confirmed, GRUB is finally fixed.

---

