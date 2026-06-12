---
title: "Grub - Add windows"
date: 2020-10-07
forum: General Help
---

### Post by Macamba on 2020-10-07
Because of the Ubuntu 20.04 update my system (dual boot with Windows 10, dual HD, amd64, UEFI) is a bit of a mess. For instance the boot loader thinks Ubuntu is the only flavor in town. I have been looking around and came up with the following [change]("https://unix.stackexchange.com/questions/453124/add-windows-10-to-grub2-bootloader") of the [FONT=Courier New]/etc/grub.d/40_custom[/FONT] file:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 10 (loader)"{
    insmod part_gpt
    search --no-floppy --set=root --fs-uuid 109C-D028
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

```

I tried to reboot but came up looking at a black screen, and no HD action. Clearly the wrong choice. 

I also [tried]("https://askubuntu.com/questions/661947/add-windows-10-to-grub-os-list"):
```
sudo update-grub
sudo grub-install /dev/sdb1
```

That did not work out either. What options do I have?

---

### Post by oldfred on 2020-10-07
You never install grub to a partition. 
And if you install grub to a NTFS partition you break it, as it has its own essential data where grub is in PBR - partition boot record or BS - boot sector. NTFS does have a backup that often can be restored.

But is system UEFI or BIOS?
Is Windows installed in UEFI or BIOS boot mode?
Microsoft has required vendors to install in UEFI mode to gpt partitioned drives since 2012. Users could use the old BIOS/MBR, but that was more for very old systems.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Macamba on 2020-10-08
The Pastebin is on [https://paste.ubuntu.com/p/RW4DFfXGgx/](https://paste.ubuntu.com/p/RW4DFfXGgx/).

---

### Post by oldfred on 2020-10-08
You have now mixed UEFI & BIOS which is difficult to manage, but can be done with two drives if you really want to.
You also have sda as gpt and sdb as MBR.
Windows only boot in BIOS mode from MBR(msdos) partitioned drives. You have Windows on sdb with MBR, so Windows has to boot in BIOS mode. Boot flag then has to be on NTFS primary partition with Windows boot files, your sdb1. 
So use gparted and move boot flag back to sdb1 and your Windows repair flash drive booted in BIOS mode to install a Windows boot loader to MBR of sdb. You may be able to use Boot-Repair to install a Windows type boot loader syslinux to MBR of sdb.

You somehow got an ESP - efi system partition on sdb. UEFI requires boot flag on ESP, but with Windows in BIOS mode cannot have another boot flag on Windows. Only one boot flag per drive.

Do not use auto fix with Boot-Repair when  you have multiple drives. Only use advanced mode. 
And be sure to boot in boot mode you want to repair UEFI or BIOS.

Better to back up Windows and reinstall in UEFI boot mode to gpt partitioned drive. But that will erase sdb, so backups required. Which you should have anyway when doing major system changes.

You have both a BIOS boot grub entry in both MBR and UEFI boot of grub in both drives.
You need to remove ESP on sdb, and have Windows boot loader in MBR of sdb.
If you want Ubuntu in UEFI boot mode (on either drive) you need to boot Boot-Repair in UEFI mode and reinstall grub in UEFI mode to sda.
If you want Ubuntu in BIOS mode on gpt drive, your sda, you need a tiny 1 or 2MB unformatted partition with bios_grub flag. Use gparted. Then use Boot-Repair in BIOS mode and only install grub to sda.

Windows only boots in UEFI mode from gpt drives. Microsoft has required vendors to install in UEFI/gpt boot mode since 2012 and release of Windows 8. Users could install in BIOS mode, but mostly allowed for old non-UEFI based hardware.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by Macamba on 2020-10-08
That went fast to hell in a basket. Probably made some bad choices when it went wrong. Let's not elaborate an that too much.

I had an unstable system where I had to install Ubuntu numerous times. Somewhere along the way I got the impression to create an UEFI on the Linux HD. I finally got a more or less stable system. After that I lost my access to Windows (if I remember correctly).

So what steps do I need to do? What you have written seems a bit post-grad science to me. Beyond me.

---

### Post by Macamba on 2020-10-09
If I remember correctly I added a small (200 mb) partition for UEFI. I can reinstall, and remove that partition, add the space back to my swap partition. I introduced the UEFI partition because my installation process failed time and time again. Would it  help to remove UEFI partition, reinstall, and when installation crashes to run Boot-Repair?

---

### Post by oldfred on 2020-10-09
Solution depends on what you want to end up with.

You have UEFI system, but Windows in BIOS mode.
If you just want to stay with BIOS add a bios_grub partition to sda. And reinstall BIOS boot loaders to each drive, grub to sda & Windows to sdb. Grub only boots working Windows, so you still have to keep Windows fast start up off. If Windows turns it on, then directly boot Windows using Windows boot loader in sdb.

Long term probably better to reinstall Windows in UEFI boot mode. But major change as that erases sdb.

You just need to always be consistent. Always UEFI or always BIOS.
Default boot mode setting in UEFI, only applies to installed systems.
You have to select UEFI or BIOS from most flash drive live installer or Windows repair disk each time you boot. And it installs or repairs in mode you boot flash drive.
Some installers only create an UEFI installer or a BIOS installer (not both). So when creating flash drive you may have to have correct selection there first. ISO is configured to be both.

---

### Post by Macamba on 2020-10-10
> **oldfred said:**
> Solution depends on what you want to end up with.

You have UEFI system, but Windows in BIOS mode.
If you just want to stay with BIOS add a bios_grub partition to sda. And reinstall BIOS boot loaders to each drive, grub to sda & Windows to sdb. Grub only boots working Windows, so you still have to keep Windows fast start up off. If Windows turns it on, then directly boot Windows using Windows boot loader in sdb.

My constellation worked before in what appears to be BIOS-mode. So during partitioning change the UEFI partition to BIOS? Is that a choice I will see during installation/partitioning?

Next you say: "reinstall BIOS boot loaders to each drive". Ehm, how? Does the live CD do it automatically? Or need I instruct it to do it? How? 

Then you say "grub to sda & Windows to sdb". I think grub is installed on sda, and I do not change anything of my installation of Windows on sdb, so I am in the clear on that account? Otherwise, what do I need to do?

Oh, and thanks for your help.

---

### Post by oldfred on 2020-10-10
Grub does not correctly install to gpt partition drives in BIOS mode unless you have a bios_grub partition.
With MBR, there is space after the MBR and before first partition for core.img or more of grub's BIOS boot code.
So with gparted on live installer, shrink any partition on sda, by several MB and add a 1MB unformatted partition with bios_grub flag.
Then with Boot-Repair in BIOS mode, reinstall grub to sda using advanced mode.

See if Boot-Repair's advanced mode offers to install a Windows boot loader to sdb, but if fast start up on, it may not see your Windows to offer to install a Windows type boot loader to sdb.


You may be able to manually install syslinux which is a Windows type boot loader. I have seen two versions, not sure which path is correct?
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
sudo dd if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sdb 

My UEFI system still has syslinux in the SYSLINUX folder? And in a syslinux-legacy folder. Not sure if different mbr.bin?
sudo dd if=/usr/lib/SYSLINUX/mbr.bin of=/dev/sdb
Best to use your Windows repair flash drive and run fixMBR.

---

### Post by Macamba on 2020-10-13
That failed :') 

```
Executing 'grub-install /dev/sda' failed
This is a fatal error
```

I could not find a choice bios_grub flag. The closes I could get was allocating 16 MB as "Reserved BIOS boot area". I could not find a choice bios_grub flag. 

During partitioning my choices where:
```
partition #1 of SCSI2 (0,0,0) (sda) as biosgrub
partition #4 of SCSI2 (0,0,0) (sda) as swap
partition #2 of SCSI2 (0,0,0) (sda) as ext4
```

As grub-install failed I have totally not working system again. Now I am thinking about trying to install the previous working version of Ubuntu (18.something).

---

### Post by oldfred on 2020-10-13
Gparted shows the flag as bios_grub.
Attached is old screen shot, but newer one is the same with updated graphics.

Did you leave it unformatted? It only needs to be 1 or 2MB.

Post link to new Summary Repair from Boot-Repair.

---

### Post by Macamba on 2020-10-17
I am reluctant to try again. But if I do not do it I will not get back my preferred configuration. I probably tackle it tomorrow. In the mean time, this was the choice I made during partitioning:
[[img]https://i.ibb.co/CMg6NXv/Partitioning-choices.jpg[/img]](https://ibb.co/CMg6NXv)

---

### Post by CelticWarrior on 2020-10-17
Seems fine but, again, only 1 or 2MB is enough. Anything larger is a waste of space.

---

### Post by Macamba on 2020-10-18
Well, here goes nothing:
[[img]https://i.ibb.co/w7JTXbg/Partitioning-final.png[/img]]("[url=https://ibb.co/w7JTXbg)"][[img]https://i.ibb.co/w7JTXbg/Partitioning-final.png[/img]](https://ibb.co/w7JTXbg)[/URL]

[[img]https://i.ibb.co/2cGPdLt/Write-changes-to-disk.png[/img]]("[url=https://ibb.co/2cGPdLt)"][[img]https://i.ibb.co/2cGPdLt/Write-changes-to-disk.png[/img]](https://ibb.co/2cGPdLt)[/URL]

[[img]https://i.ibb.co/gPBgJ2T/Installation-succesfull.png[/img]]("[url=https://ibb.co/gPBgJ2T)"][[img]https://i.ibb.co/gPBgJ2T/Installation-succesfull.png[/img]](https://ibb.co/gPBgJ2T)[/URL]

In seems the installation was successful. Will restart now.

Edit: While it looked like the installation completed successfully, **when I booted my computer it stuck on &#8220;Verifying DMI Pool Data ....&#8221;. **

Next I disconnected the Linux HD, hoping to be able to boot Windows, but I came upon the error:
```
error: no such device: string of hex numbers
Entering rescue mode...
grub rescue>
```

And that was probably something I should have expected. Now I have to reinstall Ubuntu again to a state that works (the one with uefi) so I can download a Windows disk and try to get Windows up and running again, as I have pressing business to attend to using the Windows part of my system. 

Any suggestions so I cam get Ubuntu, Grub2 AND Windows running again?

---

### Post by Macamba on 2020-10-18
I booted from DVD and will put my system to sleep. Tomorrow is a new day.

---

### Post by oldfred on 2020-10-18
Post  this before doing anything else.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Macamba on 2020-10-19
> **oldfred said:**
> Post  this before doing anything else.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:

I don't know how to proceed. Do I start with the installation process ('Install Ubuntu 20.04.1 LTS' icon in my Unity Launcher (the bar to the left))? I take it  you are not talking about the 'Updates and other software' part of the installation process (FWIW, I choose 'Normal installation', 'Download updates while installing Ubuntu' and 'Install third-party software ...'), But the obvious place to do something would be the next window/part of installation process, the 'Installation type' but the second choice would be 'Erase disk and install Ubuntu, and I don't want to loose my /home. And the 'Advanced features ...' button has nothing that implies to have something to do with PPA version.

---

### Post by tea for one on 2020-10-19
[COLOR="#0000FF"]oldfred[/COLOR] is asking you to create a report from boot-repair.

Boot into a live Ubuntu session using your usb/dvd device.
Open Firefox and navigate to this site [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option as follows:-

> 2nd option : install Boot-Repair in Ubuntu

- either from an Ubuntu live-session (boot your computer on a Ubuntu live-CD or live-USB then choose "Try Ubuntu")

- connect to the Internet

- open a new Terminal, then type the following commands (press Enter after each line):

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

---

### Post by Macamba on 2020-10-20
> **tea for one said:**
> [COLOR="#0000FF"]oldfred[/COLOR] is asking you to create a report from boot-repair.

Facepalm moment :-}

Thanks: 
[https://paste.ubuntu.com/p/frGh3gFkgm/](https://paste.ubuntu.com/p/frGh3gFkgm/) 

By the bye, a “Verifying DMI Pool Data ....” error message implies hardware troubles. I did not change my hardware configuration, or change my BIOS (much, only from booting from HD, to DVD, and back to HD).

---

### Post by tea for one on 2020-10-20
Your boot-repair report is revealing some details, which probably explains your dilemma:-

[COLOR="#0000FF"]Lines 119 - 121[/COLOR]       3 operating systems
[COLOR="#0000FF"]Lines 152 - 153 [/COLOR]      2 drives with mixed partition tables and only sdb contains EFI system partition (esp)
[COLOR="#0000FF"]Line 397[/COLOR]                  Windows in Legacy mode, yet PC boots in EFI mode

The current best practice is to boot both Windows and Ubuntu in EFI mode.

Therefore, in order to be trouble-free for the future, I would suggest some radical action:-

Back up all your data from Windows and Ubuntu
Install Windows in EFI mode with GPT on sda
Disable, de-activate or remove drive sda
Install Ubuntu 20.04 LTS in EFI mode with GPT on sdb
Verify integrity of both OS by booting via UEFI screens (or boot menu)
When you are satisfied that it is OK, restore your data.

I realise that this is a time-consuming task but this thread is now 6/7 days old without a successful outcome.

Worth considering?

---

### Post by oldfred on 2020-10-20
+1 on tea for one's suggestions.

You cannot have an UEFI boot of Ubuntu on same drive as BIOS boot of Windows.
Ubuntu does let you install in UEFI boot mode to MBR drive and should not.

Microsoft has required vendors to install in UEFI mode to gpt partitioned drives since Windows 8 released in 2012.
So most hardware is now UEFI.

---

### Post by Macamba on 2020-10-20
> **tea for one said:**
> Your boot-repair report is revealing some details, which probably explains your dilemma:-

[COLOR="#0000FF"]Lines 119 - 121[/COLOR]       3 operating systems
[COLOR="#0000FF"]Lines 152 - 153 [/COLOR]      2 drives with mixed partition tables and only sdb contains EFI system partition (esp)
[COLOR="#0000FF"]Line 397[/COLOR]                  Windows in Legacy mode, yet PC boots in EFI mode

<SNIP>

Worth considering?

I only need one Ubuntu and one Windows. Can I **remove Ubuntu 18.04.5 LTS on sda4**? Is it possible to get the Ubuntu installation back to the **legacy** situation? 

To be able to backup Windows I need to have access to Windows. And that I not have. 

I need to go back to the situation where I had a Ubuntu on one HD, and Windows on the other one. That worked before October 6th. Is that feasible?

---

### Post by tea for one on 2020-10-20
Your Windows OS is on sdb therefore why not de-activate/remove sda (rather than deleting anything yet) and see if it boots?

---

### Post by oldfred on 2020-10-20
Run Boot-Repair in advanced mode. And reinstall grub to sda and Windows type (syslinux) boot loader to sdb. Usually better to use Windows repair flash drive to make Windows fixes, but if Windows not hibernated Boot-Repair may offer to fix it.
The other issue is boot flag. Windows requires boot flag on its primary partition with boot files, your sdb1. But UEFI requires boot flag on ESP, so Ubuntu install moved boot flag to sdb7. 
Another user with similar issue seemed to have boot flag moved back with Boot-Repair's fix. If not use gparted and move boot flag.

If you choose the install in sdb, but install that grub to sda's MBR, you will be able to boot everything in BIOS mode.
But still better to totally convert to UEFI.

---

### Post by tea for one on 2020-10-20
> **Macamba said:**
> To be able to backup Windows I need to have access to Windows. And that I not have. 

You can backup your Windows data via a [COLOR="#0000FF"]live[/COLOR] Ubuntu session.

---

### Post by Macamba on 2020-10-21
> **tea for one said:**
> You can backup your Windows data via a [COLOR="#0000FF"]live[/COLOR] Ubuntu session.

You are right. After writing my question I tried it and succeeded. But besides data (all probably in the 'My Documents' directory (eg. in /media/ubuntu/Windows 10/Users/macamba/Documents :)). But it is not the documents I need to keep safe, it is also the configuration (Java Development, SQL server and what not) that will be lost when I reinstall Windows to cope with UEFI. And my system worked before when it used legacy. So I would prefer to get back to that situation. In the long term I will probably step over with a new system.

---

### Post by tea for one on 2020-10-21
It seems that your Windows data is more important than anything at the moment (even more important than protecting Ubuntu and your data within Ubuntu).

I don't know where Java Development, SQL server  etc is stored in Windows so I cannot offer any help with backing up that data/configuration.

I imagine re-installing a Windows bootloader in Legacy mode may well interfere with Ubuntu in EFI mode.

Some more suggestions:-

Back up your Ubuntu data (if it is important).
Seek advice in a Windows forum about completely removing Ubuntu and restoring a Windows bootloader in Legacy mode.
Once Windows is working OK for you - use Windows tools to back up everything you need.
Reinstall Windows and Ubuntu on separate drives in EFI mode when you are ready.
Restore your backups.

Possibly, other forum members with experience of Windows bootloaders may jump in and offer advice.

---

### Post by oldfred on 2020-10-21
Did you try fixes in #24?

What if hard drive fails tomorrow?
You need to know where your development data so you can back that up also.
Years ago with Windows, I separated system c: from data d: 
But that started with DOS as you booted with one floppy A: and removed it to put in your data floppy B: as you only had one floppy drive.

---

### Post by Macamba on 2020-10-22
FWIW, I will be reinstalling Windows, now on UEFI. But first I am hoping on a successful Ubuntu installation with a 200 Mb UEFI partition, which worked before.and I will be backing up data, just for in case. Fingers crossed.

Edit: ***_Nope_***

---

### Post by Macamba on 2020-10-22
I got an 'Installation complete' message after installation. But after reboot I got after 'Verifying DMI Pool Data .....'
```
error: No such device: 4a8ddd8d-09fd-4394-8f24-4631dc80ea19
Entering rescue mode ...
grub rescue>
```

I would like to have a working system (not running Life DVD). Would anyone know what options I have now? Here is a new 'boot-repair' file:

[https://paste.ubuntu.com/p/G2vSK73vgR/](https://paste.ubuntu.com/p/G2vSK73vgR/)

Edit: Looking at the boot-repair file I see (what was already noticed earlier):
```
OS#1:   Ubuntu 20.04.1 LTS on sda4
OS#2:   Ubuntu 20.04.1 LTS on sdb8
OS#3:   Windows 8 or 10 on sdb1
```

I changed /dev/sdb7 (efi) and /dev/sdb8 (ext4 with Ubuntu 20.04 LTS (20.04):
[https://ibb.co/NgvnwGQ]("https://ibb.co/NgvnwGQ")

into /dev/sdb7 (fat32)
[https://ibb.co/cyH03FC]("https://ibb.co/cyH03FC")

Hopefully, when everything is up and running again I can change fat 32 under Windows into ntfs and use this new found space for whatever takes my fancy. I did not assign a mount point (/windows was suggested).

Fingers crossed.

---

### Post by Macamba on 2020-10-22
Nope, again. I got the same error:
```
error: No such device: 4a8ddd8d-09fd-4394-8f24-4631dc80ea19
Entering rescue mode ...
grub rescue>
```

Accompanying pastebin: [https://paste.ubuntu.com/p/gBk6Hn8m2P/](https://paste.ubuntu.com/p/gBk6Hn8m2P/)

But now with only 2 OS'es:
```
================================ 2 OS detected =================================

OS#1:   Ubuntu 20.04.1 LTS on sda4
OS#2:   Windows 8 or 10 on sdb1
```

With the newly created sdb7:
```
sdb7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:   
```

I now will try a reinstall, not with UEFI, but with a 1 MB biosgrub.

**Warning!** "No EFI SYstem Partition was found". That is new. In a previous step I removed an EFI partition on the Windows HD. Continue anyway.
[https://ibb.co/QfmzK2Y]("https://ibb.co/QfmzK2Y")

---

### Post by oldfred on 2020-10-22
This is correct as that was your old install partition. And that means you are trying to boot with the old grub in the MBR, not new UEFI grub in UEFI.
> error: No such device: 4a8ddd8d-09fd-4394-8f24-4631dc80ea19

While you have what looks like a UEFI install, it seems to be missing the UEFI boot entry.

This says you booted live installer in BIOS/CSM/Legacy boot mode.
> While you have what looks like a UEFI install, it seems to be missing the UEFI boot entry.

Reboot in UEFI mode and reinstall grub. It will not add Windows to grub menu as UEFI & BIOS are not compatible. Or once you start booting in one mode, you cannot switch.
You are missing UEFI boot entry:
See line 137. Or this. 
sudo efibootmgr -v

To boot Windows you have to install a BIOS boot loader to sdb, it now has grub will will  not work.
Either syslinux or use your Windows repair flash drive and fixMBR.

---

### Post by Macamba on 2020-10-22
> **oldfred said:**
> Reboot in UEFI mode and reinstall grub. It will not add Windows to grub menu as UEFI & BIOS are not compatible. Or once you start booting in one mode, you cannot switch.
You are missing UEFI boot entry:
See line 137. Or this. 
sudo efibootmgr -v

To boot Windows you have to install a BIOS boot loader to sdb, it now has grub will will  not work.
Either syslinux or use your Windows repair flash drive and fixMBR.

My latest pastebin: [https://paste.ubuntu.com/p/k75Y9Pfkp3/](https://paste.ubuntu.com/p/k75Y9Pfkp3/)

I hoped on better times, with the biosboot partition. But sad to say (again), no :-{. 

Use suggest syslinux? Like 
```
syslinux --install /dev/sdb
```
(partly from man page)

Or otherwise l need to find out how to make a "Windows repair flash drive". The pages I find use a running Windows system, which I lack at the moment.

*Sigh*

---

### Post by tea for one on 2020-10-22
From your latest boot-repair report in post 33:-

[COLOR="#0000FF"]Line 141[/COLOR] sdb is not GPT

Widows in EFI mode requires GPT.

Suggestion:-

Remove drive sda completely from you PC
Use a live Ubuntu session to create GPT on your drive where you wish to install Windows
Install Windows only on this drive
Verify Windows boots successfully
Restore your backup

When this is OK, please post back here and we can try to help with your Ubuntu drive (originally sda)

---

### Post by oldfred on 2020-10-22
Only because you have two drives, You can have one drive UEFI/gpt and the other BIOS/MBR. Some older UEFI required you to change settings so it knew which way to boot the drive you wanted to boot from. Most UEFI now know and let you choose which to boot and it works. But you have to choose from UEFI boot menu.

Boot-Repairs's advanced mode may install syslinux for you. You have to choose your install (Windows) and drive for boot loader, sdb. But if Windows is hibernated or fast start up on, then Boot-Repair may not see it.

Install my have syslinux.
sudo apt-get install syslinux
Not sure which path is correct, it may depend on version of Ubuntu or Linux.
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
sudo dd if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sdb

---

### Post by Macamba on 2020-11-04
Some time has past. But I finally succeeded in booting my Windows, after disconnecting my Linux HD. Working with your counterpart from the Microsoft forums I found out I actually "may not have a UEFI capable BIOS . . . ". So can I install Ubuntu without it writing UEFI to my HD's?

---

### Post by oldfred on 2020-11-04
Your trusty Microsoft source says your system may not be UEFI capable?
Boot-Repair said this:
> BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.


Repeating myself several times after reviewing previous posts.
Microsoft has required vendors to install Windows in UEFI/gpt boot mode since Windows 8 released in 2012. So most hardware is UEFI.
And how you boot install media, UEFI or BIOS is then how it installs.
Microsoft only installs in UEFI mode to gpt partitioned drives.

---

### Post by tea for one on 2020-11-04
> **oldfred said:**
> trusty Microsoft source

Touché [COLOR="#0000FF"]oldfred[/COLOR] - Best oxymoron of the day. ;)

---

### Post by Macamba on 2020-11-04
> **oldfred said:**
> Your trusty Microsoft source says your system may not be UEFI capable?
Boot-Repair said this:


Repeating myself several times after reviewing previous posts.
Microsoft has required vendors to install Windows in UEFI/gpt boot mode since Windows 8 released in 2012. So most hardware is UEFI.
And how you boot install media, UEFI or BIOS is then how it installs.
Microsoft only installs in UEFI mode to gpt partitioned drives.

During my forum session at Microsoft I had to offer a picture of my BIOS Security Tab. I had none.
[https://ibb.co/BGrx3D6](https://ibb.co/BGrx3D6)

Next I was asked to provide him with a picture of my System Information.
[https://ibb.co/SrfCSMg](https://ibb.co/SrfCSMg)

On seeing this picture he concluded "that Secure Boot is not supported on your motherboard, so therefore you cannot switch to UEIF, may I ask why were you going to switch to UEFI"

@oldFred: You say "So most hardware is UEFI." Might my BIOS not support UEFI despite what Boot-Repair said?

---

### Post by CelticWarrior on 2020-11-04
> **Macamba said:**
> Might my BIOS not support UEFI despite what Boot-Repair said?

No, period. It is, sadly, a very early implementation (yes, old) that looks indistinguishable for the old BIOS at first glance. But the bare minimum features are there under Advanced BIOS features > [https://download.gigabyte.com/FileList/Manual/mb_manual_ga-78lmt-usb3_v.6.0_e_04.pdf](https://download.gigabyte.com/FileList/Manual/mb_manual_ga-78lmt-usb3_v.6.0_e_04.pdf) pages 23-24 mention "EFI boot" and that settles the matter. Pay special attention to the "Hard Disk Boot Priority" where, if more than one disk, the first in order should always be the one containing the ESP (EFI System Partition irrespective of where the OSes are installed. 

> [COLOR=#000000]On seeing this picture he concluded "that Secure Boot is not supported on your motherboard, so therefore you cannot switch to UEIF, may I ask why were you going to switch to UEFI"[/COLOR]
And this tells us a lot about the "support". I guess he missed the part about "BIOS mode: Legacy" that automatically implies Secure Boot unsupported. The system information page reports how it was installed only (legacy).

---

### Post by oldfred on 2020-11-04
Specs says hybrid EFI type BIOS.
Vendors still call UEFI as BIOS.
[https://www.gigabyte.com/Motherboard/GA-78LMT-USB3-rev-41#ov](https://www.gigabyte.com/Motherboard/GA-78LMT-USB3-rev-41#ov)

So early UEFI.
Vendors, Microsoft & Linux developers all had to make many updates to have UEFI work well with those early versions. Some worked better than others.
And then some users just stayed with BIOS boot. 
But you have to be consistent on how you boot as that is how both Windows & Ubuntu install or repair system.
If you want BIOS always boot in BIOS mode.

---

### Post by Macamba on 2020-11-05
Now I can dive into this, buy me an external HD to back up my Windows HD (do I also backup the Linux HD). This costs money, and caries the risk of failure, or I can go back to the situation I had before, both Windows and Linux using Legacy BIOS. I have not seen an answer on that request.

---

### Post by CelticWarrior on 2020-11-05
> **Macamba said:**
> Now I can dive into this, buy me an external HD to back up my Windows HD (do I also backup the Linux HD). This costs money, and caries the risk of failure, or I can go back to the situation I had before, both Windows and Linux using Legacy BIOS. I have not seen an answer on that request.

Yes, you did, many...

> [COLOR=#000000][INDENT]If you want BIOS always boot in BIOS mode.[/INDENT]
[/COLOR]


---

