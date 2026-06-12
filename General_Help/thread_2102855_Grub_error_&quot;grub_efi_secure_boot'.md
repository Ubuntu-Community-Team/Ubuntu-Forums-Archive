---
title: "Grub error: &quot;grub_efi_secure_boot'"
date: 2013-01-08
forum: General Help
---

### Post by user753 on 2013-01-08
Hi,
I have a problem with my Lenovo ThinkPad T420. Since an update, i think two days, ago my laptop won't boot anymore.
I get following error message: 
```
error: symbol not found: 'grub_efi_secure_boot'.
error: symbol not found: 'grub_efi_secure_boot'.
```My Laptop  is running with UEFI BIOS Version 1.42 so it is using EFI but not secure boot. I'm using Ubuntu 12.04 64bit ( GRUB version 1.99-21ubuntu3.7) and formatted my hard disk as following:
_hd0_

[LIST]
[*]gpt1: EFI fat partition
[*]gpt2: /boot (ext2)
[*]gpt3: encrypted with LVM volume group inside
[/LIST]
I think the reason for this is an update of GRUB which messed with my GRUB configuration.
Does anyone have a solution for this? Or some tutorials how I can find a solution myself?

Thanks a lot!
Nils

EDIT:
My GRUB menu entry:
```

setparams 'Ubuntu, mit Linux 3.2.0-35-generic'

recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root 5f965616-ad3e-4b6d-b786-99dba2174bdb
linux /vmlinuz-3.2.0-35-generic root=/dev/mapper/vg_ubuntu-root ro  kopt=root=dev/mapper/vg_ubuntu-root
initrd /initrd.img.3.2.0-35-generic

```Older, previously working kernel versions (tested with 3.2.0-29-generic) do not work either.

---

### Post by oldfred on 2013-01-08
If not using secure boot, 12.04 has UEFI capabilities with grub 1.99 that should work. But 12.10 has grub2 2.00 that works with secure boot. Grub2 2.00 is supposed to be added to 12.04 with the next point release, but I do see additions to 1.99, which may be adding to the issue.

Probably best to run Boot-Repair.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by user753 on 2013-01-08
Ok I tried boot repair with an ubuntu secure remix live usb image and get the following:
[http://paste.ubuntu.com/1510412/](http://paste.ubuntu.com/1510412/)
Should I try the recommended repair? If yes boot repair says:
 "EFI detected. Please check the options." 
 "/boot detected. Please check the options."
But I can't see anything relevant in the advanced options.

---

### Post by oldfred on 2013-01-08
Perhaps the LVM with encryption is preventing Boot-Repair from fully parsing your system.

Normally it will offer a checkbox to use separate /boot  and reinstalls to efi partition. But system is encrypted, so it cannot see rest of system.

---

### Post by user753 on 2013-01-08
So I tried anyway and the problem persists:
[http://paste.ubuntu.com/1510482/](http://paste.ubuntu.com/1510482/)
next thing I did was encrypting the partition:
```
root@ubuntu:~# cryptsetup luksOpen /dev/sda3 crypt_lvm
```now boot-repair says:
```
RAID detected. You may want to retry after installing the [mdadm] packages (sudo apt-get install -y --force-yes mdadm --no install-recommends
```I ignored this message and got as info: [http://paste.ubuntu.com/1510711/](http://paste.ubuntu.com/1510711/)
Should I  try the recommend repair without these mdadm packages or install them first?

EDIT:
Ok I tried it with installation of the mdadm packages ([boot info]("http://paste.ubuntu.com/1511011/")) but when I try to repair I get this error message:
```
 "Please close all your package managers (Software Center, Update  Manager, Synaptic, ...). Then try again." 
```But I'm not running any  package managers!
Any ideas? Or should I try to repair GRUB manually? I suspect that would require some chroot magic?
Good night and thanks for the help so far!

---

### Post by oldfred on 2013-01-08
Bootinfoscript is part of Boot-Repair and I have this in my notes, but do not really know about LVM nor RAID.

       Boot script is able to search LVM partitions if the LVM2 package is install, Fedora needs to be mounted to see it with os-prober
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install gawk
sudo apt-get install xz-utils
# unlzma is equivalent to xz --format=lzma --decompress.

---

### Post by user753 on 2013-01-09
Because boot-repair didn't worked I tried repairing GRUB with chroot:
```

sudo cryptsetup luksOpen /dev/sda3 crypt_lvm
sudo mount /dev/mapper/vg-ubuntu-root /mnt
sudo mount /dev/sda2 /mnt/boot
sudo mount /dev/sda1 /mnt/boot/efi
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -t proc /proc /mnt/proc
sudo cp /proc/mounts /mnt/etc/mtab
sudo chroot /mnt /bin/bash
grub-install /dev/sda
update-grub 

```
Everything went without errors but it didn't change the GRUB error after restart. 
Does anyone know what the "error: symbol not found: 'grub_efi_secure_boot'." error means?

---

### Post by oldfred on 2013-01-09
Since not using secure boot at all, you should not get that error.  I find little reference to it. You may need t report a new bug.

[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bugs?field.searchtext=grub_efi_secure_boot&search=Search&field.status%3Alist=NEW&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bugs?field.searchtext=grub_efi_secure_boot&search=Search&field.status%3Alist=NEW&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

       bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by user753 on 2013-01-09
Great! I solved the problem!
grub-install and grub-update are installing to ```
sda1/EFI/ubuntu/grubx64.efi
``` but the Lenovo implementation of UEFI seems to recognize only: ```
sda1/EFI/boot/bootx64.efi
``` so i just mounted the partition in a live system an copied+renamed grubx64.efi to bootx64.efi

Thanks a lot for your help!

---

### Post by K4nia on 2013-01-11
> **user753 said:**
> Great! I solved the problem!
grub-install and grub-update are installing to ```
sda1/EFI/ubuntu/grubx64.efi
``` but the Lenovo implementation of UEFI seems to recognize only: ```
sda1/EFI/boot/bootx64.efi
``` so i just mounted the partition in a live system an copied+renamed grubx64.efi to bootx64.efi

Thanks a lot for your help!

Hi!
I have the same problem with efi_secure_boot... 
I did what you have mentioned:

[LIST=1]
[*]I mounted my /dev/sda1 partition using a live-USB
[*]After mounting in folder /mnt I can see a folder called /EFI but there is no /sda1
[*]In /EFI folder there are 3 folders: Microsoft, Boot, Ubuntu
[*]In folder /ubuntu there was in fact the file that you mentioned and I changed it the way You suggested (I first change just the name, It didn't work, then I copied the file that was in folder /Boot which had a proper name, but it also didn't work
[*]Can You please help me? Maybe I´m doing something wrong?
[/LIST]

I would be very thankfull for the help. I don´t want to reinstall the system again.

---

### Post by oldfred on 2013-01-11
@K4nia
Please start your own thread & post BootInfo report. Many systems seem to hav efi partition as sda2 or even sda3. UEFI spec says it should be first, but must not have to be.

---

