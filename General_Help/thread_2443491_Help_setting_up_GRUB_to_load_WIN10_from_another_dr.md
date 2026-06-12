---
title: "Help setting up GRUB to load WIN10 from another drive"
date: 2020-05-16
forum: General Help
---

### Post by Slash0mega on 2020-05-16
I have a duel boot setup on solid state drive that is booting windows 7 and xubuntu just fine, but i feel its about time i updated my windows. 

not wanting to lose my perfectly functional windows 7 install, i just opted to place it on another drive. but now i need help figuring out how to get my grub menu to show windows 10 along with the rest

I put a empty 10gig partition at the start of the drive in case i needed to make a boot partition cause it looked like i need one from what googling i did do. (but if i don't meh. ) other than that i left the rest of the drive unpartitioned and let the windows installer handle the rest. 

os probe can't find it, and grub-install or whatever that command was couldn't find a boot partition. 

if someone can help me that would be wonderful, i am willing to reinstall windows10 if i need to do something during setup.

---

### Post by oldfred on 2020-05-16
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Windows 7 usually was installed in BIOS/MBR, but could be installed in UEFI/gpt mode.
Microsoft has required vendors to install Windows in UEFI/gpt since Windows 8 released in 2012. But allowed BIOS installs as some large mfg. wanted similar configuration or had old systems.
Windows only installs in BIOS boot mode to MBR partitioned drives. And only in UEFI boot mode to gpt partitioned drives.

---

### Post by Slash0mega on 2020-05-17
I only got one pastebin link from the software. what do you mean by "do not post report?"

---

### Post by oldfred on 2020-05-17
Some try to copy the entire report which is huge, often cannot be copied in its entirety. 

You copy & paste the pastebin link so we can click on it and see the details of your install.

---

### Post by Slash0mega on 2020-05-17
ah, i understand now. 

[http://paste.ubuntu.com/p/qmV8tk5F3N/](http://paste.ubuntu.com/p/qmV8tk5F3N/)

don't know if this is helpful info, but i believe windows10 is installed to sdc

---

### Post by oldfred on 2020-05-17
You have an UEFI system.
You booted Boot-Repair in BIOS mode.
Do not run any auto-fix from Boot-Repair with multiple drives. You can use advanced mode only.

Windows only boots & installs in UEFI boot mode from gpt drives.
Windows only boots & installs in BIOS boot mode from MBR (msdos) drives.
You have 4 MBR drives & 2 gpt drives.
Windows is installed in UEFI boot mode on sdc a gpt drive.

You have Windows BIOS boot loaders in sda & sdc & sde, and looks like sdd is another Windows in BIOS boot mode, but has grub in MBR of sdd. 

You should have Windows BIOS boot loader in the MBR of sdd, even though it looks like you have Ubuntu 18.04 installed in sdd also. You can have grub in any other MBR drive set to boot the BIOS install in sdd3 and keep Windows boot loader in MBR of sdd. Windows 10 often turns fast start up back on, and then you have to boot it directly. Grub will not boot the Windows in UEFI boot mode. UEFI & BIOS are not compatible.

Your UEFI Windows should directly boot from UEFI boot menu.
If you have Windows boot loader in sdd, you can boot Windows in sdd from that drive.
Then with grub in any other MBR drive you can boot the Ubuntu install. It should offer to also boot the BIOS version of Windows.

Long term, I would convert all drives to gpt and all installs to UEFI since new UEFI hardware. BIOS/MBR goes all the way back to DOS, and original IBM PC in mid 1980's. 
Microsoft has required vendors to install Windows in UEFI/gpt mode since Windows 8 released in 2012.

You can use Boot-Repairs Advanced Mode to select Ubuntu install and any MBR drive. It will give an error if you try to install a BIOS version of grub to gpt drive without a bios_grub partition.
Boot-Repair can also install a Windows type boot loader, syslinux to MBR of sdd. But often better to use your Windows repair flash drive to install the Windows boot loader to MBR of sdd with fixMBR command.

If you want to keep BIOS/MBR, better to have Windows on one drive and Ubuntu on another since you have several drives. But only can mix BIOS & UEFI on separate drives & then have to boot from UEFI boot menu if not in same boot mode. Those in same boot mode as grub can be booted from grub, if no other issue. Grub only boots working Windows.

---

### Post by Slash0mega on 2020-05-20
This probably wont work cause i don't think i got space at the start of the drive for a boot partition, but other than that would it be possible to change a drive from bios to uefi? or perhapse i can clone the intact windows 7 to another drive then clone it back after getting everything settled. (i am willing to distroy/reinstall xubuntu due to the home directory not being on the same drive)

otherwise, i think i might try changing my bios settings to get windows to install in bios mode. 
Next time i do anything with os's i am going to try using uefi from the start.

---

### Post by oldfred on 2020-05-20
I do not think it is easy to convert a BIOS Windows to UEFI since you also have to convert from MBR to gpt.
Standard conversion erases drive. But there are tools to convert without data loss, but  backups still required as sometimes things do go awry. And Windows wants lots of additional partitions with UEFI/gpt, see link below.

Windows 7 was able to install in UEFI boot mode, but original installer had to have files moved around. Updated installer worked if booted from USB in UEFI mode.

Settings in UEFI are for installed system. Booting installer depends on the boot options in UEFI one time boot menu for flash drive, UEFI or BIOS. And that only works if flash drive correctly configured. You cannot clone a MBR partition to gpt, structures are too different.

While ESP is usually first or second partition on a drive, it just has to be within the first 2TiB of a drive.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by C.S.Cameron on 2020-05-21
I have Win 10 UEFI on one hard drive and Ubuntu 18,04 BIOS on another.
I have not been able to get Ubuntu's grub to Boot Windows as it did with Win 7.
Only thing to do is press F12 every boot and choose the drive to use.

---

### Post by oldfred on 2020-05-21
UEFI and BIOS are not compatible.
Once you start booting in one mode from UEFI boot menu, you cannot switch. Or grub can only boot other installs in same boot mode.
Your BIOS install of Ubuntu could then boot a BIOS install of Windows, but not an UEFI install.
If you install Ubuntu on a gpt partitioned drive, you can convert from UEFI to BIOS (or vice-versa), just by installing the correct version of grub. There is grub-pc for BIOS boot and grub-efi-amd64 for UEFI boot on 64 bit PCs.

---

