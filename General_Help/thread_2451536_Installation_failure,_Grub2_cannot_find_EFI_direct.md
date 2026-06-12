---
title: "Installation failure, Grub2: cannot find EFI directory"
date: 2020-10-06
forum: General Help
---

### Post by daanheuvelbeuk on 2020-10-06
Hi,

I have had a running dual boot dual disk system since 2016. While I was on my Ubuntu install I got the message to update my 18.xx version to 20.04. After some time the installation halted. Nothing happened, except a spinning HD. I rebooted my system, and burned a Live CD (20.04.1) on a DVD while running Windows 10. When installing Ubuntu from the live DVD it fails on installation of Grub2:
```
Executing 'grub-install /def/sda' failed
This is a fatal error.
```
I still had about one third of the installation to run.


Next I looked on the Internet to find out how to [Repair Grub2 with Live CD]("https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd"). I followed the instructions carefully, although I made a typo, which I could correct. But this try also failed:
```
grub-install /dev/sda
grub-install: error: cannot find EFI directory
```

And to make matters worse, my Windows is missing from the Grub menu. So I am writing this in Firefox of the Live DVD.

What can I do?

---

### Post by daanheuvelbeuk on 2020-10-06
Fwiw:
```
/dev/sda
    /dev/sda1/    swap
    /dev/sda2/    ext4    root
    /dev/sda3/    ext4    data
```

---

### Post by daanheuvelbeuk on 2020-10-06
Trying the [Internet]("https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd"), I read that "by default it assumes the EFI system is mounted as /boot/efi"
```
ubuntu@ubuntu:~$ mount | grep /boot/efi
```
No result.

```
ubuntu@ubuntu:~$ mount | grep efi
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
```

And that is not the same as /boot/efi.

---

### Post by daanheuvelbeuk on 2020-10-06
Tried it again. The error message now is:
```
The 'grub-efi-amd64-signed package failed to install into / target/. Without the GRUB boot loader,  the installed system will not boot.
```

Sigh.

---

### Post by daanheuvelbeuk on 2020-10-06
Still trying to finish the installation, using [Repair Grub2 with Live CD]("https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") I tried:

```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda /mnt
mount: /mnt: /dev/sda already mounted or mount point busy.

```

Continue?

```
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev &&
> sudo mount --bind /dev/pts /mnt/dev/pts &&
> sudo mount --bind /proc /mnt/proc &&
> sudo mount --bind /sys /mnt/sys
mount: /mnt/dev: mount point does not exist.
```

So, still no luck. And I do want at least my Windows 10 back.

---

### Post by daanheuvelbeuk on 2020-10-06
Found the solution. In [UEFI - Community help]("https://help.ubuntu.com/community/UEFI") it is explained that you have to create an EFI System partition. 

> If you are manually partitioning your disk in the Ubuntu installer, you need to make sure you have an [EFI System Partition (ESP)]("http://en.wikipedia.org/wiki/EFI_System_partition") set up. This partition holds EFI-mode boot loaders and related files. 


[LIST]
[*]If your disk already contains an ESP (eg if your computer had Windows 8 preinstalled), it can be used for Ubuntu too. **Do not format it.** It is strongly recommended to have only 1 ESP per disk. 
[*]An ESP can be created via a recent version of [GParted]("https://help.ubuntu.com/community/GParted") (the Gparted version included in the 12.04 disk is OK), and must have the following attributes:
[LIST]
[*]*Mount point:*  /boot/efi  (remark: no need to set this mount point when using the  manual partitioning, the Ubuntu installer will detect it automatically) 
[*]*Size:* minimum 100Mib. 200MiB recommended. 
[*]*Type:* FAT32 
[*]*Other:* needs a "boot" flag 
[/LIST]
   
[/LIST]


I still have to repair my bootloader. My system started as if Windows was not there. And I need to change my home directory to my existing home partition.

---

