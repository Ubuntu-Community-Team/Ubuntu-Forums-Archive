---
title: "msdos or GPT"
date: 2012-12-17
forum: General Help
---

### Post by geohei on 2012-12-17
Hi.

I plan to install Windows7 together with Ubuntu 12.04 on a brand new 64 bit GPT capable hardware.

Two questions:

1.
Is is preferential to use the msdos partition table system (primary and extended partitions) or the GPT partition system? ... and why (pros and cons)?

2.
Shall I use the Windows7 boot selector or GRUB? ... and why (pros and cons)?

Thanks,

---

### Post by oldfred on 2012-12-17
I prefer grub and most users now seem to find it works with Windows. In the beginning there were some issues with flexnet and other DRM software in Windows overwriting grub. But grub created work arounds.

I prefer gpt, but Windows will only boot from gpt if you install in UEFI mode. I use gpt on two Ubuntu only drives and have an old XP install in a MBR(msdos) drive. They worked together since 10.10, but now I am not booting XP as the SSD needed AHCI and that driver really is easier to install when installing XP.

If your system is UEFI you have to install both Windows & Ubuntu in UEFI mode. Or if not using UEFI then Windows has to have MBR partitioning.

If totally installing yourself, then the partition issues of 4 primary partitions with MBR can easily be worked around. With gpt all partitions are the same but you only can have 128 partitions. :)

If using UEFI then both systems have boot loaders in the efi partition. It then is like having both boot loaders in the MBR which of course is not possible with BIOS/MBR booting.

       Windows will only boot from gpt partitioned drives with UEFI.
Windows x64 Installer determines which firmware has been used for booting the ISO/DVD/USB. If BIOS is used, only MBR is supported. If UEFI is used then only GPT is supported. Not vice-versa.

    
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by geohei on 2012-12-19
Thanks a lot for the very valuble information! After I read your posting, I opted to give GPT a try.

My motherboard (64bit, UEFI):
GA-Z77X-UD5H
Firmware: F14 (latest)

First I installed Windows7 by booting in UEFI mode. I got 3 partitions I got this [GParted]:

```

/dev/sda1 fat32      /boot/efi 100.00 MiB boot
/dev/sda2 unknown              128.00 MiB msfres
/dev/sda3 ntfs                 97.43 GiB
unallocated

```

Then I installed Ubuntu from the install CD (using "Install Ubuntu" directly without starting Ubuntu Live first) [GParted]:

```

/dev/sda1 fat32      /boot/efi 100.00 MiB boot
/dev/sda2 unknown              128.00 MiB mfsres
/dev/sda3 ntfs                 97.43 GiB
/dev/sda4 ext4       /         46.57 GiB
/dev/sda5 linux-swap           14.90 GiB
unallocated

```

Now ... when I reboot the system, I have several (relevant) options to start:
1. UEFI: WDC WD1000FYPS01ZKB1
2. P2: WDC WD1000FYPS01ZKB1
3. Windows Boot Manager
4. ubuntu

Explanations:
1. Ubuntu starts directly, without showing the GRUB selection interface.
2. "Reboot and Select proper Boot device" ... aovious since HDD is booted using BIOS. No MBR, hence the error.
3. Windows7 starts directly.
4. Ubuntu starts directly, without showing the GRUB selection interface.

Questions:
I never see any GRUB screen! What went wrong?
I also don't see the Windows7 boot selection screen, which might show to select Windows7 or Ubuntu.

How come?

---

### Post by oldfred on 2012-12-19
I am surprised you do not get grub menu. That means its os-prober did not find Windows.

But the os-prober has a bug where it does not correctly find Windows in UEFI installs anyway. You can use Boot-Repair to add the correct chain load entry or manually add an entry to 40_custom.

Then you should be able to set default to ubuntu from UEFI menu and then from grub menu chain back to Windows without going into UEFI menu everytime.

Unless it does not work you do not need to post BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

    
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
this style entry will work as the chain load has to be to the efi partition not the Windows install on sdXY.
'Windows ...) (on /dev/sdXY)'


You can add this to 40_custom. Boot repair normally adds a similar entry to 25_custom so it is first in menu.
       
```
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

     
    

```

---

### Post by sgage on 2012-12-19
I have an old-school BIOS (no UEFI or suchlike), and I have found that if you don't let Windows have the MBR, it will be unable to hibernate (suspend works fine). If that's not important to you, I'd just let Grub have the MBR.

---

### Post by geohei on 2012-12-20
No joy yet ...

To start off from the beginning ... no dual boot or W7 installed. A bare-metal HDD (no partitions). Just as easy as it can get ...!

I start the amd64 Ubuntu installation CD in UEFI mode.

I get:
"error: 'prefix' is not set."
(don't know if it means something but the CD continued to start)

Then I select "Install Ubuntu."

Later on during the installation process, I use "Erase disk and install Ubuntu".

After the installation is complete, I start, and grub doesn't show up!

The partitions look like this (GParted):

```

/dev/sda1 fat32      /boot/efi  95.37 MiB boot
/dev/sda2 ext4       /         915.53 GiB
/dev/sda3 linux-swap            15.89 GiB

```

Why is there no grub menu?

---

### Post by oldfred on 2012-12-20
If you only have Ubuntu installed you do not get grub menu as it only sees one system and know that you will boot that. Only if you want it for recovery, you might hold shift key down from BIOS/UEFI boot until menu appears. There were some issues with that working with UEFI, but I think they fixed that.

Did Windows boot when you had Windows installed?

Rather than default installs for either system, if you are going to reinstall with both. I would install Windows shrink its partition with its own mmc and reboot a could of times. Then install Ubuntu but create a separate NTFS data partition for shared data. And you may just want to make / (root) a lot smaller. I use 25GB for every / (I have many to test) and have two shared data partitions, one NTFS from when still using Windows and ext3 for Linux only data and all new data now.

---

### Post by geohei on 2012-12-24
I read a lot (!) the last few days about UEFI/GPT and dual boot of Windows 7 and Ubuntu 12.10 Desktop. I rarely had such difficulties to install OSs in dual boot.

After many test installs, I ended up having Windows 7 and Ubuntu 12.10 Desktop running, but I still have some questions in order to fully understand what I did.

What I did ...

Tests with last 3 firmwares on my motherboard (F8, F13, F14). I still have this problem with the remaining entry in the boot device selection menu of UEFI/BIOS.

[http://forum.giga-byte.co.uk/index.php/topic,11330.0.html](http://forum.giga-byte.co.uk/index.php/topic,11330.0.html)

Question 1:
Is it normal that the entry "ubuntu" remains after all storage devices are physically detached from the motherboard?

I installed Windows 7 using UEFI mode first. 3 partitions were created (100 MB fat32 for EFI, 128 MB msfres for MSR, 100 GB ntfs for Windows 7). All worked fine and the "Windows Boot Manager" became visible in the UEFU/BIOS boot device selection menu.

Next I installed Ubuntu 12.10 (tested also with 12.04 - no real change). I used 50 GB ext4 as / and 20 GB as swap. I selected /dev/sda1 (the efi/boot partition created by the Windows 7 installer) as partition for the EFI bootloader. The installation ran fine except that at the end, the Ubuntu 12.10 install left the system unresponsive after the CD/DVD was taken out of the drive. I had to hard reset in oder to reboot:

Question 2:
Is it normal that Ubuntu 12.10 doesn't reboot after pressing ENTER at the end of the installation process? Might this be already an indication that something went wrong?

Ubuntu 12.04 install rebooted properly, as expected.

But now ... the UEFI/BIOS boot device selection menu showed "ubuntu" and it booted properly, but no sign of grub. This left me with a system where I had to use the UEFU/BIOS boot device selection menu every time to change OS. I followed quite some tutorials and forum articles about what to do, but for me the install never ended up in a working grub installation.

Question 3:
Is it normal that Ubuntu 12.10/12.04 doesn't manage to create a working grub when installing both OS on a GPT HDD? In other words ... are there users who managed to achieve this, or is it always required to use post installation tools to make grub work?

Question 4:
Is it possible that there is a misused UEFI/BIOS setting which is responsible that Ubuntu doesn't install and configure properly? If yes, where should I look for? See above for details about my motherboard and firmware.

Question 5:
Is it possible that my UEFI/BIOS contains a bug so that Ubuntu doesn't recognize the Windows 7 installation?

I used Boot-Repair ... and it worked. grub started when I used "Windows Boot Manager" or "ubuntu". Both selections end up in the grub menu.

[http://paste.ubuntu.com/1461544/](http://paste.ubuntu.com/1461544/)

Question 6:
Is there a hint in the Boot-Repair log above pointing to a possible problem? I'd really like to understand what was wrong before the boot repair and what Boot-Repair did.

Question 7:
Is it normal/useful that grub leaves the 2 entries ("Windows Boot Manager" and "ubuntu") in the UEFI/BIOS boot device selection menu? One would be sufficient since they both end up at the same point - the grub menu.

Please tell me if you need more details about my system ...

Thanks,

---

### Post by oldfred on 2012-12-24
UEFI & grub (and Windows) are separate. UEFI/BIOS is on motherboard and starts boot process. Then grub or Windows boot loaders are loaded and continue boot process. Grub can chain load back to the efi Windows entry so you can just use ubuntu default in UEFI. But grub cannot change entries in UEFI (and should not).

I thought UEFI read entries in efi partition to know what to boot, but it must save those entries in EEPROM on mother board. You should then have maintenance menu somewhere to edit those entries.


Grub has a bug and it is reported on not correctly finding efi Windows. The more that post that the bug applies to them the sooner it may get fixed. You do have to create a sign-on for launchpad.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
'Windows ...) (on /dev/sdXY)'


You may have UEFI shell already installed or can install one for detailed command line editing of UEFI info.
       
 [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)

---

### Post by YannBuntu on 2012-12-24
Hi
I haven't read everything, but i can answer for this:
> **geohei said:**
> I used Boot-Repair ... and it worked. grub started when I used "Windows Boot Manager" or "ubuntu". Both selections end up in the grub menu.

[http://paste.ubuntu.com/1461544/](http://paste.ubuntu.com/1461544/)

Question 6:
Is there a hint in the Boot-Repair log above pointing to a possible problem? I'd really like to understand what was wrong before the boot repair and what Boot-Repair did.

Question 7:
Is it normal/useful that grub leaves the 2 entries ("Windows Boot Manager" and "ubuntu") in the UEFI/BIOS boot device selection menu? One would be sufficient since they both end up at the same point - the grub menu.

Q6: B-R reinstalled grub-efi, added a custom "Windows UEFI loader" entry, and renamed the original Windows entry to *.bkp
I guess the original problem was that GRUB created a Legacy entry to Windows (when you needed an UEFI entry).

Q7: yes, it's normal that you have both a "Windows" and a "Ubuntu" entry in your BIOS. The "Windows entry currently boots GRUB because B-R replaced the original Windows efi file by a GRUB efi file. You can make the "Windows" entry boot directly Windows by running Boot-Repair --> Advanced options --> untick "Backup and rename EFI files" --> tick "Restore EFI backups" --> Apply. (this will rename the Windows efi files to their original names).

---

### Post by geohei on 2012-12-25
Thanks for the replies!

Now ... did I do something wrong during the described Windows 7 / Ubuntu 12.10 installation to end up with a broken grub configuration, or is this all "normal" (taking into account the mentioned grub bug)?

> **oldfred said:**
> UEFI & grub (and Windows) are separate. UEFI/BIOS is on motherboard and starts boot process. Then grub or Windows boot loaders are loaded and continue boot process. Grub can chain load back to the efi Windows entry so you can just use ubuntu default in UEFI. But grub cannot change entries in UEFI (and should not).
I'm not sure what you want to tell me (sorry) ... I understand what you say, but what was your message?

> **oldfred said:**
> I thought UEFI read entries in efi partition to know what to boot, but it must save those entries in EEPROM on mother board. You should then have maintenance menu somewhere to edit those entries.
Ack! There seems to be storage place in the UEFI/BIOS EEPROM, but I didn't find any selection to change these. Also, taking out the battery reset date/time, but the boot device "ubuntu" remained in the UEFI/BIOS boot device selection menu. Weird!

> **oldfred said:**
> Grub has a bug and it is reported on not correctly finding efi Windows. The more that post that the bug applies to them the sooner it may get fixed. You do have to create a sign-on for launchpad.

grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
'Windows ...) (on /dev/sdXY)'

Found this bug description:
> ...
Its menu shows 2 INVALID Windows entries. When selecting these entries, it displays "Invalid EFI file path" error, and returns to GRUB menu.
...
This is not really what I have since I don't see the grub boot menu at all.

> **oldfred said:**
> You may have UEFI shell already installed or can install one for detailed command line editing of UEFI info.
       
[https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)
Will read about the UEFI Shell.

> **YannBuntu said:**
> ...
Q7: yes, it's normal that you have both a "Windows" and a "Ubuntu" entry in your BIOS. The "Windows entry currently boots GRUB because B-R replaced the original Windows efi file by a GRUB efi file. You can make the "Windows" entry boot directly Windows by running Boot-Repair --> Advanced options --> untick "Backup and rename EFI files" --> tick "Restore EFI backups" --> Apply. (this will rename the Windows efi files to their original names).
That's what I did. When applying, Ubuntu crashed. Black screen and error messages. After hardware reset, "Windows Boot Manager" booted Windows 7, and "ubuntu" booted with this error:
```
error: ELF header smaller than expected.
grub rescue>"
```

---

### Post by YannBuntu on 2012-12-25
> **geohei said:**
> That's what I did. When applying, Ubuntu crashed.

Ouch, not good. Please:
1) boot onto an Ubuntu live disc, choose "Try Ubuntu", run Boot-Repair --> Advanced options --> click the "Backup .." button --> save the ZIP file somewhere --> attach this file to your reply, or send it to me by email (yannubuntu ATT gmail DOT com). This will help us understand what crashed, and the possible consequences.
2) then run Boot-Repair --> Recommended Repair , reboot the pc, and tell us if you can access Ubuntu.

---

### Post by geohei on 2012-12-26
1. Done!

2. No joy ... even the "ubuntu" Entry starts Windows 7. I investigated a bit. Unless I did something wrong, the above described (and requested by you) repair operation of Boot-Repair managed to delete the / and swap partitions of Ubuntu. This was confirmed by diskpart (Windows) and gparted (Ubuntu). But no worries ... I reinstall. I'm still in the test phase ;)

---

### Post by YannBuntu on 2012-12-26
Unfortunately, the ZIP doesn't give any clue about what happened.
I attach the log for future reference.

Currently no OS is detected by os-prober, neither Windows nor Ubuntu. Your filesystem seems damaged.

Please run Boot-Repair --> Advanced options --> tick "Repair filesystems" --> Apply , and indicate the new URL that will appear.

Then, if the Ubuntu partition is accessible, browse it, and send me a ZIP of your /var/log/boot-sav folder.

---

### Post by geohei on 2012-12-27
I'll do some more tests/attempts tomorrow ...

Meanwhile ... having a hard time to install Windows 7 and Ubuntu 12.10 as dual boot with UEFI and a single GPT disk, I gradually get the impression that not very many people are using this (or tried it) setup, which is a surprise though. There must be a howto out there describing the steps to follow ?! I have no fancy GPT/MBR mixted disks or even 2 disks. All GPT and all on one disk. That should be feasible ...!

BTW ... I did some tests with EasyBCD from Windows 7. This tool doesn't take the Ubuntu partition (i.e. bootloader).

Either the UEFI, GRUB2, EasyBCD tools aren't quite ready yet to cope with GPT disks, or might do some mistake during setup. Also ... the UEFI settings of my machine could be the reason?!

---

### Post by oldfred on 2012-12-27
I know EasyBCD did not work with UEFI, but they were updating it. But with UEFI I see no reason for it. Also grub2 is designed to multi-boot.
       EasyBCD does not work with Windows 8
[http://neosmart.net/forums/showthread.php?t=11135](http://neosmart.net/forums/showthread.php?t=11135)

With hardware without Windows UEFI secure boot 12.04 will work with UEFI, but 12.10 has further updates and should work better for all UEFI installs.

I do not know about your specific hardware, but others that worked:
       UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

            UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)

---

### Post by geohei on 2012-12-27
> **oldfred said:**
> I know EasyBCD did not work with UEFI, but they were updating it. But with UEFI I see no reason for it. Also grub2 is designed to multi-boot.
       EasyBCD does not work with Windows 8
[http://neosmart.net/forums/showthread.php?t=11135](http://neosmart.net/forums/showthread.php?t=11135)
The last posting [#6] says that EasyBCD should work for Windows 7. So ... what am I doing wrong?

> **oldfred said:**
> With hardware without Windows UEFI secure boot 12.04 will work with UEFI, but 12.10 has further updates and should work better for all UEFI installs.

I do not know about your specific hardware, but others that worked:
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
This is all for an MBR disk. I use a GPT disk.
Besides this, you mention "Secure Boot". I didn't find any related selection in my UEFI/BIOS.
Is it possible that my brand new Gigabyte motherboard doesn't support "Secure Boot"?
Do I need "Secure Boot" to dual boot Windows 7 w/ Ubuntu 12.04/12.10?

> **oldfred said:**
> UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
All read ... had no clue it would be so complicated! I still don't get it why it must be so complicated.

---

### Post by oldfred on 2012-12-27
Secure boot is currently only on Windows 8 systems that are pre-installed from a vendor. That will always be UEFI and gpt partitioning.

With your own install you can install in either UEFI or BIOS mode. But both Windows & Ubuntu have to be in the same mode.

Most have reported that they can just install & it works. But it is how you boot your install media either UEFI or BIOS, is how it will install.

If you insist on EasyBCD then you have to install in BIOS mode and have the 4 primary partition issue. And grub is forced into a partition boot sector and may need replacing with a liveCD/DVD/Flash drive with any major grub update. 

Some of the links were to show users with Windows 7 & Ubuntu dual booting and in UEFI mode.

---

### Post by geohei on 2012-12-28
> **oldfred said:**
> Secure boot is currently only on Windows 8 systems that are pre-installed from a vendor. That will always be UEFI and gpt partitioning.

With your own install you can install in either UEFI or BIOS mode. But both Windows & Ubuntu have to be in the same mode.

Most have reported that they can just install & it works. But it is how you boot your install media either UEFI or BIOS, is how it will install.

If you insist on EasyBCD then you have to install in BIOS mode and have the 4 primary partition issue. And grub is forced into a partition boot sector and may need replacing with a liveCD/DVD/Flash drive with any major grub update. 

Some of the links were to show users with Windows 7 & Ubuntu dual booting and in UEFI mode.
Ok, so I forget about "Secure Boot". I don't have it and I don't need it for my purposes.

I always installed both OSs (Windows 7 and Ubuntu 12.04/12.10) in UEFI mode from CD/DVD.

What do you mean by: "Most have reported that they can just install & it works"? Is this related to dual boot Windows 7 / Ubuntu 12.04/12.10 on UEFI systems with GPT disks or just dual boot in general?

No, I don't insist on EasyBCD. I stay with GPT disks and forget EasyBCD so far. But reading about the tremendous problems users have to get grub configured properly isn't really motivating, but I guess my choice is reduced to 1 ... which is grub.

> **geohei said:**
> ...
Question 7:
Is it normal/useful that grub leaves the 2 entries ("Windows Boot Manager" and "ubuntu") in the UEFI/BIOS boot device selection menu? One would be sufficient since they both end up at the same point - the grub menu.
...
Regarding this, I noticed that both entries are in fact stored in the NVRAM of the motherboard. Reloading the same UEFI/BIOS firmware kills the entries, and the only entry remaining is "UEFI: WDC WD1000FYPS-01ZKB1"

So ... after Windows 7 and Ubuntu 12-04/12.10 gets installed, I have:
- Windows Boot Manager [boots Windows 7]
- ubuntu [boots Ubuntu]

After Boot-Repair with recommended options:
- Windows Boot Manager [starts grub]
- ubuntu [starts grub]

After UEFI/BIOS firmware update (= flashed same version as installed, deleting NVRAM stored UEFI boot device entries):
- UEFI: WDC WD1000FYPS-01ZKB1 [starts grub]

Now ... after starting Ubuntu for the first time:
- UEFI: WDC WD1000FYPS-01ZKB1 [starts grub]

Then ... after starting Windows 7 for the first time:
- UEFI: WDC WD1000FYPS-01ZKB1 [starts grub]
- Windows Boot Manager [starts grub]

I don't really know what to conclude out of this. Ubuntu seems to write an entry into NVRAM, which is only deleted when UEFI/BIOS is flashed. Also starting Ubuntu doesn't rewrite the entry. Windows 7 doesn't seem to do that. However Windows 7 doesn't show up in the UEFI/BIOS boot device selection menu after UEFI/BIOS flash. It needs to be started first at least once. This means that it writes something either to the HDD or NVRAM. The NVRAM is hard to believe because the entry is gone when the drive is disconnected. All very strange.

Q8.
Can I change the "Windows Boot Manager" entry into something user selectable like "grub2"?

After I ran Boot-Repair, I got the following grub selection menu:
- Ubuntu
- Advanced options for Ubuntu
- Windows UEFI loader
- Windows Boot UEFI bootx64.efi.bkp

Q9.
Can I get rid of an entry (like "Advanced options for Ubuntu")? If yes, how?

Q10.
This seems to be the old Windows entry - "Windows Boot UEFI bootx64.efi.bkp"
Why should it still be there?
Any reason?

Q11.
How can I change the order of the entries?

Q12.
How can I change the default OS to be booted?

Q13.
Is there any Ubuntu (GUI) tool which allows to change grub settings?

Q14.
Can I safely remove either partition / (Ubuntu) or C: (Windows) and the other OS still starts properly? This assumes I leave the EFI as well as the MSR partitions on the disk.

Thanks,

---

### Post by oldfred on 2012-12-28
Many have installed with UEFI and have it just work with dual boot. The only issue has been the bug that grub2's os-prober creates incorrect chainload entries and you have to manually update or use Boot-Repair.

Part of the issues Boot-Repair fixes with Windows 8 is the booting from Windows with grub. It backs up the Windows efi files and renames them. It then copies the grub file to  the Windows file, so you can easily boot grub on systems that only boot Windows which seem to be most with Windows 8.
       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)

If booting Windows 7 without the secure boot issues you could probably use the standard Windows efi files And the standard grub/ubuntu files and dual boot from the UEFI menu. 
The backup efi file is the Windows version of this file.
       /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Boot-Repair has a function to undo the file renaming.

I would backup the efi partition before doing anything.

If you want to uninstall either system, I would use Boot-Repair's sister application as it will make sure you can still boot the old system.
       
 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

If you delete the Ubuntu partition without resetting the efi entries, you would not be able to boot. Grub has to find its menu in the Ubuntu partition. So you have to directly boot the Windows efi entry from UEFI not from a grub menu. If you delete Windows then the grub menu entry for Windows would not work, but you could still boot Ubuntu.

Both Boot-Repair & the uninstaller are on the Secure Remix and it is best to have several repair DVD/flash drives with both Windows & Linux repair tools.

Many recommend as a gui way to edit grub menus, Grub Customizer. I prefer to do it manually, but many want a gui.
       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

            The Grub 2 Guide - drs305 also link to grub customizer
Ubuntu Community Documentation site
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by geohei on 2012-12-28
Thanks oldfred ... you fill my upcoming day again with reading ... :)

> **oldfred said:**
> ...
If you delete the Ubuntu partition without resetting the efi entries, you would not be able to boot. Grub has to find its menu in the Ubuntu partition. So you have to directly boot the Windows efi entry from UEFI not from a grub menu. If you delete Windows then the grub menu entry for Windows would not work, but you could still boot Ubuntu.
...
Getting more and more nasty ... ;(

I do need to boot Windows 7 also when Ubuntu isn't present anymore and vice versa.

Ok ... let's try something else.

Is it possible to install Windows 7 and Ubuntu on the same GTP disk (using UEFI mode of course), and to select the OS using the UEFI boot device selection menu?

This would mean I don't use grub to select which OS I'd like to take.

Is that possible?

I used to start my first attempts with dual boot like this, but I do need both OSs to be bootable without the other one requiring to be installed simultaneously.

Initially, I had 2 entries in the UEFI boot device selection menu. "Windows Boot Manager" and "ubuntu". But an UEFI/BIOS flash deletes the "ubuntu" entry (stored in the UEFI/BIOS flash), hence, Ubuntu becomes unbootable.

I wouldn't care to select boot device using UEFI/BIOS, but teh entries need to survive a BIOS flash.

---

### Post by oldfred on 2012-12-28
With my BIOS system I try to avoid flashing BIOS. It automatically resets everything back to defaults. Last time I did it keyboard & mouse quit working in grub and many other issues. Only then I remembered when first installed I had to turn on USB keyboard setting in BIOS. Now I used camera and made screen shots of my BIOS screens so I know all the changes I have made.

I would think UEFI should rediscover Ubuntu in the efi partition, but do not have UEFI to test. Let us know.

Some have reported that they do boot directly from UEFI menu. I think you should also have a one time boot key that gives you the same boot choices. It is f12 on my BIOS system, but varies by vendor.
I think then you do not use Boot-Repair to rename efi files. You need the separate grub/ubuntu and windows efi entries. If you have run Boot-Repair you can rename them back or backup after Windows install the entire efi partition, so you each version of efi files.

Even then, you still should be able to use grub to boot Windows, but have to add the correct chain load entry to 40_custom or 25_custom.

       [http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)

```

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}


```Where Boot-Repair renames/backsup Window's bootmgfw.efi and chains to the backup. It does to to get around UEFI/BIOS that only boot the Windows entry. (Which is a bug in the UEFI, not grub). You would have to test, but the issues are more with secure boot & Windows 8.
      
 From Boot-Repair typical entry where UUID on set root is UUID of efi partition on your system.
```

menuentry "Windows UEFI " {
search --fs-uuid --no-floppy --set=root 96D8-1AC2
chainloader (${root})/EFI/Microsoft/boot/bootmgfw.efi.bkp
}

    
```

---

### Post by geohei on 2012-12-30
Thanks again oldfred. I'll did myself through. Will take some time ... !!!

Meanwhile something else - during regular Ubuntu 12.10 Desktop installation, is there a difference to put the bootloader to /dev/sda1 (efi partition) or /dev/sda4 (/ partition) or /dev/sda (disk)? This question shows during installation when the partitions need to be defined/selected.

In all 3 cases, I see after install is complete: <EFI partition>/EFI/ubuntu/grubx64.efi (122880 Bytes).

Is this correct that all 3 selections end up writing the same file to the EFI partition?

Thanks,

---

### Post by oldfred on 2012-12-30
With a BIOS install grub2's boot loader really should be installed to a MBR, preferred the same drive. But it does give an option to install to a PBR or partition's boot sector. But if in a partition you have to have another boot loader from another system to chain to grub or to boot directly using kernel. 

With UEFI install it seems that the installer knows the only place to install the boot loader is the efi partition. Since all boot loaders are equal in efi partition there is no more argument like in BIOS over who controls MBR.

But some of the options or descriptions are not yet fully updated even if the underlying code is.

But the os-prober does not yet seem efi aware and only creates the old style chain load entries to partitions, not a chain load to the efi partition. I think I posted that bug report before.

---

### Post by geohei on 2013-01-08
> **geohei said:**
> ...
Question 1:
Is it normal that the entry "ubuntu" remains after all storage devices are physically detached from the motherboard?
...
Yes, it is.

Using efibootmgr, I found this:
```
root@xxx:/home/geohei# efibootmgr
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001,0006,0007
Boot0000* ubuntu
Boot0001* Windows Boot Manager
Boot0006* Hard Drive 
Boot0007* CD/DVD Drive
```

There are 2 entries from my installation in this list.

"ubuntu" - This one resides inside the NVRAM of UEFI. When I delete the HDD containing W7/Ubuntu completely (no partitions anymore), this entry still remains in the UEFI Boot Manager.

"Windows Boot manager" - This entry seems (?) to be read from the /boot/efi/EFI when the computer starts. When I delete the HDD, this entry is gone. Can you confirm this assumption? If yes, which file in /boot/efi/EFI is responsible for this UEFI Boot Manager entry?

Next ... I tried to change the name of "ubuntu" into "Ubuntu 12.10". This was more an exercise than anything else in order to get used to efibootmgr.

```
root@xxx:/home/geohei# efibootmgr -b 0000 -L "Ubuntu 12.10"
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001,0006,0007
Boot0000* ubuntu
Boot0001* Windows Boot Manager
Boot0006* Hard Drive 
Boot0007* CD/DVD Drive
```
Why is this not working?

Next ... what is the difference between efibootmgr and the EFI Shell, except that one is executed from Ubuntu and the other one on EFI level? When do I use the former one, when the latter?

> **oldfred said:**
> ... But grub cannot change entries in UEFI (and should not).

I thought UEFI read entries in efi partition to know what to boot, but it must save those entries in EEPROM on mother board. You should then have maintenance menu somewhere to edit those entries.
Well, either grub or Ubuntu installation uses efibootmgr mechanisms to write directly into UEFI.

There seem to be 2 ways the UEFI Boot Manager entries appear.
1. UEFI entries stored in NVRAM.
2. UEFI looks in EFI partition and finds bootloaders.

Thanks,

---

### Post by oldfred on 2013-01-08
I do not have UEFI and most have just had issues getting UEFI to work and have not gotten into the details.

       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

    
Someone did post this, but I do not know if every UEFI is similar or not. It seems some have UEFI shell built in and others do not.
> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

    

---

