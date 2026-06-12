---
title: "Ubuntu + Win8 gone wrong"
date: 2013-09-09
forum: General Help
---

### Post by Johan_Groenewold on 2013-09-09
Hi there,

My new study requires Linux for programming, writing files in LaTeX and so on. So I decided I'd buy a Dell Inspiron 15z notebook and install Ubuntu on it. Unfortunately, it had Windows 8 installed on it. So, after some reading, I disabled Secure Boot, set the Boot Mode to Legacy and tried to install Ubuntu. It worked quite well. However, when rebooting my system to complete the installation, it didn't boot any OS whatsoever. I tried to reverse the settings to at least be able to boot Windows, but that failed too.

Now, after some struggling, I finally managed to boot Ubuntu.. on the LiveCD. When running the installer from there, it says I already have Ubuntu installed (yay, that's correct), but the GRUB doesn't load it, if the GRUB shows up at all. Luckily, the LiveCD allows me to see how the disks (32GB SSD + 500GB HDD) are partitioned. I see that the changes in Boot Mode probably ruined some stuff. I attached some screenshots from the notebook below.

As you can see, there is no logic at all. PRB Image, OS, DIAGS and WINRETOOLS, all part of Windows 8, are somehow located in /media/ubuntu. I'm pretty sure I didn't install it this way. I allowed Ubuntu to use 10GB of the SSD, and some 300GB of the HDD. Probably the changes in the BIOS moved some stuff around, resulting in this.

Is there any way I can get the notebook to boot in either Ubuntu or Windows 8 without problems? I don't really care if one of the two OS's won't work anymore, as long as I can boot it. (Heck, I'll even run Ubuntu in VirtualBox if that's what it takes to solve this)



[IMG]http://i.share.pho.to/a0bd4d00_o.png[/IMG][IMG]http://i.share.pho.to/8fc03aa4_o.png[/IMG]
[IMG]http://i.share.pho.to/8e3452d2_o.png[/IMG][IMG]http://i.share.pho.to/2c968ad5_o.png[/IMG]

---

### Post by kc1di on 2013-09-09
Hi,

Sorry your having problems uefi can be a pain in the###  but it can be done.
my first step would be to go to the Boot-Repair page download and run boot-repair
it fixed my uefi boot with win 8 and tells you step by step what to do.
you can find it [here ]("https://help.ubuntu.com/community/Boot-Repair")
Good Luck :)

---

### Post by Johan_Groenewold on 2013-09-09
[S]Hello,

I tried to run the commands, as I am using the LiveCD. It results in the following:
....... (some stuff with "gpg:" in front of it, a line with OK, and then:)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg), are you root?

So, should I burn a Boot-Repair disk to fix this?[/S]
[B]
Edit: [/B]Okay, that's solved. The second command, installing it, ends in this:
Errors were encoutered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Johan_Groenewold on 2013-09-09
Okay, after some struggling, I was able to run the Boot-Repair.

Plus side: Ubuntu works <3
Downside: Only Ubuntu works. Loading the HDD or SSD doesn't do anything. At all. It just gives me a white underscore on a black background, blinking. When I load Windows Boot Manager, I actually reach the GRUB, where I can run Ubuntu (works!), Advanced options for Ubuntu (haven't tried), and some Dell/Windows stuff. All of those last ones result in the computer telling me it can't be found, bringing me back to the GRUB.

While I'm quite happy with this progress, is there any way to either load Windows using the GRUB (maybe I'll have to change some BIOS settings back to default?) or remove those options and load Ubuntu instantly? I can, for instance, see that the program "Disks" gives me an overview of both disks. The partition OS (/dev/sda5) is located on there, has 105GB, Contents = FAT (1.3.00) and not in use. Can I get that to use, or is that not the way to think?

Thanks for now though! :D

---

### Post by oldfred on 2013-09-09
Please attach screenshots not post in line. Some users do not have high speed Internet and just trying to look at your post may lock up their download for a while.

Best to post link to BootInfo report.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    
You have an UltraBook which has the separate SSD, seen as sdb by Linux. It looks like you installed in totally encrypted mode as that uses LVM to enable the encryption. I do not know about that mode but am glad to see you got it working.
But are you in BIOS boot mode or UEFI boot mode? Windows is in UEFI boot mode and to easily dual boot you need both Ubuntu & Windows in UEFI boot mode.
Ultrabooks also have the Intel SRT which uses RAID and causes issues. And have dual video which also often causes issues. See link in my signature for more info.

Dell's seem to be very similar across models with difference just which options are included.
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)

---

### Post by Johan_Groenewold on 2013-09-09
Hi oldfred,

Yeah, I'm sorry for the inline images. The attachment system denied 3 of the 4 images. Don't know why, a red warning symbol just appeared.

My BootInfo at this moment would be:
[http://paste.ubuntu.com/6084158/](http://paste.ubuntu.com/6084158/)

During the Boot-Repair I got another one, which is:
[http://paste.ubuntu.com/6083774/](http://paste.ubuntu.com/6083774/)

The Boot Mode I'm in is "Legacy", the only other option is "UEFI". I have Secure Boot disabled and "Load Legacy Option Rom" enabled (can't disable that anyway). In Advanced, Intel SpeedStep & Intel Rapid Start Technology are both enabled. "SATA Operation" is set to AHCI (it can be set to ATA and Intel Smart Response Technology as well). That's about it for the relevant information I guess.

The solutions in the links you've given are, as far as I can see, mostly useful when performing an entire new installation. However, I can't get in Win8 at this moment, so making a backup isn't really an option. Is downloading a Win8 recovery disk an option you think? There wasn't any data stored on it whatsoever. Or does the BootInfo-links provide enough information?

:)

---

### Post by kc1di on 2013-09-09
you will have to change to UEFI mode in order to boot win 8.  you should be able to boot ubuntu in that mode also. but you have to install the correct grub boot file for efi.
that should have been explain when you ran boot-repair

---

### Post by Johan_Groenewold on 2013-09-09
The boot-repair did say something about it, but I had the option to just continue, so I continued. I'll change it and run boot-repair again.

---

### Post by Johan_Groenewold on 2013-09-09
Okay, that didn't work out. When changing to UEFI Mode and pressing F12 at startup, it gives me this:

[ Boot mode is set to: UEFI with Legacy OPROM; Secure Boot: OFF ]

LEGACY OPTIONS:
Hard Drive
CD/DVD/CD-RW Device
Second HDD
NetWork

UEFI OPTIONS:
Windows Boot Manager (which leads to GRUB)
UEFI: WDC WD5000LPVT-75G33T0
UEFI: HL-DT-ST DVD+/-RW GU70N
UEFI: Network Card
UEFI: Network Card

OTHER OPTIONS:
Diagnostics
Enter Setup
Peripheral Device Setting (OPROM Setting)
Change Boot Mode Setting

----------------

So, should I turn OPROM off (never turned it on actually), or should I turn Secure Boot back on? The way it is now, I can't boot the CD/DVD in UEFI at all. And when doing it this way, the boot-repair still pops up the message that I am in Legacy mode

---

### Post by oldfred on 2013-09-09
You need to have legacy off. Or if yours is one that only has secure boot and a combination of legacy/CSM/BIOS and UEFI where it tries efi and if that fails boots with BIOS/MBR, then you must boot in UEFI mode. If secure boot is on or off, Ubuntu should boot. But generally better is secure boot is off.
Does your Windows boot with secure boot off? Some do & some do not.

If booting Windows from UEFI leads to grub you must have used the rename function in Boot-Repair. That is for the few systems that have hard coded in the UEFI code to only boot the Windows efi file. Many do not need the rename and then UEFI menu would show both Windows and ubuntu as UEFI boot choices.
When secure boot is on only secure boot, boot options will be available to use to boot.

From others with Dell, they usually did not have lots of problems. Most were related to the Intel SRT or dual video which are not UEFI issues.

Did you do this?
 Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
It does this:
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by Johan_Groenewold on 2013-09-09
When I turn on Secure Boot, I get a window saying:
```
internal hard disk drive not found
to resolve this issue, try to reseat the drive
No bootable devides--strike F1 to retry boot, F2 enter Setup Menu, F5 enter PSA
```
F1 doesn't work, F2 brings me to the BIOS and F5 runs a diagnostic test, telling me everything is fine.

I haven't used the Rename-function. As far as I know that is, I just made it do the Recommend Repair and that's it.

At this moment, Windows does not boot at all, regardless the settings of Secure Boot. It used to boot with Secure Boot off though. When I press F12 at boot now and select the CD/DVD drive, I get the GRUB menu. Selecting Try Ubuntu or Install Ubuntu results in a black screen.

Should I run the Boot-Repair from the LiveCD in Legacy Mode and make the changes you suggested, or should I burn a Boot-Repair CD and try to run that in UEFI mode?

---

### Post by oldfred on 2013-09-09
It looks like rename was done. I might try the undo on rename from Boot-Repair.
This is just Ubuntu but Boot-Repair has been added. It is large so you really need flash drive or DVD.

I do not think I would have used LVM on SSD. Did you select encryption when installing?

---

### Post by Johan_Groenewold on 2013-09-10
I didn't select encryption when installing. I wasn't even asked for, I believe.

I managed to run boot-repair on Ubuntu (not the LiveCD, since the normal Ubuntu is the only one I am able to boot on UEFI), and got this Boot Info:
[http://paste.ubuntu.com/6088254/](http://paste.ubuntu.com/6088254/)

Should I run boot-repair again on Ubuntu (not LiveCD) in UEFI mode and make the changes (Rename windows EFI files & 'SecureBoot') you suggested, or is that very dumb to do on a normal Ubuntu (non-LiveCD) environment?
As you can see, I'm kind of careful now, since I don't want to screw the system up even more :(

**Edit:** Oh awesome. The laptop just restarted. The GRUB has no Ubuntu-option anymore. Pressing F12 gives me an option 'ubuntu', but that leads directly to the GRUB, where no Ubuntu is located. :\
**Edit2:** Without changing a thing (how could I, I'm not able to reach any of the OS's) the ubuntu option now leads to the GRUB where the normal (Try, install Ubuntu) options are. None of which are working, but still. The CD/DVD option is leading to the (same??) GRUB, can't load from there either

---

### Post by oldfred on 2013-09-10
Boot-Repair is showing all sorts of mount issues. That indicates you did not turn off fast boot (hibernation) or Windows needs chkdsk. After any resize you have to run chkdsk on Windows.  Normally if you use Windows own disk tools to shrink Windows and immediately reboot then it will auto run chkdsk.

The mapper data may just be Linux seeing the Intel SRT which uses RAID somehow as the cache on the SSD, to speed up Windows booting and maybe other things.
Grub will not normally install if the RAID meta-data is still on drive. With Ultrabooks you have to turn off the SRT and remove the RAID meta-data.  Lots more details in link in my signature on Ultrabooks. You also may have video issues.

       sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

The live installer flash drive will boot two ways, one UEFI and you see grub menu and BIOS where you get purple accessibility screen. It just is which option you choose from UEFI menu. And how you boot installer UEFI or BIOS is how it will install.
      
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Johan_Groenewold on 2013-09-10
I do have "Intel Rapid Start Technology" enabled. A quick Google search learns me it's quite the same thing as hibernation.  I did shrink the disk using the Win8 built-in tool and rebooted afterwards. In that case, apparently it didn't run chkdsk itself?

I turned the SRT off now. Can't get it to boot though. Same stuff as before (can get into GRUB when selecting either ubuntu or CD/DVD, all options in GRUB resulting in black screen).

Just to make sure, I am now booting in:
UEFI Mode
Secure Boot = On
Intel SRT = Disabled
SATA Operation = AHCI
Load Legacy Option Rom = Disabled (because Secure Boot is enabled)

And while we're at it, I'm not sure one of these is even relevant, but it can't hurt to mention I guess:
Intel SpeedStep = Enabled
Virtualization = Enabled
Integrated NIC = Enabled
USB Emulation = Enabled
USB Powershare = Enabled
USB Wake Support = Disabled
Adapter Warnings = Enabled
Function Key Behaviour = Function Key (Okay, pretty sure this is unrelated ;))

---

### Post by oldfred on 2013-09-10
Not sure about all the settings. But one user posted this:

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Ubuntu on Laptop Toshiba Satellite P75 - Haswell
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

Then you may still have video issues with the dual video. Does yours allow you to set one or the other, or does it switch automatically?
You may need bumblebee. The very newest nVidia has some updates for the dual video systems but only runs nVidia so it may run hotter and only works with 13.10 and maybe even then you need some other updates. Since 13.10 is about at beta it is not suggested unless you are willing to have crashes and report bugs. Best to have another working install to always be able to boot if testing next version.

---

### Post by Johan_Groenewold on 2013-09-12
I turned the NIC off, but still no luck. Still get some options for booting:
Windows Boot Manager
ubuntu
and some UEFI stuff

Both WBM and ubuntu are directing to a GRUB with the options "Windows UEFI bkpbotmgfw.efi", "Windows Boot UEFI loader", "EFI/Dell/Boot/bootmgfw.efi", "EFI/Dell/Boot/biitx64.efi" and System Setup. None of which, except for the setup (BIOS Setup), are working.

Now, I enabled OPROM. Booting leads me to ubuntu quite fine actually (I'm quite amazed while typing this). I do have a functioning Ubuntu-environment, but it's running in Legacy mode (since OPROM allows both Legacy as UEFI). Is there anything I can do from here? Can't boot into Ubuntu in UEFI Mode. Somehow. Perhaps I can try fixing the GRUB from here, so I can actually reach Ubuntu in EFI mode? Or can I do some partitioning to fix anything? :)

---

### Post by oldfred on 2013-09-12
Boot-Repair can convert a BIOS/CSM/Legacy install to UEFI by uninstalling grub-pc and installing grub-efi.

But your UEFI entry for Windows should directly boot Windows.
Boot-Repair has a rename function which was automatic and I thought it was changed to a choice. The rename fucntion is for the few UEFI systems that are hard coded to only boot the Windows efi file, so it changes the Windows efi file to really be the grub2 shim and from grub you boot the backed up Windows.

       Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)

 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
 Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi 


Only if your system will not boot ubuntu entry from UEFI menu should you have renamed.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

If further repairs do not work, post link to BootInfo report from Boot-Repair.

---

### Post by Johan_Groenewold on 2013-09-13
Running boot-repair, I get the instruction to type this in my terminal:
sudo chroot "/mnt/boot-sav/mapper/ubuntu--vg-root" apt-get install -y --force-yes grub-efi linux"

However, doing this, I get the result:
```
[FONT=arial]dpkg: error processing grub-efi-amd64 (--configure):[/FONT]
[FONT=arial] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=arial]dpkg: dependency problems prevent configuration of grub-efi:[/FONT]
[FONT=arial] grub-efi depends on grub-efi-amd64 (= 2.00-13ubuntu3); however:[/FONT]
[FONT=arial]  Package grub-efi-amd64 is not configured yet.[/FONT]

[FONT=arial]dpkg: error processing grub-efi (--configure):[/FONT]
[FONT=arial] dependency problems - leaving unconfigured[/FONT]
[FONT=arial]No apport report written because the error message indicates its a followup error from a previous failure.[/FONT]
[FONT=arial]                          Errors were encountered while processing:[/FONT]
[FONT=arial] grub-efi-amd64[/FONT]
[FONT=arial] grub-efi[/FONT]
[FONT=arial]E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Should I just continue or is there any way to work this out?[/FONT]

---

### Post by oldfred on 2013-09-13
Why are you getting the mapper. Did you install with full encryption which uses LVM and then has the mapper or did you not remove the RAID meta-data from your drives (post #16). The Intel SRT RAID meta-data prevents correct install of grub. For more info see link in my signature.

---

### Post by Johan_Groenewold on 2013-09-13
I haven't removed the RAID-data. However, boot-repair asked me to delete dmraid and install mdadm instead. Can I remove the data with mdadm, or should I install dmraid again for removing it?

---

### Post by oldfred on 2013-09-13
Do not know for sure. I think Boot-Repair was asking for mdadm as that is required for certain RAID types and dmraid for others. I do not know difference. 
But if it is the Intel SRT issue then just use dmraid commands to remove RAID meta-data. Then Boot-Repair will not ask for mdadm.

---

### Post by Johan_Groenewold on 2013-09-25
I'm sorry for the late response, as I have been very busy with my study. I've been running Ubuntu from the LiveCD for a couple of days and I decided that the easiest way to go is to erase my HDD and SSD, install a fresh new Ubuntu installation on the SSD while storing my files on the HDD and never use Windows on this notebook again.

Anyway, I have no idea how to
1. erase my hard disk (or at least make sure the windows and old ubuntu aren't bothering me anymore)
2. install ubuntu on the ssd while storing media on the hdd
3. do this with my disks in RAID0

Anyone got tips for this?

---

### Post by oldfred on 2013-09-25
I would suggest to backup efi partition and Windows. We get users who have that one game or application that they just have to have Windows for and want to know how to reinstall after they totally deleted it.
Some info on backup software for Windows in link in my signature. 

If primarily a Linux user then remove RAID meta-data, and just install Ubuntu to SSD. You can have data on hard drive by either using hard drive as /home or as a data partition and link or bind the data folders into your /home.

I have posted several links to others with Dell UEFI install. These are others with Intel SRT which is really an Intel standard and almost identical for all systems.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
            Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

             lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

I have a Desktop with full 62GB SSD. But I put two / (root) partitions, one current working and one future testing. And mount data partition to /mnt/data from hard drive and link all the folders in the data partition into my /home. My 25GB / uses about 9GB total, but I mount 2 100GB data partitions from hard drive.

---

