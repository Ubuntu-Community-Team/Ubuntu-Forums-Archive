---
title: "Cannot boot into Ubuntu- No ubuntu/Windows Menu selection"
date: 2013-01-06
forum: General Help
---

### Post by fergie716 on 2013-01-06
Hey guys and gals, I recently tried to downgrade from Ubuntu 12.10 to Ubuntu 12.04 however I ran into a major issue

I initially booted into a Live CD of 12.04, formated my original 12.10 partition and installed 12.04 onto that partition.  Towards the end of installation I got an error saying the grub could not be installed to target and the system was not installed

I went back and forth trying a few fixes and could not come up with anything.  I ended up installing 12.10 onto that same partition via Live USB and it installed successfully.  At the end of installation the installer prompted me to restart my computer. I did so and ended up at the black Ubuntu selection menu (the menu that only has the installation options such as Try Ubuntu, Install Ubuntu, OEM Install etc)

I tried shutting down my computer after installation, removing the USB and restarting but then I end up at the grub rescue> menu.  So I booted into a Live USB again and ran boot repair. Boot repair says it fixed my problem BUT it also says:

 

Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

After running Boot Repair I tried just rebooting (didn't work) and I also tried shutting off my computer and changing my boot list in BIOS to have it start with my hard drive, that didn't work either

So I am absolutely stuck.  I had a previous thread requesting help on downgrading from 12.10 to 12.04 and I received some awesome help, that thread can be found [here]("http://ubuntuforums.org/showthread.php?t=2101899")

Here is a pic of my partitions before attempting the downgrade:  [http://imgur.com/TOIUg](http://imgur.com/TOIUg)

Here is a pic of my partitions now while on the Live USB of 12.10:  [http://imgur.com/fUQ5I](http://imgur.com/fUQ5I)


Here is my latest log from my latest Boot Repair:  [http://paste.ubuntu.com/1502030/](http://paste.ubuntu.com/1502030/)


I have a Toshiba Laptop with Windows 8 (came pre installed).  Initial installation of Ubuntu 12.10 went fine with no issues a few days ago

If anyone could help me I would greatly greatly appreciate it, I will be up for a few more hours.  But I am really nervous and frustrated and would really appreciate it if someone could please help

Thank you

---

### Post by fergie716 on 2013-01-06
Anyone out there who could possibly help me? I'm willing pay someone that can guide me through a fix or just has some ideas lol

---

### Post by fergie716 on 2013-01-06
In case anyone is reading this I ran boot repair again, here is the log

[http://paste.ubuntu.com/1504497/](http://paste.ubuntu.com/1504497/)

Also, I got the same thing:

Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

---

### Post by fergie716 on 2013-01-06
Hey community, some great news.  I was able to boot into my installed 12.10 however I still cannot get into my system without having my BIOS select to boot from my USB stick first.  Here's what I have to do:

-Make sure BIOS is set to start up with USB
-At Ubuntu installation menu from USB press 'c' on keyboard
-Type 'exit' from command line
-Asked what I want to load from BIOS Menu (USB, Hard Drive)
-Select Hard Drive
-My Options are then 'grub', 'ubuntu', 'Windows Boot Manager'
-Select 'ubuntu'
-This takes me to the traditional grub menu (purple background)
-Select 'Ubuntu' from the tradtional grub menu

I haven't tried to access Windows, don't wanna press my luck lol.  But if anyone has any additonal input on how I can just get to the traditional purple grub menu without using the command line from the Live USB menu that would be great.  

I tried to select my hard drive as #1 in BIOS but after I reboot I just get the grub rescue menu

Any help?  Thanks!

---

### Post by oldfred on 2013-01-06
Those entries look more like a UEFI menu not the USB? Or maybe some combination somehow?

I have not seen grub rescue from UEFI entries.

Without flash drive plugged in and going into UEFI menu can you boot either Windows or ubuntu entry directly?

Boot script looks normal, so I am not seeing anything specific perhaps someone else will. Although you seem to have a new uefi firmware entry which I have not seen before. There is/was a bug on that issue.

---

### Post by fergie716 on 2013-01-06
> **oldfred said:**
> Those entries look more like a UEFI menu not the USB? Or maybe some combination somehow?

I have not seen grub rescue from UEFI entries.

Without flash drive plugged in and going into UEFI menu can you boot either Windows or ubuntu entry directly?

Boot script looks normal, so I am not seeing anything specific perhaps someone else will. Although you seem to have a new uefi firmware entry which I have not seen before. There is/was a bug on that issue.
Thanks for responding!

Unfortunately when I reboot or shut off the computer and turn it back on it goes to the grub rescue menu.  If I go into BIOS and select my hard drive as #1 in the boot order and reboot it goes back to the same grub rescue menu

The only way I can load into Ubuntu is by taking the steps above.  When I get home I can take pictures of what each menu looks like?

---

### Post by oldfred on 2013-01-07
If booting from USB are you booting in BIOS mode or UEFI mode? UEFI menu or even one time boot key should give both options from UEFI/BIOS.

I might try Boot-Repair again.

From UEFI/BIOS does the Windows entry work?

---

### Post by fergie716 on 2013-01-07
When booting from the USB I get to that installation selection menu where it asks if I want to try Ubuntu or Install it etc

I press 'c' then in the command line type 'exit' 

After that I come to this menu

[http://imgur.com/BwkYT](http://imgur.com/BwkYT)

In the pic I already selected option 2, then I select 'ubuntu'

After that it takes me to the purple grub menu that came with 12.10, however this is the only way I can access Ubuntu lol.. I'll try selecting a Windows option next.   I'm sorry I'm not too sure on the names of these menus lol so I'll post more pics if they are helpful

Thanks again for helping, should I run boot repair from a Live USB or from my installed system?

---

### Post by Calinou on 2013-01-07
Why do you want to downgrade in the first place? The software in the 12.10 repositories is more up-to-date and the LTS is getting old already.

---

### Post by oldfred on 2013-01-07
That looks like a UEFI menu. But once you have selected Ubuntu (or Windows) it should just use that entry again until you change it.

Does Windows work from that entry. We have seen some UEFI's that will only boot Windows entry, and boot repair can rename grub/ubuntu's file to the Windows files and backup the Windows files. Then you boot Windows from UEFI menu and get grub. And then grub chain loads to the backup Windows efi file to boot Windows. A bit of a work around but the UEFI should let you boot other systems.

---

### Post by fergie716 on 2013-01-10
Hey sorry it took me a bit to get back, finished up my last semester at school

Yes, I can access Windows with no issues but I have to do the same workaround (have BIOS set to boot from USB, select to load from HD, select Ubuntu then select Windows UEFI loader)

---

### Post by fergie716 on 2013-01-10
Here is my theory:  When I first installed Ubuntu (1st time ever) I set up a swap partition and a "/" root partition (ended up being sda7)

I think Windows boot is set at sda2 (look @ my pics in OP) but grub was initially set to load from sda7.  

Somehow that got messed up and set to load from sda2, that's why whenever I run boot repair it always says:

Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

But in conclusion I can load Ubuntu and Windows but I need BIOS boot order set to load USB first, then use the workaround I explained earlier

Anyone possibly know how to fix this?  Doing some Googling now

Thanks!

---

### Post by oldfred on 2013-01-10
With UEFI boot all installed systems install boot files into the efi partition, not any other partition. 
UEFI is supposed to show all bootable systems. But many UEFI are not implemented correctly it seems.

Best to backup efi partition before anymore changes.

       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)> 
So this time I installed 12.10, then I booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

       
 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

 UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

---

### Post by fergie716 on 2013-01-11
Hmmm I tried a few boot-repair options as described in those threads but I did not try this

> So this time I installed 12.10, then I booted again from liveCD, made  backup of (efi part)/EFI/microsoft/boot and copied all files from  /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to  bootmgfw.efi. And it works


What do you think is the worse thing that could happen if I did this lol.. Because I recently did a search for some of those efi files and I seem to have duplicates of a lot of them

But this is the only fix I haven't tried, just worried if I do it I will ruin something lol..

---

### Post by oldfred on 2013-01-12
That is why you do a backup first of efi partition. 

Boot-Repair has its own process of copying files and renaming with additional endings to keep track of which is which. See links above on explanation of Boot-Repair.

       Boot files normally mounted at /efi/Boot:
# for grub/ubuntu
 /efi/ubuntu/grubx64.efi
# New secure boot grub version:
/efi/ubuntu/ shimx64.efi.
# for Windows, but for UEFI systems that only boot this file, grub or shim may get renamed to this and this backed up.
/EFI/Microsoft/Boot/bootmgfw.efi
# Both Windows & Ubuntu may provide this shell file, not sure of differeneces.
 /efi/Boot/bootx64.efi

    There also may be other files in each directory to support booting.

---

### Post by fergie716 on 2013-01-12
> **oldfred said:**
> That is why you do a backup first of efi partition. 

Boot-Repair has its own process of copying files and renaming with additional endings to keep track of which is which. See links above on explanation of Boot-Repair.

       Boot files normally mounted at /efi/Boot:
# for grub/ubuntu
 /efi/ubuntu/grubx64.efi
# New secure boot grub version:
/efi/ubuntu/ shimx64.efi.
# for Windows, but for UEFI systems that only boot this file, grub or shim may get renamed to this and this backed up.
/EFI/Microsoft/Boot/bootmgfw.efi
# Both Windows & Ubuntu may provide this shell file, not sure of differeneces.
 /efi/Boot/bootx64.efi

    There also may be other files in each directory to support booting.
Yea I think there's a few files that support the boot

So I am really nervous to do the renaming thing, IDK where I would backup those files to (cloud storage OK?).  Anyway I took a few screen shots of /boot

Here are the pics:  [http://imgur.com/a/WuKvD](http://imgur.com/a/WuKvD)

According to the error I am getting in boot-repair, it says to make sure BIOS is set to boot off of sda2/EFI/ubuntu/grubx64.efi

If you would be so kind as to look at those pics real quick and see which ones I need to rename and where they go?  I know my problem is similar to the person who had the Sony but I just wanna make sure I get this right 

Thank you so much

---

### Post by oldfred on 2013-01-12
You did not post Microsoft nor Toshiba. 

I think all the Microsoft files were in Boot, but it may have files in both or one is to boot Windows recovery/repair only? I assume the Toshiba will have files to boot the Toshiba recovery.

The only file to rename is 
       /EFI/Microsoft/Boot/bootmgfw.efi
    
You may have to copy the grub or shim efi file into the Windows or Boot partition, rename the Windows boot file to bootmgrw.efi.backup and rename either the shim or grub to bootmgrw.efi. I think the shim is required if you want to turn secure boot back on, otherwise grub may work. Not sure.

Entire efi partition should be tiny. You can copy to CD or flash drive.

---

### Post by fergie716 on 2013-01-12
> **oldfred said:**
> You did not post Microsoft nor Toshiba. 

I think all the Microsoft files were in Boot, but it may have files in both or one is to boot Windows recovery/repair only? I assume the Toshiba will have files to boot the Toshiba recovery.

The only file to rename is 
       /EFI/Microsoft/Boot/bootmgfw.efi
    
You may have to copy the grub or shim efi file into the Windows or Boot partition, rename the Windows boot file to bootmgrw.efi.backup and rename either the shim or grub to bootmgrw.efi. I think the shim is required if you want to turn secure boot back on, otherwise grub may work. Not sure.

Entire efi partition should be tiny. You can copy to CD or flash drive.
Toshiba and Microsoft were in those pics.. Here are direct links in case something went wrong

Microsoft: [http://i.imgur.com/wFf9Nh.png](http://i.imgur.com/wFf9Nh.png)

Toshiba:  [http://i.imgur.com/LbNrvh.png](http://i.imgur.com/LbNrvh.png)


OK I'll do some testing and see which combo works

I also checked the properties of each ".efi" file in /boot to see which one loads which.. Remember how I have to have my BIOS set to load a USB or DVD first at boot?  Then press"c", then "exit" at the GRUB GNU (black screen) then enter that other boot menu to select my hard drive then load from ubuntu.

Well, after looking at which ".efi" loads when here is what I saw:

-/boot/efi/EFI/ubuntu/grubx64.efi >> loads first

-/boot/efi/EFI/Boot/bootx64.efi and /boot/efi/EFI/Microsoft/boot/bootmgfw.efi (and bootmgr.efi) both load next at the same time

-/boot/efi/EFI/grub/grubx64.efi loads next

-/boot/efi/EFI/toshiba/Boot/boot.mgfw.efi (and bootmgr.efi) load last and this is (I'm assuming) the menu at which I select ubuntu (I posted a pic of this menu a few posts back)

Just thought I'd post these if they are important at all 

Thanks for sticking it out with me lol really appreciate it.  Almost there!

---

### Post by oldfred on 2013-01-12
Since they were both in /boot under the main, I missed the difference.

I expect the bootmgfw in Toshiba has a related BCD that then just loads the recovery mode partition to restore the system.

If you can set ubuntu to be first or grubx64.efi (or shim file?) as first in the UEFI menu, it should boot ubuntu first everytime.

---

### Post by fergie716 on 2013-01-16
Ran Boot-Repair via Live CD with the "backup and rename efi files" option ticked

Same results as before (error: file not found) followed by grub rescue>

Here is my latest boot info from the repair

[http://paste.ubuntu.com/1539690/](http://paste.ubuntu.com/1539690/)

Thanks

---

### Post by oldfred on 2013-01-16
Are you booting from UEFI menu the ubuntu entry as Boot-Repair says?

lease do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

---

### Post by fergie716 on 2013-01-16
Do you mean when I reboot after running boot-repair?  Because after running boot repair and restarting I take out my CD then end up at the grub rescue menu

There is no option in my BIOS to boot on sda2/EFI/ubuntu/grubx64.efi, there are only the 4 normal options:

-CD
-Hard drive
-USB
-LAN

---

### Post by oldfred on 2013-01-17
Are you in UEFI mode or BIOS mode?

Do you have more settings under the hard drive setting?

Normally UEFI has all options at the same level not in sub menus.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by fergie716 on 2013-01-18
> **oldfred said:**
> Are you in UEFI mode or BIOS mode?

Do you have more settings under the hard drive setting?

Normally UEFI has all options at the same level not in sub menus.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
I guess that would be BIOS mode

But I found this interesting, I was in Windows 8 and went to the UEFI Advanced Startup section, when it rebooted I went to the Select Device Option and this came up:

[http://i.imgur.com/sE4TDdu.jpg](http://i.imgur.com/sE4TDdu.jpg)

The grub selection goes to the 
"file not found
grub rescue" prompt

The Ubuntu selection does take me to the correct menu selection  menu I need to start up from the get go (it has a purple background, full screen, has options to load Ubuntu as well as Windows 8 and both selections work)

So I guess it's interesting but still have no idea how to get it to work at boot

---

### Post by oldfred on 2013-01-19
Each system is a bit different even though UEFI is a standard. But most seem to have a fast boot setting that skips UEFI, then you only can get back to UEFI from Windows. And if Windows is broken you brick system. (perhaps UEFI/BIOS reinstall/updatge fixes it but we do not know).

So we suggest you turn off fast boot in UEFI  and from UEFI not Windows boot ubuntu. then it should be the default not Windows.

Also good idea to have liveCD or repairCD  or flash for current version of every system installed.
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by fergie716 on 2013-01-19
> **oldfred said:**
> Each system is a bit different even though UEFI is a standard. But most seem to have a fast boot setting that skips UEFI, then you only can get back to UEFI from Windows. And if Windows is broken you brick system. (perhaps UEFI/BIOS reinstall/updatge fixes it but we do not know).

So we suggest you turn off fast boot in UEFI  and from UEFI not Windows boot ubuntu. then it should be the default not Windows.

Also good idea to have liveCD or repairCD  or flash for current version of every system installed.
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)


Thanks for the links. I made a W8 recovery disk a few days ago and it didn't really work.  It will try to load but never does then just stops.  But if I get back into windows (following the steps outlined below) it takes me to a command prompt that I can exit and enter W8

Anyway, still have the same issue lol.  Can boot into W8 and Ubuntu 12.10 no issues but I have to have my boot order set to load a disk first (and it has to be an Ubuntu disk in the drive) then press "c" then "exit" to get into the  system selection menu

I've followed many guides on how to load the system frm grub rescue (which will pop up if i dont have the CD in) and to some extent it works, it will load Ubuntu if I'm at a regular grub menu and do the set prefix= and insmod normal command sequence  (doesnt work from grub rescue)


This whole thing is just confusing lol

---

### Post by oldfred on 2013-01-20
We see that fairly often with BIOS as users may install grub to flash drive or system promotes flash to sda and grub auto installs to sda which is then not the internal hard drive.

Not seen issue with UEFI. Perhaps a grub reinstall from inside your Ubuntu install?

Post link to a new BootInfo report.

With BIOS these commands would reinstall grub.

Post this as I am curious if UEFI shows the same info as a BIOS install.
       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    
The install choice with UEFI should only be the efi partition and some have reported whatever they choose, it still knows it is UEFI and installs grub to the efi partition correctly on a new install. This is a reinstall and supposedly works the same as the original install, but have not seen anyone do it with UEFI yet.
       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by fergie716 on 2013-01-20
> **oldfred said:**
> We see that fairly often with BIOS as users may install grub to flash drive or system promotes flash to sda and grub auto installs to sda which is then not the internal hard drive.

Not seen issue with UEFI. Perhaps a grub reinstall from inside your Ubuntu install?

Post link to a new BootInfo report.

With BIOS these commands would reinstall grub.

Post this as I am curious if UEFI shows the same info as a BIOS install.
       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    
The install choice with UEFI should only be the efi partition and some have reported whatever they choose, it still knows it is UEFI and installs grub to the efi partition correctly on a new install. This is a reinstall and supposedly works the same as the original install, but have not seen anyone do it with UEFI yet.
       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
OK cool thanks again for your help!  Appreciate it very much

Here is the report of a boot repair I did the other night from a Live CD

[http://paste.ubuntu.com/1547330/](http://paste.ubuntu.com/1547330/)


I'll boot up and try those commands from inside my system and report back

---

### Post by fergie716 on 2013-01-20
Here are my results from "sudo debconf-show grub-pc"

```
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
  grub-pc/install_devices:
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10
```


Results of this command: "sudo grub-probe -t device /boot/grub"

```
/dev/sda7
```

Which is the partition I initially installed Ubuntu on.  This is where it gets confusing, here is a pic of my partitions

[http://i.imgur.com/PtQxvNo.png](http://i.imgur.com/PtQxvNo.png)


sd1- I'm not sure what that is, came with Windows 
sda2- Says its mounted at /boot/efi
sda3- Not sure
sda4- Main Windows 8 partition
sda7- Ubuntu partition
sda5- Recovery

---

### Post by oldfred on 2013-01-20
I have BIOS not UEFI, but your install is blank. Maybe that is how it is with UEFI?
This is mine:
> grub-pc/install_devices: /dev/disk/by-id/ata-FUJITSU_MHV2160BT_PL_NY07T6A28HNP

You somehow got a Windows boot loader in the protective MBR. That is not really used with UEFI except to tell old system tools that the drive is gpt partitioned and do not mess with it.

Your sda1 is a Windows repair partition, sda2 is efi, sda3 is the Windows MSR which Windows has to have to hidden stuff like digital rights serial numbers.

line 917 Boot0004* ubuntu
BootOrder: 0004,2002,0005,0003,2003,2001

That says your should be booting Ubuntu since it is 0004.

What I still do not understand is the first boot order and why you have two? Or is one BIOS and the other UEFI?
 line 906 
BootOrder: 2002,0005,0003,2003,2001
Boot0002* EFI Network 0 for IPv4 (00-8C-FA-24-81-A0)
So that is set for network boot.

Review your UEFI settings to see what it is really saying.

---

### Post by fergie716 on 2013-01-21
> **oldfred said:**
> I have BIOS not UEFI, but your install is blank. Maybe that is how it is with UEFI?
This is mine:


You somehow got a Windows boot loader in the protective MBR. That is not really used with UEFI except to tell old system tools that the drive is gpt partitioned and do not mess with it.

Your sda1 is a Windows repair partition, sda2 is efi, sda3 is the Windows MSR which Windows has to have to hidden stuff like digital rights serial numbers.

line 917 Boot0004* ubuntu
BootOrder: 0004,2002,0005,0003,2003,2001

That says your should be booting Ubuntu since it is 0004.

What I still do not understand is the first boot order and why you have two? Or is one BIOS and the other UEFI?
 line 906 
BootOrder: 2002,0005,0003,2003,2001
Boot0002* EFI Network 0 for IPv4 (00-8C-FA-24-81-A0)
So that is set for network boot.

Review your UEFI settings to see what it is really saying.

Oh cool thanks for the explanation on the partitions. Yea in my BIOS settings DVD is set to boot first, then hard drive, then USB and the IPv6 

If I go into the UEFI settings from Windows (Advanced Start up Menu) there's no real order, just given options. But it goes DVD, grub, Ubuntu, USB, IPv6

---

### Post by oldfred on 2013-01-21
If you go directly into UEFI menu, not thru Windows and set ubuntu as boot device does not not keep booting Ubuntu?
Is fast boot off?

---

### Post by fergie716 on 2013-01-21
> **oldfred said:**
> If you go directly into UEFI menu, not thru Windows and set ubuntu as boot device does not not keep booting Ubuntu?
Is fast boot off?
I don't get any options in BIOS for Ubuntu, if I go straight there my options are Hard drive, CD, USB, IPv6

The only time I can access Ubuntu/Windows are under these conditions:

1) Have BIOS/UEFI set to Boot from DVD (I press F2 while computer is starting up to access this and change Boot Order (there is NO boot menu at this point))

2) Once the DVD Loads (12.10) I get to that black screen where it asks if I want to "Try Ubuntu", "Install Ubuntu 12.10", "Check Disk For Errors", etc

3) I press "c" which takes me to the grub command prompt window (not grub rescue, regular grub>

4) Once in the command prompt I type "exit"

5) After I type "exit" I get sent to this menu

[http://imgur.com/BwkYT](http://imgur.com/BwkYT)

6) Like in the pic, at this menu I select my Hard Drive, then those three options come up. The grub option takes me to "file not found:  grub rescue>" menu.  The Ubuntu selection takes me to the proper grub menu that has options to load Ubuntu 12.10 OR Windows 8.  I have other selection options but I can access both Ubuntu and W8

So that's where I'm at.  According to that pic "grub" is the 1st option but it's that grub rescue menu.  I need that "ubuntu" option to be 1st so I can get to that proper grub menu (the one with Ubuntu and Windows 8 selection options)

---

### Post by fergie716 on 2013-01-21
Actually I just found out I can hold F12 at boot to access that Boot Menu from startup

---

### Post by oldfred on 2013-01-21
If you select Ubuntu does that not boot ubuntu as default?

---

### Post by fergie716 on 2013-01-21
> **oldfred said:**
> If you select Ubuntu does that not boot ubuntu as default?
Not at default, I have to press F12 at boot now. But I don't have to load from DVD. So I changed my boot order from DVD to Hard Drive. Just gotta hold F12 to enter that Boot Menu. Butif I reboot or turn  it off then back on I end up at the grub rescue menu again

---

### Post by fergie716 on 2013-01-21
Kinda found this interesting 

I have multiple grub folders

If I type "set" frm grub rescue my prefix is 

(hd0,gpt7)/boot/grub gpt7 is the partition my Ubuntu system is on

However I have a grub folder on (hd0,gpt2)/grub

See the pic

[http://i.imgur.com/E95p3UU.png](http://i.imgur.com/E95p3UU.png)

Could this mean anything?  I knw whenever I run boot repair I have to keep that option checked in GRUB location "Separate /boot/efi partition on sda2"

---

### Post by oldfred on 2013-01-21
Boot files to start booting are in the efi partition, the rest of grub is the /boot folder or if you have a separate /boot partition then in that partition. Grub also has configuration files in several places in the Ubuntu system.

The boot files in the efi partition are the new version of what used to be in the MBR in BIOS based systems. But now with UEFI all systems can install boot files into the efi partition. It is like having many MBRs to boot from.

Typically f12 is a one time boot key to let you boot your DVD or flash just this time. Handy so you do not have to go into UEFI/BIOS to change boot order. And you can keep hard drive ubuntu entry as first in boot order so system does not have to look at other devices and not find them. Than can slow boot.

---

### Post by fergie716 on 2013-01-21
> **oldfred said:**
> Boot files to start booting are in the efi partition, the rest of grub is the /boot folder or if you have a separate /boot partition then in that partition. Grub also has configuration files in several places in the Ubuntu system.

The boot files in the efi partition are the new version of what used to be in the MBR in BIOS based systems. But now with UEFI all systems can install boot files into the efi partition. It is like having many MBRs to boot from.

Typically f12 is a one time boot key to let you boot your DVD or flash just this time. Handy so you do not have to go into UEFI/BIOS to change boot order. And you can keep hard drive ubuntu entry as first in boot order so system does not have to look at other devices and not find them. Than can slow boot.
So.. What do you think I should do?  I guess this is semi solved lol.  I can access both W8 and Ubuntu albeit not the usual way 

The more and more I Google and try things out I think two things are going on:

- I have multiple versions of GRUB installed, one at /dev/sda7 (main Ubuntu partition) and another on /dev/sda2 (UEFI/Boot Partition).  This is causing some issues somewhere

- My set prefix= is off, maybe it should be (hd0,gpt2)=/grub?

---

### Post by fergie716 on 2013-01-21
So I booted into Windows 8 and installed Easy BCD just to see what it would say.  Interestingly enough it gave me some valuable info.

The first entry I have for starting up my computer is a version of grub, which is either currupt, the wrong version or something.  But it's loading from /dev/sda2/EFI/grub/grubx64.efi

The second entry is Ubuntu but that's really the correct grub menu I should be getting and that's loading from /dev/sda2/EFI/ubuntu/grubx64.efi

Here are some screenshots 

[http://i.imgur.com/nvMFSrc.png](http://i.imgur.com/nvMFSrc.png)


[http://i.imgur.com/6pGDLX4.png](http://i.imgur.com/6pGDLX4.png)


I've done some reading and I'm still not sure if Easy BCD is safe to use for Windows 8/UEFI stuff

But based on the available info what would be the best (safest) route to correcting this?  Has anybody out there used Easy BCD to move around boot entries like this?  OR is there something I can do through grub rescue commands to fix this?  I feel like I need to delete some of these grub files in Ubuntu

---

### Post by oldfred on 2013-01-22
It looks like EasyBCD is just showing the efi files in your efi partition that you can use to boot. You should see the same thing from your UEFI menu. Some UEFI do not come with the full UEFI shell but most do.

Grub then should offer to boot any efi file in the efi partition. You really should not need EasyBCD with UEFI, but I understand they have updated it to work with UEFI. Before it did not.

UEFI is a multi-boot system. It is like having many MBR's to boot from as every folder in the efi partition is another boot loader for another installed system.

---

### Post by fergie716 on 2013-01-22
I marked this thread as [SOLVED] because it primarily is. I have the regular grub menu now whenever I boot now.  To anyone stuck where I was or something similar here is what I did:

- Booted Windows and opened up Easy BCD, in the Boot Order Menu I moved the Ubuntu selection to #1 and also selected it as Default (Windows 8 was the default prior to this)

- This however did not solve my problem and in fact made it worse.  I was unable to load Windows 

- So, I booted into my Ubuntu system, updated everything (including boot repair) and ran Boot Repair.  In the options I selected the Backup and Restore EFI Files

- It must have restored some older backup I made earlier but whatever it did it worked. After I ran it (got the "Don't forget to BIOS loads from /sda2/EFI/ubuntu/grubx64.efi!" error)

- After boot repair finished I turned off my computer and turned it back on.. No more grub rescue!! Just the regular grub menu (purple background).

- I am able to boot into Ubuntu properly but also Windows.  However, when I select the UEFI Loader for Windows it takes me to a menu (it's a Boot Menu but looks like an older BIOS looking one, black and white) that has two selections: grub and Windows.  It also has an option for Windows Diagnostics.  AND if I press F8 on the while the cursor is on the Windows selection it takes me to a UEFI looking screen that has 9 options for running Windows, like debugging at boot, open a command prompt, and other development tools.

- But I am able to open Windows fine.  I doubt anyone has a solution to this so I'll accept it as SOLVED lol

Thanks for all the help!

---

### Post by fergie716 on 2013-01-22
In case this will help someone here is a copy of my boot repair pastebin

[http://paste.ubuntu.com/1561335/](http://paste.ubuntu.com/1561335/)

---

