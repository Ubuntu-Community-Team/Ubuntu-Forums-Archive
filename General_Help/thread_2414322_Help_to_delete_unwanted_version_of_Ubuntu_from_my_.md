---
title: "Help to delete unwanted version of Ubuntu from my machine."
date: 2019-03-08
forum: General Help
---

### Post by vysero on 2019-03-08
The last time I attempted to delete a version of Ubuntu from my machine some kind of boot loader problem occurred and I had to go through a long process to get everything working again and i want to avoid that. So currently my machine is running 16.04 and that is what I use. However, there is also a 12.04 of this machine that is just taking space I would like to free up that space.

It is hard to say what is what. When I open the Disks utility none of these partitions on the various drives have useful names. I believe the 16.04 lives on the solid state drive while the 12.04 lives on the 1TB hard drive. The hard drive has 5 partitions:

First one is just called: Partition 1 and its 134 MB the device location is /dev/sda1 it says the type is Microsoft Reserved (no Microsoft OS on this computer) and it says the contents are unknown.

The second is called DATA and I made this a long time ago.

The third is called partition 3 its 1.0 MB. Its @ /dev/sda3 and the partition type is BIOS boot contents unknown.

The fourth is called a Filesystem. Its 487 GB located @ /dev/sda4. The partition type is Linux Filesystem and ints contents are: Ext4 (version 1.0) -- Not Mounted (I believe this is the 12.04)

The fith is called: Swap. its 17 GB @ /dev/sda5, the partition type is: Linux Swap and the Contents are: Sweap (version 1) -- Not Active


What do I need to delete from this hard drive to get rid of Ubuntu 12.04 and can I do it in a way that won't screw up my boot loader?

---

### Post by yancek on 2019-03-08
The information in your post shows only one possible system install which would be sda4.  Unless you named one of the Ubuntu installs Data from the other.  Can you still boot 12.04?  If so, do that and from a terminal run the command df -h.  The example output below shows the booted system is on sda6.  Whichever partition shows the Mounted on with the forward slash ( / ) is the filesystem, or 12.04.  If you can''t boot 12.04, boot 16.04 and run the same command.  The partitions 1, 3 and 5 can't be either.  When you get the correct partition for 12.04, you don't delete it you format it.  It's an operating system not an application.

> df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        50G   16G   32G  34% /


---

### Post by thehipho on 2019-03-08
If you installed 16.04 last on your machine, and you currently are able to boot it, then you should have the boot-loader on it.
As for deleting the whole 12.04 partition. You should make sure that it does not effect your current boot order!

```
sudo fdisk -l
```

---

### Post by Impavidus on 2019-03-09
While running your 16.04 from the SSD, use these commands to tell what partitions are there and which of them are used by 16.04:```
sudo parted -l
df -h
```parted is the more modern version of fdisk, but you could fdisk as well. This may tell you which partitions can be removed.

As for the boot loader, the last Ubuntu system installed takes control over the boot loader (=grub). This is probably 16.04. Whenever the package manager installs an upgrade to grub, the OS installing that upgrade can take back control over grub. 12.04 hasn't had any upgrades to grub for 2 years as it has been unsupported for that time, whilst 16.04 had several. 16.04 should already control grub.

---

### Post by NM5TF on 2019-03-09
I have used OS-Uninstaller before with good results....

[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

simple GUI.....

tommy

---

### Post by vysero on 2019-03-11
I decided to go with the OS-Uninstaller option. I ran the program and it said 12.04 was successfully removed. I haven't tried restarting my computer yet because the program told me:

We hope you enjoyed it and look forward to read your feedback.You can now reboot your computer.
Please do not forget to make your BIOS boot on We hope you enjoyed it and look forward to read your feedback.You can now reboot your computer.
Please do not forget to make your BIOS boot on nvme0n1p1/EFI/ubuntu/shimx64.efi file!

How would I go about making my BIOS boot on nvme0n1p1/EFI/ubuntu/shimx64.efi file?

---

### Post by vysero on 2019-03-13
Bump

---

### Post by yancek on 2019-03-13
Look in the BIOS boot options and see if you have something like 'Boot from EFI file'.  Different manufacturers have different methods of doing this and we don't know what you have so it's not possible to give more details.

---

### Post by oldfred on 2019-03-13
This should show UEFI boot options:
sudo efibootmgr -v

You may have two ubuntu entries, one uses shim & other grub, see detail in above command.

---

### Post by vysero on 2019-03-13
```
rob@linux038:~$ sudo efibootmgr -v
[sudo] password for rob: 
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0007,0008,0009,000A,000B,000C,000D
Boot0000* ubuntu    HD(1,GPT,adeaa359-5ecc-439a-8eca-498c36b29c28,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0007* UEFI: KXG50ZNV256G NVMe TOSHIBA 256GB    HD(1,GPT,adeaa359-5ecc-439a-8eca-498c36b29c28,0x800,0x100000)/File(EFI\boot\bootx64.efi)..BO
Boot0008* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot0009* KXG50ZNV256G NVMe TOSHIBA 256GB    BBS(HD,KXG50ZNV256G NVMe TOSHIBA 256GB,0x0)..BO
Boot000A* P0: ST1000DM010-2EP102    BBS(HD,P0: ST1000DM010-2EP102,0x0)..BO
Boot000B* USB Storage Device    BBS(USB,USB Storage Device,0x0)..BO
Boot000C* P0: HL-DT-ST DVD-ROM DTA0N        BBS(CDROM,P0: HL-DT-ST DVD-ROM DTA0N    ,0x0)..BO
Boot000D* Onboard NIC    BBS(Network,Onboard NIC,0x0)..BO
rob@linux038:~$ 

```

Should 0007 be first?

---

### Post by oldfred on 2019-03-13
0000 uses shim, so that is correct.

I believe 0007 would be a fallback or hard drive boot entry. Typically new Windows systems have bootx64.efi be a copy of Windows .efi boot file. But Boot-Repair backs that up, and makes it a copy of shimx64.efi to also boot Ubuntu.

---

### Post by vysero on 2019-03-13
It sounds to me like I should be okay to restart my computer.

---

