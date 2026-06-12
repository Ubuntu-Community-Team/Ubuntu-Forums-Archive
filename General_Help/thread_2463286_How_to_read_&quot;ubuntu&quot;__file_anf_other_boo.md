---
title: "How to read &quot;ubuntu&quot;  file? anf other boot qustions"
date: 2021-06-08
forum: General Help
---

### Post by anneranch on 2021-06-08
Here is my current efibootmgr file. 

Where is "ubuntu" file ? 
(how do I read it ?) 

What is "hard drive " entry ? 
What is "USB" entry ? 

Can  I   safely  delete anything from file?

What builds the efibootmgr and when ?

How does "update-grub" fits with efibootmgr ? 


qe@qe-desktop:~$ efibootmgr 
BootCurrent: 000A 
Timeout: 3 seconds 
BootOrder: 000A,000C,000B,0012,0013,0014,0015,0016,0017,0018,0019,0002 
Boot0002  USB  
Boot000A* ubuntu 
Boot000B* Hard Drive  
Boot000C* ubuntu 
Boot0012* UEFI: Seagate BUP Ultra Touch 0004 
Boot0013* UEFI: Seagate BUP Ultra Touch 0004 
Boot0014* UEFI: Seagate BUP Ultra Touch 0004 
Boot0015* UEFI: Seagate 
Boot0016* UEFI: Seagate 
Boot0017* UEFI: Seagate 
Boot0018* UEFI: Seagate 
Boot0019* UEFI: Seagate 
qe@qe-desktop:~$

---

### Post by yancek on 2021-06-08
[QUOTE][Where is "ubuntu" file ?[ /QUOTE]

The ubuntu entry shown with efibootmgr refers to the efi boot files on the EFI partition which are in a directory named ubuntu.  There are multiple files there including a small grub.cfg file which points to the actual grub.cfg file on the / (root filesystem) partition.

The Hard Drive entry will boot whatever OS was preinstalled when you purchased the computer.  The USB entry should allow you to access/boot a USB drive.  The other entries likely point to addtional internal/external drives recognized by your BIOS firmware, no need to delete anything.  efibootmr is software which is included with EFI systems.

After ubuntu is selected from EFI it goes to the grub.cfg file on the / partition and update-grub updates this file when run.

---

### Post by grahammechanical on 2021-06-08
> Can  I   safely  delete anything from file?

I would say that there are conditions that must be met before the word "safely" applies. A "Yes" or "No" answer would put a person in the situation of "a little knowledge is a dangerous thing."

> Let&#8217;s say you have installed multiple Linux distributions on a hard  disk so you have multiple boot entries just like the above screenshot.  And now you deleted a Linux distro but the boot entry is still there. To  remove the respective boot entry, run

```

sudo efibootmgr -b <bootnum> -B
```

Source?

[https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

Reading that tutorial has taught me something. One day I might own a UEFI motherboard and the information or at least the knowledge that the information is out there somewhere might be useful

Regards.

---

### Post by oldfred on 2021-06-08
change your question to 
sudo efibootmgr -v

see also 
man efibootmgr

Ubuntu often has two entries, one using /EFI/ubuntu/grubx64.efi and one using shimx64.efi.
Shim is used for secure boot and grub if UEFI Secure Boot not on. But Shim always works. I noticed now my system only has shimx64.efi.
Your fstab mounts ESP as /boot/efi, so full path then is /boot/efi/EFI/ubuntu once mounted.

UEFI uses GUID/partUUID to know which ESP - efi system partition to find boot files.
Drives in UEFI boot mode boot from /EFI/Boot/bootx64.efi.
Bootx64.efi may be a copy of Windows .efi boot file or shimx64.efi.

To see GUID/partUUID:
lsblk -e 7 -o name,mountpoint,label,size,fstype,uuid,partuuid,uuid

To see ESP mount and / partition mount.
cat /etc/fstab

---

### Post by anneranch on 2021-06-08
I am stiil not sure how "grub"  gets into picture. 
I  have been testing the OS , using grub info  dev/sdxy and when it does not fully load the OS I go to gparted and delete the partition .
I found this cumbersome, but gparted  "goes by "  .de/sdxy .
Then I run update-grub to verify the OS is gone. 
So far I not check efibootmgr.

Back to the posted file - so now I know I have TWO "ubutu" entries on different HDD 
and corresponding efibootmgr.
in theory I should never run the second "ubuntu " entry .

---

### Post by oldfred on 2021-06-08
If you know which entry is now invalid, you can delete it.

sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

