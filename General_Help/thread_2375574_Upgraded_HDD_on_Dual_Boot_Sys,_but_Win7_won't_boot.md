---
title: "Upgraded HDD on Dual Boot Sys, but Win7 won't boot - Xubuntu does"
date: 2017-10-25
forum: General Help
---

### Post by Rick St. George on 2017-10-25
Upgraded my HDD from 250GB to 1TB HDD, and had a dual boot Laptop with Win7 & Xubuntu v16.04.

Partiioned 1TB HDD in 3 partitions for Win7; Xubuntu; and Storage.

Cloned the two partitions with CloneZilla to new drive and upon Reboot, Win7 would not boot but Xubuntu did.
Ran Grub2 Boot Repair Disk and no change. Restored MBR with previous BU via Acronis - no change!
Looked around the Net for similiar situation, found several but not specific to my situation.

Plugged HDDs into main system, looked at them side by side, I see on both HDDs Win7 is flagged Boot. Both partitions have a Key!
Tried to Run TestDisk, [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery), but it would not run in UbuntuStudio v16.04.

Does anyone have an idea how I can get Win7 to boot again while I'm looking at them in my main system running UbuntuStudio v16.04?

Thanks!
:confused:

---

### Post by oldfred on 2017-10-25
Boot-Repair is primarily for Linux, it cannot fix most Windows issues.
Have you used a Windows repair disk to run repairs on the NTFS install?
Did you resize the NTFS partition with Windows tools or with gparted. Best to only use Windows tools for Windows.

---

### Post by Rick St. George on 2017-10-25
Good to hear from you OldFred, read another post from you on this general issue. This thread "[https://ubuntuforums.org/showthread.php?t=2295421](https://ubuntuforums.org/showthread.php?t=2295421)" is 24 pages long and unresolved. I know we can resolve this.

> **oldfred said:**
> Boot-Repair is primarily for Linux, it cannot fix most Windows issues.
Have you used a Windows repair disk to run repairs on the NTFS install?
A: No, however, I just found one.

> Did you resize the NTFS partition with Windows tools or with gparted. Best to only use Windows tools for Windows.
A: I used Acronis for Seagate drives, and have a BU of the Win partion.

Thanks!

---

### Post by Rick St. George on 2017-10-25
Used the Win7 install disk to do a boot repair. When I got to the Regional settings, selected Location/Keyboard setting  then click next. On the next page, clicked on "Repair your computer." On the next page, if it found the Windows installation, made sure it is UNSELECTED before clicking next. Then clicked on "Command prompt". From there, typed in the following 2 commands: 
```

bootrec.exe /fixboot
bootrec.exe /fixmbr

```

Now Grub Menu does not show up, and all I see if flashing prompt in upper left corner.  NO BOOT at all. If I use Grub2 Boot Repair, I'll probably get back Grub Boot Loader but still not Win7.  Any ideas would ber very much appreciated. 

Thanks!

---

### Post by oldfred on 2017-10-25
Windows repairs typically do the fixMBR or put the Windows boot loader in the MBR if a BIOS/MBR configuration.
You just need to run Boot-Repair or even just two commands at terminal of Ubuntu live installer to mount and install grub.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
    
Often chkdsk(until no errors) and  bootrec commands and if any resize of NTFS partition, the bootsect commands are required.
 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/) 
   Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd 
   [http://superuser.com/questions/949219/how-to-fix-windows-10-boot-loader-from-windows/950042#950042](http://superuser.com/questions/949219/how-to-fix-windows-10-boot-loader-from-windows/950042#950042)
bootsect {/help|/nt60|/nt52} {SYS|ALL|<DriveLetter>:} [/force] [/mbr]
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by Rick St. George on 2017-10-25
Still didn't work. I even marked Partition 1 as Active. Perhaps I can clone the old drive, instead of partitions 1 & 2.  Then spread out the partitions to add more space in each partition. But can Win7 for example do that without destroying all data in the partitions?

---

### Post by oldfred on 2017-10-25
NTFS partitions have info in the partition boot sector or PBR that must match partition table.
That is where chkdsk and bootsect commands are required if any change is made to a NTFS partition.

The NTFS partition with the boot files must be the one that has boot flag or make active in Windows.

More just to confirm configuration.
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Rick St. George on 2017-10-25
After download to DVD, and Reboot, HDD light blinks like mad continously, and screen still shows "Press the ESC key for Startup Menu". 

I'm not getting anywhere. I think I'll try Cloning the previous HDD to this new HDD, and then re-Partition or ENLARGE partitions later. Is that possible?

---

### Post by oldfred on 2017-10-26
Yes, as long as you are still using same partitioning, or drives are MBR or both drives are gpt.
Windows only boots in UEFI boot mode from gpt partitioned drives and only in BIOS mode from MBR. So you cannot change partitioning type.

And only use gparted on Linux partitions, and use Windows tools on NTFS partitions.
Some of the third party Windows tools seem to recognize Linux partitions, where Windows does not, or does not correctly see them.

I typically suggest just reinstalling Ubuntu, easier than cloning. If you have good backups (which you always should)  or have your older drive, you can just reinstall, copy /home and perhaps some other data and in old drive export list of installed apps and reinstall that in new install. 
Also good experience in restoring system from backup if you have a drive failure.

---

### Post by Rick St. George on 2017-10-26
WOW, almost worked ... Cloned entire previous HDD to new HDD with Acronis for Seagate Drives, enlarging the partitions in the process.

Grub Menu appears, Win7 boots OK, but Xubuntu 16.04 boots to what looks like a command prompt Login! 
How do I get to the actual Login Screen?

---

### Post by oldfred on 2017-10-26
Partitions may have different UUIDs?
You may need to just reinstall grub to MBR, or a full reinstall of all of grub.

Many use Boot-Repair, if just reinstalling to MBR, it is just two lines, mount & install.
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Rick St. George on 2017-10-26
Not sure I understand, because - the Grub Boot Menu comes up. I can choose Win7 or Xubuntu. When choosing Xubuntu the Ubuntu Splash screen shows for a while (counting to 50+) then a command line login prompt.

Logged in and Tried this command;
```

systemctl set-default graphical.target

```

Screen came back with; "Failed to set default target: Read-only file system".

What does that mean? How come Read-only??  How do I get back the Login Screen???

Thanks!

---

### Post by oldfred on 2017-10-26
Have you tried recovery mode, second entry, probably under Advanced Options.

Do you have proprietary video? Nvidia or AMD?

Does system need fsck? Even if new install or copy.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Rick St. George on 2017-10-26
First thing I see upon Reboot; "a TPM 7 Error occured ... attempting to read a PBR value" disappeared before I could read the rest. But chose Ubuntu Options; then to boot "Ubuntu Upstart" whatever that is, and Xubuntu booted up. Ran an Update and Rebooted.

After Reboot, clicked on *Ubuntu (instead of Options) and got "Failed to Start Remount Root and File System" and back to prompt!
Saw "Starting Create Volatile Files and Directories" amung many other "Starting ...".

CTL-ALT-Delete; and chose Advanced Options / Upstart and got the regular Login Screen and boot up into Xubuntu Ok.
This does not seem normal, but it works!  Is something still wrong? Any final suggestions?

Thanks a million for hanging in there.

---

### Post by oldfred on 2017-10-26
Is this an UEFI system, but booting in BIOS mode.
TPM is a setting in UEFI. But defaults should just work.

 Microsoft has announced that from January 1, 2015 all computers will have to be equipped with a TPM 2.0 module in order to pass Windows 8.1 hardware certification.
[https://en.wikipedia.org/wiki/Trusted_Platform_Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) 
      
 Older computer without TPM
GRUB_CMDLINE_LINUX_DEFAULT="tpm_tis.force=1" 

Do not use control-alt-delete in Linux.
      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[URL="https://en.wikipedia.org/wiki/Magic_SysRq_key"]https://en.wikipedia.org/wiki/Magic_SysRq_key
[/URL]
 R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system 

Are you getting a fsck at reboot?

[URL="https://en.wikipedia.org/wiki/Magic_SysRq_key"]
[/URL]

---

### Post by Rick St. George on 2017-10-27
> **oldfred said:**
> Is this an UEFI system, but booting in BIOS mode.
TPM is a setting in UEFI. But defaults should just work.


It seems to be a UEFI due to the fact on Boot-up Screen shows F12 for Startup Menu (typical of UEFI sys) giving those options.
But don't know if booting in BIOS mode, surely it boots to BIOS then UEFI in order to see Startup Menu upon hitting F12.
And the question remains ... Defaults should work - Buy why is it not???

> 
Do not use control-alt-delete in Linux.
      Reboot System Even If Ultimately Broken ...LOL.
[URL="https://en.wikipedia.org/wiki/Magic_SysRq_key"]https://en.wikipedia.org/wiki/Magic_SysRq_key
[/URL]
 R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system 


Never heard of that one! Learn something new everyday! Good to know ... Thanks!!!

> 
Are you getting a fsck at reboot?


NO!

---

### Post by oldfred on 2017-10-27
UEFI systems first boot in UEFI mode, and if none found, will try BIOS/CSM/Legacy mode and then post failure message.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

But most UEFI have settings to turn on/off UEFI or CSM mode and then system defaults to that.
Dell seems to need to have CSM/Legacy on, but you still can and should boot in UEFI mode.
Boot of flash drive is separate from boot of hard drive. You choose which way to boot each time with flash drive boot option.

If UEFI Secure boot is off, you should have UEFI or BIOS boot options.
If UEFI Secure boot is on, you only have UEFI boot and may not have any flash drive boot options, unless you turn on another setting somewhere to allow USB boot. USB boot by default is not assumed to be secure.

Windows 7, even if installed in UEFI mode has no UEFI Secure Boot mode. So either just BIOS or just UEFI.
And Windows only boots in BIOS mode from MBR partitioning and only from gpt partitioning with UEFI.

---

### Post by Rick St. George on 2017-10-27
Thanks for the Info OldFred, Good to know. 

But fail to see the relevance to my situation. The BIOS/UEFI has not changed, and neither has the Boot sequence / folders as the previous working system was Cloned, should all match. Yes? Just asking for confirmation and knowledge. Thanks!

---

### Post by oldfred on 2017-10-27
What brand/model system?
What video card/chip?

Is UEFI/BIOS drive setting AHCI, not IDE nor RAID?

Run this with both drives connected from live installer.
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

While you often have to clone Windows, I am a firm believer that it just easier to reinstall Ubuntu, restore /home and/or data and list of installed apps. 
I typically install each new release using that procedure, but keep LTS version as main working install.

---

### Post by Rick St. George on 2017-10-29
> **oldfred said:**
> What brand/model system?
What video card/chip?

Is UEFI/BIOS drive setting AHCI, not IDE nor RAID?

Run this with both drives connected from live installer.
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair 

HP EliteBook 6930p
Video: RV620/M82; Mobility Radeon HD 3450/3470; 33 Mhz, 32 bits, 

UEFI "Enabled" (according to BIOS, but UEFI Boot Mode is "Disabled", If attempt to Enable, this Message appears;
                       The UEFI Boot option on this system is provided for development purposes only and is currently NOT
                       fully supported by HP. Preboot Authentication and Drive Lock are currenlty NOT supported under UEFI
                      boot mode. HP strongly recommends disabling Preboot Authentication and Drive Lock before enabling
                      UEFI Boot on this system.)

Cannot connect both drives. Need USB and SATA disk enclosure! Ran LiveCD on current Upgrade 1TB Drive;
"ERROR: Sub-process returned an Error Code, problem executing scripts APT: ...."; Ran INSTALL anyway ... and;
[http://paste.ubuntu.com/25846837](http://paste.ubuntu.com/25846837)

Note: SDA3 is currently blank. Wanted to make a 3 & 4th partition, but Gparted and Win7 won't let me. 
It looks like the UUID on line 528 does not match !!!
Standing by for instructions!

---

### Post by oldfred on 2017-10-29
Specs say that is a core2?
If so then not really UEFI.
But have you updated UEFI/BIOS to latest version for your system from HP?

I would use live installer to correct UUID in fstab, but if true clone, UUIDs should have been the same.
Swap also looks like it has wrong UUID also.
Only if you partition in advance and copy system, then you need to edit fstab, totally reinstall grub, so all its UUIDs get updated, and perhaps a few more places.
Often easier just to reinstall & restore backups of /home, list of apps and any other settings or data you normally backup.

---

### Post by Rick St. George on 2017-10-29
Modified FSTAB file with correct UUIDs and that fixed it. System now boots OK, defaults to Xbuntu on timeout, boots to Win7 OK.
Now I will research multiboot as I want to add Win10 partition for testing .... unless you think that is not advisable?!?!?

BOTTOM LINE:
Thanks everyone for your help. Botom line ... make sure if Partition, then Clone, modify the FSTAB for proper UUID of partitions.

```

sudo blkid
gksudo gedit /etc/fstab

```

---

### Post by oldfred on 2017-10-30
I have seen several users with multiple installs of Windows.
But second install with BIOS/MBR takes over booting and installs its boot files in the primary NTFS partition with boot flag.
Best to have all Windows installs in primary partitions, then you can separate them and have boot files in each partition. And boot both from grub. Otherwise you boot grub then in Windows (BCD) choose which copy of Windows you want.
       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth + words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) 
    
Also with Windows 10 you must make sure fast start up is off, otherwise grub will not boot hibernated Windows. And on updates Windows may turn it back on. If you miss turning it back off, you have to temporarily reinstall Windows boot loader to directly boot.
Often better to have separate drives for Windows & Linux, so you can always have Windows boot loader in MBR. Or have newer UEFI system that can always be directly booted from UEFI.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

