---
title: "Stuck On Ubuntu"
date: 2019-10-04
forum: General Help
---

### Post by marios3132 on 2019-10-04
Hi,

I just installed Ubuntu 18.04.3 LTS.I used UUI on a clean usb drive to burn my .iso and all went well installing it.I did make a partition on my SSD which also included my windows 10.Now I'm stuck at Ubuntu ,can't switch to Windows 10 from my bios(msi z77a-g45 with an intel 2700k) .I really need to get back on windows and i can't figure out how to dual boot.

Please I need some help!
[h=2][/h][h=2][/h]

---

### Post by Impavidus on 2019-10-04
Boot using your live disk and try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Create a boot info summary and show us the link. That should tell us what's going on.

You may need a Windows repair disk. Have you got one? Dual booting Ubuntu and Windows is no longer as simple as it was in the WinXP days.

---

### Post by marios3132 on 2019-10-04
This is all going so bad.I've downloaded the iso and for some reason i can't burn it with UUI or with rufus.Can i skip the live usb thing?Because on the page says: ''
The easiest way to use Boot-Repair is to create a disk containing the tool (eg [Boot-Repair-Disk]("http://sourceforge.net/p/boot-repair-cd/home"), a disk starting Boot-Repair automatically), and boot on it. 
Remark : it is recommended to install the ISO on a [live-USB]("https://help.ubuntu.com/community/Installation/FromUSBStick") (eg via [UnetBootin]("http://unetbootin.sourceforge.net/") or [LiliUSB]("http://www.linuxliveusb.com/") or [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"))."

---

### Post by oldfred on 2019-10-04
Better to use Ubuntu live installer & just add Boot-Repair to it.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

      [/URL]sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt update
sudo apt install -y boot-repair && boot-repair 
    [URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

### Post by marios3132 on 2019-10-05
I eventually did the boot repair and here's the link it produced : [http://paste.ubuntu.com/p/dn7bV6ncFC/](http://paste.ubuntu.com/p/dn7bV6ncFC/)

Thanks in advance

---

### Post by yancek on 2019-10-05
Line 1232 of your boot repair shows the following:

> The boot of your PC is in EFI mode, but no EFI partition was detected 

3 of your drives are Legacy (dos) including the drive with Ubuntu (sda) and the windows drives (sdb and sdc) so you need to change the boot in the BIOS from UEFI to enable Legacy/CSM.  You could also install Ubuntu UEFI by creating an EFI partition but I believe that would entail installing windows again UEFI.  Surprised to see a windows 10 that is not UEFI/GPT?  Also, for some reason the windows boot files are not shown by boot repair on their drives.  Enable Legacy boot in the BIOS and see if that works.

---

### Post by oldfred on 2019-10-05
I do not know if Boot-Repair handles configurations with separate /var partitions. It does recognize and mount a separate /boot partition. Also not sure if mount of /var required for reinstall of grub. Both /boot & / must be mounted.

Generally for desktops better to just have few partitions as then you have to manage each partition's size separately. Default install is just / (root) or with UEFI also an ESP. With only one larger / partition available space is shared. That said, many also suggest a separate /home partition or data partition(s).

Not sure how you created sdd drive. Inside unknown MBR, is message saying it can be only booted in UEFI mode. See message starting at lines 600. It says you need different settings in Rufus.

Since you booted in UEFI mode, you must have a more recent PC. Windows has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012. But many users (corporations with many computers) wanted old BIOS/MBR for consistent configuration with older systems, so users can install in the now 35 year old BIOS configuration.

How you boot install media, UEFI or BIOS is then how it installs (and repairs). 
And Windows only installs to MBR drives with BIOS and only to gpt drives with UEFI. If install & drive partitioning do not match, Windows erases drive and converts to correct partitioning. So always have good backups.

You do not show Windows on SSD drive? If it was installed, you erased it when you partitioned for Ubuntu. Was it UEFI/gpt before & you converted to MBR, erasing all gpt data? If so, STOP using system. You can only totally recover by reinstalling & restoring your data. But if you have some data you have not backed up, there are tools that can scan a drive to look for erased files. Any data overwritten is gone.

---

### Post by marios3132 on 2019-10-05
@yancek thanks for your time.
I'm sorry I'm really inexperienced and confused right now.My bios only has to options UEFI and LEGACY+UEFI which I am using.

---

### Post by oldfred on 2019-10-05
Have not used BIOS/MBR for years.

But it looks like Rufus has settings to make USB flash installer either BIOS or UEFI.

Generally the ISO can be booted in either UEFI or BIOS boot mode from UEFI boot menu. You should have two entries, one UEFI:flash & one flash which then is the BIOS boot option. But if Rufus does not include the BIOS boot files when creating flash drive, you only have UEFI boot option.

---

### Post by marios3132 on 2019-10-06
@oldfred which ISO are you referring to?At this point i want to just return on Windows.I used the Windows ISO,burned on my usb to go through the installation,but the system wouldn't let me to.When i chose the Install Windows and keep files,settings and applications  i was introduced with the following problem:

 "The upgrade option isn't available if you start your computer using Windows installation media. 
If a copy of Windows is already installed on this computer and you want to upgrade,remove the installation media and restart your computer.After Windows has started normally,insert the installation media and run Windows Setup."

I'm just lost at this point and can't go back on Windows,which i really need for my univercity.My guess,when i did a mistake with partitions on the sdd,which included both OSs and clicked restore,it erased all data on it and now it's confused with some remaining directories on my other drives(like system32).
My last trump card would be to use a sata to usb adapter and get access on the ssd from another computer.From there i would get a better idea of what's in it and what's not.

---

### Post by oldfred on 2019-10-06
According to Boot-Repair report sda is SSD and it only has Linux partitions in BIOS boot mode.

Was Windows UEFI or BIOS boot?
And Windows will not install to SSD with Linux partitions. 
Windows in BIOS boot mode needs unallocated space and unused primary partitions. Or it normally in BIOS mode uses sda1 as a smaller boot partition and sda2 as main or c: drive.

If you partition in advance you can use one primary NTFS partition with boot flag formatted as NTFS. But some have reported that NTFS format from Linux will not work, you have to reformat it as part of install or before install from Windows. Windows will not boot directly from logical partitions.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

