---
title: "Ubuntu installer doesn't see external SSD connected via USB"
date: 2021-02-16
forum: General Help
---

### Post by avanguardia on 2021-02-16
Hi everyone,

I'm super new here and I'm also new to Ubuntu, which I need in order to use OpenFOAM for university reasons. I'm having some trouble installing it (20.04.2) on an external SSD connected via USB to my computer. The problem is that my ssd doesn't appear among the possible options where to install ubuntu, and only my main internal SSD appears, where I don't want it to be. I have Windows 10 on my main SSD and I have formatted the external SSD with a primary partition of NTFS type. My laptop BIOS is of UEFI type and I have no idea if this has anything to do with the problem. I don't know which other details i need to give you to get a prespective so I will wait for any kind answer :D

Thanks in advance

p.s I think I should have put in in the installing section but I don't see how I can delete this post...

---

### Post by Impavidus on 2021-02-16
Can you see the external ssd from within the Ubuntu live session? Can you see it in uefi?

You should be able to install Ubuntu on the external ssd. The bootloder will be put in the first (internal) drive anyway, in the efi partition already used by Windows. You probably want that in the external ssd too, so you may have to disable the internal ssd in uefi or physically disconnect it (if possible on your computer).

There's no need to format the ssd first. The installer can do so and Ubuntu cannot be installed on an ntfs partition anyway. If you use manual partitioning (often recommended when there are multiple drives in your computer), it's convenient to use the gparted tool for that. It's included in the live system.

---

### Post by dragonfly41 on 2021-02-16
[COLOR=#000000]> I have Windows 10 on my main SSD and I have formatted the external SSD with a primary partition of NTFS type.[/COLOR]

[COLOR=#000000]This is your first misunderstanding coming from Windows land.[/COLOR]
[COLOR=#000000]Ubuntu requires ext4 not NTFS.[/COLOR]

[COLOR=#000000]Within Windows territory there is a package Rufus which can create a LiveUSB which in turn installs Ubuntu on your external USB.[/COLOR]

[COLOR=#000000]I have gone through the same stages, starting with Windows10. But rather than sharing the internal SSD my preference is to install Ubuntu on one or more external SSD's. I have two SSD's in an external docking bay with separate power.[/COLOR]

[COLOR=#000000]If your external SSD supports USB3.0 and your host has USB3.0 that is preferred for performance.[/COLOR]

[COLOR=#000000]There is a galaxy of posts in this forum about dual booting. You will need two USB flash drives:[/COLOR]
[COLOR=#000000]One for holding Windows recovery data (not necessary, but advised)[/COLOR]
[COLOR=#000000]Another for your Ubuntu LiveUSB.[/COLOR]

[COLOR=#000000]Once Rufus has created a LiveUSB you can launch this and "Try Ubuntu" (before Install Ubuntu which comes later).[/COLOR]
[COLOR=#000000]Then in "Try Ubuntu" mode on your laptop you will need to install Gparted (from memory it is not installed by default, but possibly my memory fails me). Then I advise using Gparted to prepartition your external SSD.[/COLOR]

[COLOR=#000000]If you get stuck I can offer a screenshot of the Gparted view on /dev/sdc (I have Windows on /dev/sda, another copy of Ubuntu on /dev/sdb and my current Ubuntu running on /dev/sdc). Although Windows does have a partition for boot, I prefer to add my own fat32 EFI (with boot flags) to each external SSD.[/COLOR]

---

### Post by avanguardia on 2021-02-16
Thanks to both of you for the answer, I understand some of the steps and I am doing mostly what dragonfly said. However, once I am in Ubuntu Live, I can't see my external SSD among the memory devices, only my internal one, called dev nvme01. Thus, I can't partition  my external one using gparted because I don't see it in the first place. (Maybe I'm missing/not understanding something really silly)

---

### Post by CelticWarrior on 2021-02-16
Gparted has a dropdown menu for different devices.
Disks shows all drives in the left panel.

---

### Post by mIk3_08 on 2021-02-16
> **avanguardia said:**
> installing it (20.04.2) on an external SSD connected via USB to my computer...
Have you already created it as a gpt disk on your external drive?

---

### Post by dragonfly41 on 2021-02-16
Perhaps an obvious point .. but have you tried connecting SSD through a different USB port?
And does your USB port recognise other devices?
Could be port/cable.

---

### Post by avanguardia on 2021-02-16
Yes, if i understand the question correctly. I have created a single partition on my external ssd as GPT disk with NTFS format; then, as some of you mentioned that NTFS can't be used for ubuntu, I've also tried removing that space so I was left with an unallocated space on a GPT disk, but either way Ubuntu doesn't recognize it. Also to reply to dragonfly, I have tried with both of the available usb ports and it doesn't work, the ssd is fully visible in windows so i doubt that's the problem.

---

### Post by mIk3_08 on 2021-02-16
> **avanguardia said:**
>  I have tried with both of the available usb ports and it doesn't work, the ssd is fully visible in windows so i doubt that's the problem. Have you tried using the sata ports? Just try using the SATA maybe it will work. What specific usb do you have, usb 2 port or usb 3?

---

### Post by CelticWarrior on 2021-02-16
How exactly have you concluded that "Ubuntu doesn't recognize it"?
Again, in GParted you must use the dropdown menu to see other drives. Or you can open Disks instead and all drives should show up in the left panel.
There are also different commands to gather a more in depth information about the whole system:
```
[FONT=Consolas]sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL[/FONT]
```
Or
```
[FONT=Consolas]sudo fdisk -l[/FONT]
```
Both in terminal, obviously.

And I must insist in what was commented a few times here: Please refrain from doing partitioning and formatting in Windows for a drive that is intended for installing Ubuntu. Creating a NTFS partition and then removing it is a (twice) waste of time. Anything related to partition table, partitions and formatting can and should be done in the Ubuntu live session and most if not all can be done within the Ubuntu installer itself.

---

### Post by dinkidonk on 2021-02-16
Not that it would cause the drive to be unavailable, but beware that some cheap SATA=>USB3 adapters / enclosures work very poorly with Linux since UASP support is broken and TRIM is not available. I would not recommend you to install Linux on a SSD connected with USB unless you are sure that UASP abd TRIM is working with the adapter.

---

### Post by oldfred on 2021-02-16
Many (even new) SSD need firmware update to work. Have you checked if firmware is newest available?

I always suggest partitioning in advance with any second drive.
The Ubuntu installer will not add an ESP- efi system to a second drive & external drives really need an ESP, if you even want to boot from any other system or boot on its own. Ubiquity installer always installs boot files with UEFI into the first or internal drive.

Reboot with external drive unplugged.
If issues, plug in device and see if shown or error in syslog, contol+c to exit tail listing
lsusb
tail -f /var/log/syslog

---

### Post by avanguardia on 2021-02-16
To celtic warrior : I have run it (sudo fdisk -l and also the other you mentioned) and only my main SSD is shown, there is no trace of my external ssd connected via usb. I figure it should be called dev sdb or something similar but there's not trace of it, only my main ssd dev nvme with all its partitions. Also thanks for explaining that I shouldn't bother partitioning; it takes a minute so at least I didn't waste too much time. The weird thing about this is that windows can see it and Ubuntu apparently not. 

To mlk:  my laptop only has 1 ssd slot so unfortunately I cannot add the external one that way, otherwise I would have done it

To dinkidonk and oldfred: Thanks for pointing out that it could be dangerous, I'll look into it,  for now I've given up and just created an ubuntu partition on my main ssd. I am sure that the externally connected SSD itself is working with the usb adapter (enclosure) because yesterday before formatting it,  I've tested if I could boot my old windows operating system from it ( it was my old SSD)  and it worked fine. I am not sure this also answers the firmware issues question, I am very new to Ubuntu.

Thanks for all the answers anyway! wasn't expecting this much quality support

Since I don't know if this is gonna be solved shortly and I've kind of given up , should i put the solved flag? Or maybe just delete the thread?

---

### Post by CelticWarrior on 2021-02-16
So... A couple of things to try:
- With the drive connected in Windows [disable the Windows Fast Startup]("https://www.windowscentral.com/how-disable-windows-10-fast-startup") feature. The link explains why it should be disable in any circumstance. I must add it's a MUST for dual-booting.
- If still unrecognized in the Ubuntu live session then please do as recommended above and boot again a live session without the external drive, i.e.,
> [COLOR=#000000]Reboot with external drive unplugged.[/COLOR]
[COLOR=#000000]If issues, plug in device and see if shown or error in syslog, contol+c to exit tail listing[/COLOR]
```
[COLOR=#000000]lsusb[/COLOR]
```
```
[COLOR=#000000]tail -f /var/log/syslog[/COLOR]
```
Please post the entire resulting messages.

---

### Post by avanguardia on 2021-02-16
I've tried the steps you mentioned to give you the log , I started the boot with the ssd disconnected then I used your code and I connected it and disconnected and then connected it back again; this is the log from after i disconnected and reconnected, I can see there are some errors but surely you know a lot more about this (sorry for the poor image quality) [https://ibb.co/Ss00mKX](https://ibb.co/Ss00mKX)

---

### Post by CelticWarrior on 2021-02-16
There's a bug reported for the device ([COLOR=#333333][FONT=monospace]1de1:1101)[/FONT][/COLOR] -> [https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch-data/+bug/1878921](https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch-data/+bug/1878921)
It's not clear if already remedied in 20.10.
There's a solution for using it as external media in Ubuntu 20.04 according to comments but definitely NOT recommended for installing Ubuntu. I'm afraid this is the end of the road.

---

### Post by oldfred on 2021-02-16
Is your SSD a new NVMe drive in an external NVMe to USB adapter?

I decided not to do that as speed advantage of NVMe thru USB3 is not seen and extra cost not worth it for external drive. 
I do have an external SSD that was my old internal SSD & it just works.

---

### Post by avanguardia on 2021-02-16
I see, thanks a lot for the help, this is much more in detail than I could have gone by myself, so thanks everyone for the replies!

---

### Post by CelticWarrior on 2021-02-16
Try Ubuntu 20.10, just in case.

You're welcome.

---

