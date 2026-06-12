---
title: "Dual Boot Problem With Kubuntu/Win8 (Bootloader)"
date: 2014-08-16
forum: General Help
---

### Post by danhavoc on 2014-08-16
While I doubt I';m the first to encounter something like this, I was unable to find a thread on it. I apologize if it's obviosly *right there* and I'm too dim to see it.

I installed Kubuntu next to Windows 8.1 by shrinking the partition in WIndows and manually setting partitions in the Kubuntu installer. If I boot into Kubuntu, it works- I'm in it now, enjoying far superior WiFi performance on this HP Envy than I get with WIndows. The problem is getting to it. When I boot the computer, it goes straight to Windows, and the only way I've found to reach Kubuntu is this convoluted nonsense:
1) insert a USB stick with Rescatux ISO burned to it via ISOtoUSB
2) try to boot the USB 
3) get an error saying no operating system was found and to press enter to continue
4) see Grub (!) and select Ubuntu (advanced options for Ubuntu and Windows 8 are also present)
5) successfully boot into Kubuntu.


my partitons look like this
1) \
     > the weird things Windows now makes with uefi (ntfs, hidden then fat32, boot)
2) /
3)  unknown 128mb flagges msftres
4)my NTFS Windows partition
5) the 1mb bios partition the Kubuntu installer had me create (I got an error and it said I had to make it)
6)my SWAP partition
7) the ext4 partition with Kubuntu
8) a shared NTFS partition filling the rest of the disk

My first thought is to try to make 5 bootable via GParted, but I'm afraid that'll be wrong and I'll lose the ability to boot into anything at all

Last time I tried linux/dual boot was Ubuntu/XP- and it was far, far simpler. Unfortunately, I seem to be stuck with eufi, since the restore media for this laptop seems to destroy the HDD and start from scratch, and the retail disk won't take the built-in certificate to let me install it like I used to with XP, setting partitions and such.

I would like to ditch Win8 for all but the few programs that require it, but need a reliable way to access Kubuntu without going through this mess to make that feasible.

secure boot is disabled in BIOS

---

### Post by oldfred on 2014-08-16
If you have a bios_grub partition then you installed in BIOS/Legacy/CSM mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

UEFI & BIOS are not compatible, so the only way to switch is to go back to UEFI and boot from that. Or you may be able to boot directly using one time boot key. I think with HP it may be f10, but on my system (not HP) it is f12.

You can convert a BIOS install to UEFI install with Boot-Repair, so you can more easily dual boot from grub menu. But HP has made that difficult as they are one of the vendors who against UEFI standard modify UEFI to only boot Windows entry. We have many work arounds for that issue. All Boot-Repair really does is uninstall grub-pc(BIOS) and install grub-efi (UEFI boot). Not sure if it works correctly now with 14.04 as efi grub package has changed to grub-efi-amd64 as they are now developing a 32 bit version also.

Do not move any boot flag. With UEFI/gpt it must be on the FAT32 partition that is the efi partition. And grub has never used boot flag, that was primarily Windows but some older boot loaders like Lilo use boot flag also with BIOS and MBR partitioning. With gpt the boot flag is not like the boot flag on MBR with BIOS boot. 

Best to make a full image backup of Windows and the efi partition.
      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And you may need a Windows repairCD or flash drive. Small flash drive is all that is required.
      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

If you convert Kubuntu to UEFI boot, you will need one of these alternatives:
       
 [http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files efi boot files in efi partition

 **a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
**a2:**(this is the same as what Boot-Repair does in B:. Windows updates will cause issues and require redoing.
Rename /efi/Microsoft/Boot/bootmgfw.efi and copy grub or shim into /efi/Microsoft/Boot and name it bootmfgw.efi  Then boot Windows entry to boot to grub menu. You have to manually add a grub menu entry to boot renamed Windows efi file. Grub2's os-prober entry boots bootmfgw.efi entry which is now just grub, so it will not work.

    Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
**d2**:  Disable Windows in UEFI and only boot from rEFInd or grub. If Windows is #1
sudo efibootmgr -A -b 0001

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Some other HP
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

