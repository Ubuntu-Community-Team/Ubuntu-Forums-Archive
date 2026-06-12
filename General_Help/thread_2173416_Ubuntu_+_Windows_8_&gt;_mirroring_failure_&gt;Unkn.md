---
title: "Ubuntu + Windows 8 &gt; mirroring failure &gt;Unknown Filesystem grub rescue"
date: 2013-09-09
forum: General Help
---

### Post by edd13 on 2013-09-09
Hi there

I recently have made something really stupid and I would like to ask any ubuntu expert to please help me out. I also would like to remind that I am very new to linux ubuntu

I had a dual boot system which had W8 and ubuntu running in 2 different solid state HDs then I had the brilliant (stupid) idea to mirror the windows 8 HD with linux which a completely forgot, I deleted the HD where ubuntu was installed and mirrored the the solid state HD.
I then restared the PC abd now I cant get into my machine even after disconnecting the ubuntu HD it looks like grub has taken over > error: unknown fylesystem grub rescue

I want to tests things out first mirroing windows and then later on after fixing windows I want to re install ubuntu 13.04

Please help me to sort this out

Thanks

Adding more info:

I have tried to install ubuntu again but it does not work
I tried to boot using the windows CD but it keeps giving me the same unknown filesystem message grub rescue. 
Could anyone help me please

I am online checking this forum

---

### Post by edd13 on 2013-09-09
Anyone please?
I need to fix my pc and I am also checking on google but no joy so far

Thanks

---

### Post by edd13 on 2013-09-09
PLEASE GUYS....HELP ME...i am getting really frustated

---

### Post by crazymonkey05 on 2013-09-09
do you have a windows 8 install disk? if so you can unplug your linux SDD so they dont get touched and then you can do a recovery on windows 8 and try and repair the MBR of windows 8

---

### Post by edd13 on 2013-09-09
Hi crazymonkey05

I will try this step and will let you know

Thanks

---

### Post by edd13 on 2013-09-09
It does not work.
I did unplugged the linux ssd and tried to boot from windows 8 cd but I still get the same window showing the same message grub rescue

Any other ideas?

---

### Post by edd13 on 2013-09-09
There must be a command line that fix this issue. i had a similar problem when installing ubuntu and windows (dual boot) and someone send all the commands to fix this issue and worked.
I had the same grub rescue screen.

---

### Post by edd13 on 2013-09-09
Does anyone knows any sort of commands to fix this issue please

---

### Post by oldfred on 2013-09-09
You need either a Windows 8 repairCD or Linux liveDVD or flash drive. The one you used to install Ubuntu will work if the standard desktop installer.
Is system UEFI or BIOS?

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

If UEFI system you may need this:
      
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by edd13 on 2013-09-10
Hi Oldfred

My system is UEFI

I have tried to access W8 using the installing disk but it does not work. I keep getting the grub rescue screen

I also tried to install ubuntu again but no joy as well. Maybe I am not creating the right partitions etc....I am new to linux

I will go through all the links you sent to me later on today and will try to fix.

Thanks

---

### Post by edd13 on 2013-09-10
Hi 

I followed the guide to install boot repair and under the GRUB location tab is select (by default) PLACE GRUB IN ALL DISKS (EXCEPT USB DISKS WITHOUT OS)
Is this the right option? I also have windows 8 installed...I am in doubt

please let me know

---

### Post by edd13 on 2013-09-10
I am really confused because some options related to the MBR are greyed out and the boot repair guide is showing something else. What are the right steps?
What do I really need to do to fully enable windows on my PC?

Please advise

---

### Post by edd13 on 2013-09-10
I have followed the guide and it got worse....Jesus christ now is showing a black screen which says that windows 8 is not present...MISSING OPERATING SYSTEM

PLEASE COULD ANYONE HELP ME

---

### Post by edd13 on 2013-09-10
I have tried to boot from both ssd and I get the same MISSING OPERATING SYSTEM screen

I just want to be able to logon to windows again

---

### Post by edd13 on 2013-09-10
Please does anyone knows how to fix this issue?

I followed the guides sent to me using boot repair and it did not work. Now It is showing MISSING OPERATING SYSTEM

I really need to sort this out and access my windows files and folders and at the moment I am really stuck

Any suggestions PLEASE? I NEED HELP!!!

---

### Post by edd13 on 2013-09-10
Can anyone help me please...this is really frustrating.....

---

### Post by oldfred on 2013-09-10
Please only bump once per 24 hours, we all are volunteers and offer our time, but are not always available.

Post link to BootInfo report so we can see details.

You have an UEFI system. Are you trying to boot with secure boot on or off? Only secure boot systems will boot with it on. Windows should boot with it on or off but some systems will not boot unless secure boot is on.
Or are you trying to boot in BIOS/CSM mode?  That will not work at all unless you have installed a BIOS based system. 

You should have screens similar to those posted by other users with different systems.

---

### Post by edd13 on 2013-09-10
Hi

I do apologise for all the replies i did not know that I should post only once.

Security boot is now Windows UEFI and the standard mode is selected.

I boot from the windows CD but still get the windows boot manager screen and it keeps saying that MISSING OPERATING SYSTEM.

I inserted the windows CD chose to repair and it did not work...whatta peanuts is going on????

I need to recover my windows system and I don`t understand why it keeps saying that the OS is missing....this started to happen after I ran that ubuntu boot repair running ubuntu from a usb stick and and chosing the otion to run ubuntu without installing.

How can I recover my PC?

Thanks

---

### Post by oldfred on 2013-09-10
I need to see what is where. 
Post link to BootInfo report from Boot-Repair. You do not have to have Boot-Repair make any changes if concerned.

---

### Post by edd13 on 2013-09-11
Hi oldfred

this is the url that boot repair Bootinfo gave me:
[http://paste.ubuntu.com/6093992](http://paste.ubuntu.com/6093992)

I was able to get this info through the usb live and TRYING UBUNTU WITHOUT INSTALLING SOFTWARE

Please let me know if you do require any more info.

Thanks

---

### Post by Kevin_Arnold on 2013-09-11
If you set up your ubuntu install to mirror over to the windows disk, just a boot repair isn't going to fix it. You're going to have to completely reinstall Windows from a CD, which should re-write the boot records and such. Your old Windows install is most likely gone at this point.

---

### Post by edd13 on 2013-09-11
Was the opposite...i tried to mirror windows 8....and completely forgot about ubuntu.

Do I really have to install windows 8 again? and about ubuntu on the other ssd...I would like to uninstall ubuntu completely from my ssd and will run it on VM

Any other suggestions?

Thanks for your reply

---

### Post by oldfred on 2013-09-11
Boot-Repair shows several issues:
> GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
=================== Advice displayed in case of recommended repair
SFS detected. You may want to retry after converting Windows dynamic partitioning (SFS partitions) to a basic disk. This can be performed via tools such as TestDisk or EASEUS-Partition-Master / MiniTool-Partition-Wizard.
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?
If Windows is on dynamic partitions, Linux does not see nor work with the Windows install. Partitions shown as SFS are dynamic.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

### Post by Kevin_Arnold on 2013-09-11
> **edd13 said:**
> Was the opposite...i tried to mirror windows 8....and completely forgot about ubuntu.

Do I really have to install windows 8 again? and about ubuntu on the other ssd...I would like to uninstall ubuntu completely from my ssd and will run it on VM

Any other suggestions?

Thanks for your reply

Ahhh, I guess I read it wrong. As long as one of your drives still has the windows install and just the boot record is messed up, it should be "fixable."

---

### Post by edd13 on 2013-09-12
Hi oldfred

Are you saying that my windows disk is a dynamic disk? 

Anyway you want me to try converting this windows disk to basic and then I might have a chance to reinstall w8...right?

How can I get rid of Ubuntu?

---

### Post by oldfred on 2013-09-12
If you do not want Ubuntu you can keep dynamic partitioning. I think even some Windows tools have issues with dynamic as it is a logical partitioning layer over the physical layer. Only those Windows tools designed for dynamic partitions will work. Similar to issue in Linux with LVM partitioning.

If you install a Windows boot loader to your Windows drive and set BIOS to boot from that, then you can just delete everything related to Linux.
       An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic !  This should fix boot issues, but will not delete partitions.
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by edd13 on 2013-09-12
Hi oldfred

Let`s go by parts because I am very confused and will have a heart attack if my w8 does not get fixed

1st - I downloaded minipartition tool because I can create a bootable disk and this is the only way to access my system but the thing is the free version does not allow me to cobert the dynamic disk to basic (I can see the all the linux partitions and the disk is basic, on w8 it is saying the the disk is dynamic and it also says BAD DISK IN BLACK) and my only option is to buy the right version which can be done tomorrow.

The other thing is I do want to get rid of ubuntu but my main priority is to recover windows as soon as possible. I can`t install anything to my windows as you requested because I can`t even access it.
Sorry being a pain in that place but could you please be more specific about how to recover my W8? I want to fix my w8, be able to boot and them I will eliminate the other issues.

Please guide me....shall I buy the minipartition tool and then change from dynamic to basic? Is it the 1st step? Is there another option?

Thanks

---

### Post by edd13 on 2013-09-12
Sorry but I forgot to add this....
I don`t understand when you say > [COLOR=#000000]If you install a Windows boot loader to your Windows drive and set BIOS to boot from that, then you can just delete everything related to Linux. because I can`t access my windows 8, I can`t do anything but I can access ubuntu via live usb and then use terminal to fix windows using cmd line or maybe boot repair > please give me the light

Thanks[/COLOR]

---

### Post by oldfred on 2013-09-12
I have no experience with Minipartition tool or Easus tools. Users have reported they worked if no more than four partitions exist so they can convert back to basic type partitions. You may be able to find the old version as it had free conversion. I know 4.2 had it several years ago and may be available from other download sites.

One user did use testdisk and it worked supposedly. I would make sure you have good backups if you want to use testdisk, but it is free.
 SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)



I do not know how to fix Windows other than the basics as you need to have a working Windows to dual boot.

Often once you leave fast boot on and change partition size Windows has all sorts of issues.
You may want to delete hiberfil.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

Did you create a Windows repair flash drive?
      
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by edd13 on 2013-09-13
Hi oldfred

I will try the mini partition tool 4.2 and convert the disk then I will have a go and if necessary use boot-repair again to send you more info.

I do have a recovery usb stick for windows 8.

I took a day off today just to sort this out because I need to fix it today so I will be online at all times today...keep me posted

Thanks

---

### Post by edd13 on 2013-09-13
Hi oldfred

I have converted the dynamic w8 disk to basic...

I also have a usb recovery disk which I tried to use....automatic repair does not fix anything, reset my pc will remove all my files, UEFI firmware settings will update/change and CMD is also available

Do you want me to boot using ubuntu usb and get boot repair info for you again? Would it help?

Please let me know as I will be online all day today(had to take a day off today to solve this problem)....meanwhile i am reading all the posts and trying to fix myself

My boot options is showing secure boot for Windows UEFI mode - Standard. I hope this is the right option. The other options is OTHER OS

More updates....
I run diskpart using cmd from the usb recovery disk and it is showing all the disks but the W8 is indicated as FOREIGNER and ubuntu as ONLINE.
Another think is showing all 3 windows partitions but the type has not changed to basic and still showing dynamic but i did convert from dynamic to basic using mini partition tool



Thanks for your time and support

---

### Post by edd13 on 2013-09-13
Hi oldfred

this is the new boot-repair URL after using mini partition tool > [http://paste.ubuntu.com/6100984](http://paste.ubuntu.com/6100984)

I also ran the advanced options to fix the MBR and go this URL > [http://paste.ubuntu.com/6100955....I](http://paste.ubuntu.com/6100955....I) hope this info helps

gparted shows me the w8 ssd as /dev/sdb1 NTFS > /dev/sdb2 ntfs > dev/sdb3 unknown > and 1MB unallocated

Thanks

---

### Post by oldfred on 2013-09-13
It will be unknown as Linux does not mount the SFS or dynamic partitions. I did just see for forensic work a command line tool has been developed to look into SFS partitions.

Generally Windows PBR - partition boot sectors must have correct Windows info in them. Yours is just showing a size error but that may be an issue. I would normally suggest chkdsk on sdb1, but with dynamic partitions I do not know if that is correct or not.

---

### Post by edd13 on 2013-09-13
I just ran boot repair and it says that was succesfully > [http://paste.ununtu.com/6101927](http://paste.ununtu.com/6101927)

I don`t understand when you say chkdsk on sdb1....shall i use terminal or cmd from the w8 recovery usb? Sorry mate but i don`t have any linux knowledge and it is getting very frustating.

Oldfred I am lost with this linux partitions and now it got to a point that It looks like I am not going anywhere. In had a similar problem with this bloody grub and you and a guy called darkod helped me to fix by knowing which sda b c d was related to linux and then you guys sent me some terminal commands and that solved my problem.

Is there a easier way to solve it?

---

### Post by oldfred on 2013-09-13
Chkdsk is a Windows repair, and you cannot run that from Linux. It repairs Windows file corruption issues and corrects most issues with the partition boot sector. Some times with file issues you have to run until no error are posted as it does not always fix everything in one pass.

       [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

Do not know if they made any changes with Windows 8, but some users have posted that they had to run it. Any resize of a NTFS partition also requires chkdsk. Usually Windows will set the chkdsk flag and auto run on reboot in those cases.

---

### Post by edd13 on 2013-09-13
I understand what chkdsk does and I can only run it through the usb recovery pen drive and it says after running the cmd: The type of the file is NTFS. Cannot lock current drive. Windows cannot run disk checking on this volume because it is write protected.

Jesus christ....

---

### Post by edd13 on 2013-09-13
Diskpart says that disk 0 (where ubuntu is installed) is a GPT disk its status is ONLINE
disk 1 (where windows is installed) is dynamic and its status is FOREIGN - so that bloody mini partition did not change anything.

[COLOR=#000000]Intel rapid Smart technology (RST), Intel Smart Connect Technoly is disabled.[/COLOR]
[COLOR=#000000]CSM is ENABLED ( it was AUTO) and boot device control to UEFI and LEGACY OpROM.[/COLOR]

[COLOR=#000000]Secure Boot is disabled and I changed the OS type to OTHER OS and also tried WINDOWS UEFI MODE.[/COLOR]
[COLOR=#000000]The setup mode is EZ MODE.[/COLOR]

Does it help in anything?

---

### Post by oldfred on 2013-09-13
That the Ubuntu drive is gpt should not be a problem. Windows does not read Linux formatted partitions anyway. But Windows (except XP) will read data from gpt drives if partition is NTFS. But Windows only boots from gpt partitioned drives with UEFI, not BIOS.

Not sure what FOREIGN means. May just be the dynamic? That was not originally Microsofts's partitioning scheme.
Or it could just be the PBR - partition boot sector issue? I know it usually says RAW if unformatted or seen as something other than NTFS.

But it sounds like dynamic did not get removed. I have seen posts by uses where that tool has worked before. But have no details. Does it need a final confirmation or something to make it rewrite partition table?
As long as fdisk, or partition tools from Linux show it as SFS is still is dynamic.

---

### Post by edd13 on 2013-09-13
This was the command that you guys sent to me and it fixed all my issues with w8 + ubuntu grub
sudo mount /dev/sdb6 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sdb

Just ran again mini partition tool 4.2.2 and this time worked now the partition is showing as NTFS and the dynamic status has gone
What shall i do now?

Thanks

---

### Post by edd13 on 2013-09-13
Ran boot repair again to fix > [http://paste.ubuntu.com/6102154](http://paste.ubuntu.com/6102154)

this is the bootinfo summary > [http://paste.ubuntu.com/6102166](http://paste.ubuntu.com/6102166)

Ran diskpart and it is now showing windos as ONLINE and there`s no dynamic disk 


Please tell me that we are now going somewhere

---

### Post by oldfred on 2013-09-13
Those command are to reinstall grub2's boot loader to the MBR of sdb when you have /boot on sdb1 and main Ubuntu install or / (root) on sdb6.
But grub in MBR is for BIOS booting, not UEFI booting. Which do you want?
If you want to dual boot, you need Ubuntu in same boot mode as Windows, so if Windows is BIOS, you need Ubuntu in BIOS boot mode even if you have a newer system with UEFI. UEFI will just be in CSM mode.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

Also Ubuntu on gpt drives in BIOS mode need the 1MB, unformatted partition with the bios_grub flag for grub to correctly install.

---

### Post by edd13 on 2013-09-13
I just want to boot windows PLEASEEEEE!!!!!!!!!!!!!!!!

the CSM is enabled, boot device control is UEFI and legacy OpROM as well as all the other Boot sections of my asus P8Z77V-LX

ubuntu is gpt as it is showing on diskpart....

---

### Post by oldfred on 2013-09-13
If you choose Windows drive in UEFI/BIOS does it not boot?
Then that is Windows issues that will need Windows repairs.

Having Ubuntu on a different drive does not change Windows unless you hibernate Windows and force writing from Ubuntu and corrupt hiberfil.

---

### Post by edd13 on 2013-09-13
I can`t wait anymore....sorry will install windows again 

I will remove ubuntu from the other ssd and run on a VM....just need to find out how to delete permanently ubuntu from my other ssd

Thanks for yr help

---

### Post by edd13 on 2013-09-13
I will look for a different point of view and see if somebody else might be able to provide me a solution otherwise I will install W8 from the scratch....unfortunately!!!!

Anyway thanks again for your help!!!

---

### Post by oldfred on 2013-09-13
From what little I can tell from BootInfo report, even thought you may have UEFI, you system is in BIOS mode for Windows. So you should just need to run Windows repairs.

I think the main issue is that you converted drive from basic to dynamic which does not work with Linux and is causing additional issues.

Since mostly Windows issues.
 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by edd13 on 2013-09-13
As I said before I can run windows I can`t get to it and system repair does not do anything

---

### Post by edd13 on 2013-09-20
Problem was not fixed. I had to installed w8 on top of ubuntu...at least my pc is running now

---

