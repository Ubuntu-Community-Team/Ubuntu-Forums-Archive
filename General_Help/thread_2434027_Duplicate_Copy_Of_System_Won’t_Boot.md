---
title: "Duplicate Copy Of System Won’t Boot"
date: 2019-12-29
forum: General Help
---

### Post by box02-0 on 2019-12-29
Hi.

I’m running a dual boot system (Ubuntu 18.04 & Windows8) on a 512gb ssd. (The Windows portion is up front on sda1 & sda2, ubuntu is on sda4.) I want to make an EXACT copy of the 512gb ssd onto a Transcend StoreJet 1Tbyte USB2 drive, giving me a bootable backup on a removable drive.

I booted with ubuntu on a usb , and plugged in the Transcend StoreJet 1Tbyte USB2 which is on /dev/sdb. The Live ubuntu/Windows ssd is /dev/sda. In Terminal:

mg@ubuntu:~$ sudo dd if=/dev/sda of=/dev/sdb bs=1M
488386+1 records in
488386+1 records out
512110190592 bytes (512 GB) copied, 11413.7 s, 44.9 MB/s  (3 Hours)

I then try to boot the Transcend, and it starts to work. The grub.cfg Menu comes  up asking me if I want ubuntu or Windows, I select ubuntu and the ubuntu logo comes up with the infamous dots below. After 2 dots are colored, it stops. And that is as far as it will go.

I then boot my regular system and plug in the Transcend and I get:
 “Unable to mount 367 mb volume , wrong fs type, bad option, bad superblock, missing codepage or helper program, or other error.”

Then I run Gparted and the Transcend partitions all look fine except for the very first partition – it has an exclamation mark in front of it, shows File System as ext4 (should be ntfs Windows Sysres), and nothing in the used/unused columns. In the Flags column, it does correctly say “boot”. When I select Properties on this partition, I get:

“error mounting /dev/sdb1 ,,,, wrong fs type, bad option, bad super block on /dev/sdb1, missing code page or helper program, or other error.”


What happened to this first partition, and how can I fix it?

Thanks for your help,
M…..

---

### Post by oldfred on 2019-12-29
You dd copy is an exact copy.
And that is normally for same size to same size drive & later recovery.
You cannot have duplicated UUIDs, so you cannot use copy while original still connected.
 
Error is probably because that UUID is already mounted.

---

### Post by box02-0 on 2019-12-30
Yes I know about duplicate UUID's. So after I made the exact copy, I BIOS disabled the SSD, and attempted to boot the supposed exact copy of the SSD on the Transcend StoreJet.

Starts off looking great, but hangs after displaying ubuntu and a few dots. (This is the point where it would ask for my Password.)

I just don't understand why it won't boot- it should be an exact copy. The extra space (512GB from SSD to 1TB on Transcend) correctly shows as "unallocated" on the Transcend. It all looks good except for the  "**!**"  on the Windows8 350MiB 1st partition.

So I BIOS enable my SSD, plug in the Transcend usb, and boot from ubuntu on another usb. The very 1st partition on the Transcend is showing with an exclamation mark. I don't know why. So I Gparted copy the very first partition from the SSD back to the Transcend. Now it looks good, only it does not say 'boot' under the Flags column.

So I tried a boot-repair on the Transcend. Still no go.

Any ideas ?

Thanks,
M....

---

### Post by oldfred on 2019-12-30
Post link summary report from Boot-Repair.

If UEFI, internal system will boot from /EFI/ubuntu, but if external drive it will boot from /EFI/Boot/bootx64.efi, usually a copy of shimx64.efi which also requires /EFI/ubuntu folder in ESP.
One is Ubuntu entry and other is a hard drive entry or like you boot of Ubuntu live installer which also uses /EFI/Boot/bootx64.efi, but a limited version of grub/shim just for booting live installer.

---

