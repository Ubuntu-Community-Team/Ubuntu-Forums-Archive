---
title: "remove signed boot"
date: 2012-10-25
forum: General Help
---

### Post by sonicb00m on 2012-10-25
How do i remove the signed boot? I can't get grub to install properly and I cant reorder the menu.

Have tried with 

rub-install --efi-directory=/boot/efi/ --target=x86_64-efi --recheck --debug

But it fails with

+ efibootmgr -q -c -d /dev/sda -p 1 -w -L ubuntu -l \EFI\ubuntu\grubx64.efi
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.

---

### Post by dino99 on 2012-10-25
so whats returns that command ?

maybe its better to ask on askubuntu to get devs answers.

---

### Post by sonicb00m on 2012-10-25
I am thinking of jumping to Linux Mint because Ubuntu is becoming more Windows like every release. I was fairly happy with 12.04 but now it feels a bit like the Gnome mentality that "we know what's best for your system" and no longer giving any options.

That is output of the grub-install debug..

```

Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
+ fgrep -i  ubuntu
+ /usr/sbin/grub-probe --target=drive --device-map= /boot/efi//EFI/ubuntu
+ efidir_drive=(hostdisk//dev/sda,msdos1)
+ /usr/sbin/grub-probe --target=disk --device-map= /boot/efi//EFI/ubuntu
+ efidir_disk=/dev/sda
+ test -z (hostdisk//dev/sda,msdos1)
+ test -z /dev/sda
+ echo (hostdisk//dev/sda,msdos1)
+ sed s/^([^,]*,[^0-9]*//; s/[^0-9].*//
+ efidir_part=1
+ efibootmgr -q -c -d /dev/sda -p 1 -w -L ubuntu -l \EFI\ubuntu\grubx64.efi
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
+ test -z 
+ test -e /boot/grub/stage2
+ gettext Installation finished. No error reported.
Installation finished. No error reported.+ echo

```

I tried to modprobe but it doesn't fix the grub-install.

I just want to remove the whole thing. I don't use Windows at all so i don't see why i should be forced to use the signed boot mode.

---

### Post by oldfred on 2012-10-26
Unless you have a new Windows 8 system, you should not have signed boot. But grub is being updated to work with signed boot and error may be from something else?

If you have Windows 8 you have to turn signed boot off in UEFI if you do not want it.

If you do not have Windows 8 run this:

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by sonicb00m on 2012-10-29
Thanks, that program worked nicely!

---

