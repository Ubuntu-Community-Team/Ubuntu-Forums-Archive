---
title: "boot problem"
date: 2017-04-11
forum: General Help
---

### Post by cccwillis on 2017-04-11
I have a Toshiba ([COLOR=#333333][FONT=Arial]Portege R935 / i5-3210M / 13.3" / 8GB / 750GB-5400)[/FONT][/COLOR] with Ubuntu installed that will only boot to the Toshiba splash screen and then sits there indefinitely.  I did a lot of dumb and mean things to it trying to fix a boot issue with it as a dual boot system (Ubuntu/Windows 10) and everything I did just made it worse ([B]Edit: It's not dual boot anymore, this question is about fixing an Ubuntu 16.10 install only)
[/B]
The error message that flashes up, alternating with the Toshiba splash is:

Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load image \EFI\BOOT\grubx64.efi: Not Found
start_image() returned Not Found
(repeats this on and on and on)

I have tried doing a full disk erase and install of Ubuntu, then Windows, then back again **(Edit: not attempts at dual boot, full single installs)**, just to see what I could shake loose and this problem persists.  It seems like whatever is looking for the grub is broken/confused and I don't know how to fiddle it, but Ubuntu has been installed to the satisfaction of the installer with no errors generated.

One of the things I have done is run boot repair, the last two results are here:
recommended: [http://paste2.org/WeW3b6M3](http://paste2.org/WeW3b6M3)
advanced (done after recommended didn't fix the issue): [http://paste2.org/0YyOPzOV](http://paste2.org/0YyOPzOV)

Right now I can only run from a live CD, but I can get into the Toshiba settings okay with F12.

Any suggestions on how to fix this would be greatly appreciated!

---

### Post by oldrocker99 on 2017-04-11
You should always, in a dual-boot system, install Windows **first** before installing Ubuntu. Otherwise, your boot *will* be messed up.

---

### Post by cccwillis on 2017-04-12
> **oldrocker99 said:**
> You should always, in a dual-boot system, install Windows **first** before installing Ubuntu. Otherwise, your boot *will* be messed up.

I agree wholeheartedly, though the problem I am trying to fix now doesn't pertain to a dual boot system, that's just where my trouble started*.  It's actually boot repair that truly boned my system into un-boot-ability (its the last thing I did before this problem started).  I have since wiped the whole thing and done a fresh install, and the problem (won't boot past Toshiba splash screen) persists.  So just to be clear: I'm trying to fix an Ubuntu install that's the ONLY OS now.

*The problem I had with the dual boot was pretty minor (I had installed Ubuntu second onto a system already running Windows 10).  It would always boot to Windows when I REstarted.  If I performed a full shutdown, it would boot to Grub and I could boot into either system as desired.  But the dual boot is long gone at this point.

---

### Post by oldfred on 2017-04-12
New Toshiba are now like Sony & HP. They violate UEFI standard and use description as part of boot. And only valid description is "Windows Boot Manager". Most prevent you making Ubuntu the default but many let you boot manually from UEFI menu.
Can you boot ubuntu one time with f12 UEFI boot menu?

Various work arounds, depending on configuration. Most make the fallback/hard drive entry which uses /EFI/Boot/bootx64.efi as a copy of shimx64.efi. All UEFI systems use that to boot external drives and it can be used on internal drive.
       
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
     'Use the standard EFI file' in advanced options. 

But Boot-Repair does not create an UEFI entry. Some systems already have a hard drive entry.
       sudo efibootmgr -v  
Your ESP - efi system partition is sda1 which efibootmgr uses as default
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi

If others see thread and have ESP on different partition, they have to specify that:
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sdX -p Y
sdX is drive, Y is efi partition example for sda2
sudo efibootmgr -c  -l *EFI*ubuntu/shimx64.efi -L "ubuntu" -d /dev/sda -p 2 

See also for details on efibootmgr commands:
man efibootmgr

Since not using Windows, you can delete the Windows entry and add a new "Windows Boot Manager" entry that uses shimx64.efi. Systems seem to check description, but not actual file used to boot.
      
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B 

  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by cccwillis on 2017-04-17
oldfred, thank you for your detailed answer.  I cannot boot from the Toshiba boot menu when I push F12.  It lists the HD then the ODD (then Lan1, etc), and the HD boot option hangs.  If I start the device without a Ubuntu live disk, it hangs indefinitely on the Toshiba splash, but the moment I put it the live disk, it boots from there

I tried the following commands while running Ubuntu live which you suggested:

[COLOR=#000000]sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi

and

[/COLOR][COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

[/COLOR][COLOR=#000000]But this did not change the boot behavior.[/COLOR]

[COLOR=#000000]For reference, at one point I tried installing Windows 10 using a disk, and after the install, which seemed to have worked correctly, Windows wouldn't boot either.  I am back to a full Ubuntu install currently.  But to me this demonstrates that something has happened to the layer above what the installer touches, Ubuntu or Windows, and this is where my understanding gets wobbly.  How do I fix what is supposed to call GRUB?  I know GRUB is there, but the machine doesn't find it somehow.

I think I will try to contact Toshiba about how to repair it, and report back what I find, but any other suggestions would be greatly appreciated.

[/COLOR]thanks in advance.

---

### Post by oldfred on 2017-04-17
Do you have the newest UEFI from Toshiba?

If you mention Linux they will not help you. Almost no vendors support Linux.
But if same issue with Windows then report that.

---

### Post by cccwillis on 2017-04-21
oldfred, I don't know what UEFI I have currently.  Do you have thoughts on how to pursue this?

It's definitely an issue in windows too, but it turns out I didn't need to speak to a human.   Their web based trouble shooter suggested I buy a new hard drive (ha!) or that UEFI might be the problem.  I know I've wiped the recovery partition Toshiba had installed, so I'm going to get media from Toshiba that I can (hopefully) use to do a factory reset on the device and fix this issue.  But if you have suggestions for UEFI updates or fixes, I'm all ears.

---

### Post by oldfred on 2017-04-21
Depending on age of system, vendors have had to make many  updated to their UEFI/BIOS.
Often first year or two there are many fixes. Some only mention one or two issues, but fix others.

But some say if system works not to update UEFI/BIOS as that has some risk of bricking system. I have always updated system and never had issues, but never had power failure in middle of update either.

Does Toshiba show a newer UEFI/BIOS for your system?
It may show drivers, also, but those are normally for Windows.

---

### Post by pete-br on 2017-04-26
> [COLOR=#000000]Failed to open \EFI\BOOT\grubx64.efi - Not Found[/COLOR]

I am almost certain that you have deleted your ESP partition. You will need to recreate it.

First make the partition.
Your disk has to be in GPT format already, otherwise is couldn't have Windows with EFI installed onto it.
You have to give the ESP partition the 'boot' flag. ('Manage flags' with GParted)

With the partition in place, you could manually mount it from the command line and recreate directories and files.
Here is an excellent source of information: [http://www.rodsbooks.com/refind/installing.html#linux](http://www.rodsbooks.com/refind/installing.html#linux)
To make things more simple I would use rEFInd in the future, unless you are doing disk/partition encryption.

---

### Post by oldfred on 2017-04-26
In first post the Boot-Repair summary report showed files in ESP including:
/EFI/ubuntu/grubx64.efi

---

### Post by pete-br on 2017-04-26
I didn't look at the report files the first time. You are right, the ESP does still exist.

However, the problem is actually clear from that report:

[LIST=|INDENT=1]
[*][FONT=inherit]/EFI/Boot/bootx64.efi /EFI/ubuntu/fbx64.efi [/FONT]

[*][FONT=inherit]/EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi [/FONT]

[*][FONT=inherit]/EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi [/FONT]

[*][FONT=inherit]/EFI/Microsoft/Boot/bootmgfw.efi [/FONT]

[*][FONT=inherit]/EFI/Microsoft/Boot/bootx64.efi[/FONT]
[/LIST]
Above are the files located on the ESP partition (sda1).

The error goes as follows:
[COLOR=#000000]*Failed to open \EFI\BOOT\grubx64.efi - Not Found*[/COLOR]

Look carefully and you see: grubx64.efi is located in the directory /EFI/ubuntu according to the report.
And UEFI is reporting that the file does not exist in /EFI/BOOT.
So what is the problem then? UEFI correctly reports the file not present in the given directory.

Either you move the file to the correct directory
OR you tell EUFI the correct path to grubx64.efi.

A Live CD will allow you to manually mount the ESP partition from the command line (mount /dev/sda1 /mnt/boot/efi).
The following link again, shows how to tell UEFI where your file is located (using efibootmgr).[URL="http://www.rodsbooks.com/refind/installing.html#linux"]
http://www.rodsbooks.com/refind/installing.html#linux[/URL]

---

### Post by cccwillis on 2017-04-27
> **oldfred said:**
> Depending on age of system, vendors have had to make many  updated to their UEFI/BIOS.
Often first year or two there are many fixes. Some only mention one or two issues, but fix others.

But some say if system works not to update UEFI/BIOS as that has some risk of bricking system. I have always updated system and never had issues, but never had power failure in middle of update either.

Does Toshiba show a newer UEFI/BIOS for your system?
It may show drivers, also, but those are normally for Windows.

This is a little unfamiliar to me, sorry.  I purchased the system back in 2012 new from the manufacturer with Windows 8 installed, and was "given" a free upgrade to Windows 10 when that came out, and this was its condition when I made my botched attempt at a dual boot. You're suggesting that I can see if there's been a UEFI update on Toshiba's support site and download/install said update, correct?  I can look into that.

> **pete-br said:**
> 
Look carefully and you see: grubx64.efi is located in the directory /EFI/ubuntu according to the report.
And UEFI is reporting that the file does not exist in /EFI/BOOT.
So what is the problem then? UEFI correctly reports the file not present in the given directory.

Either you move the file to the correct directory
OR you tell EUFI the correct path to grubx64.efi.

A Live CD will allow you to manually mount the ESP partition from the command line (mount /dev/sda1 /mnt/boot/efi).
The following link again, shows how to tell UEFI where your file is located (using efibootmgr).[URL="http://www.rodsbooks.com/refind/installing.html#linux"]
http://www.rodsbooks.com/refind/installing.html#linux[/URL]

I'll give this a try, it sounds promising and I'll let you know the end result.  It would be nice if it's as simple as giving it a different path.

In the meantime, I coughed up the $40 for a usb key from Toshiba that should allow me to factory reset the machine.

---

### Post by oldfred on 2017-04-27
You can do a full backup and avoid the $40 fee.
My Dell had a Windows backup, a Dell backup and then I did a full image backup. That was all Windows 8, after upgrade to Windows 10 I did another backup.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media

[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 
      
 How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
[http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/](http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/)
WinRE recovery partition after main NTFS
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) 
    


[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]
[/URL]

---

### Post by cccwillis on 2017-04-28
> **oldfred said:**
> You can do a full backup and avoid the $40 fee.[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]
[/URL]

Unfortunately in this case I don't think its possible to avoid the fee (for the factory reset route).  While I backed up my files so I haven't lost any data, I didn't create a back up image in advance and the recovery partition has been wiped off the drive.  Hindsight is 20/20 and all that.  But good stuff for future reference.

---

### Post by cccwillis on 2017-05-12
Alright... an update.

**TLDR:** resetting defaults in the Toshiba boot menu seemed to fix the problem that boot repair generated, but I cannot install Ubuntu on the whole disk and have it boot (frozen at Toshiba splash screen).  However, both OSes are bootable (with some quirks) after installing a dual boot Windows10/Ubuntu set up.

Full story:
The factory reset USB key ran and completed, but on reboot said that Windows had not installed properly.

An ubuntu install also failed subsequently (installer claimed to work, but on boot machine stayed frozen on splash screen).

I attempted installing Windows 10 then, and when the installer choked (different than the factory reset and Ubuntu, which only failed on reboot), it suggested I change my UEFI/Boot settings and when I clicked "ok" it rebooted me into the Toshiba boot options menu (the same as I get from pressing either F2 or F12 when I boot, I always get those mixed up).  I didn't see anything obvious for me to fix there, so I used the reset defaults option, saved and rebooted.... and it booted into Windows 10!  (Windows, not exciting, actually booting into AN operating system though, yay!!!!)

Now, I subsequently attempted installing Ubuntu on the whole disk, but I got the same "frozen on splash screen" behavior as before.  So I reinstalled Windows 10, and then created a dual boot with Ubuntu.  There is a quirk to the booting though.  If I select "restart" from either Ubuntu or Windows, the system automatically boots directly into Windows on restart.  If I select "shutdown" from either OS, when the computer is started, it gives me the GRUB menu where I can pick what OS I want to boot into.

I am now basically back to where I was before I ran boot repair and mucked things up.  I think the issue with installing Ubuntu on the whole drive (wiping the windows boot option) relates to one of oldfreds earlier posts regarding Toshiba & boot descriptions (below).  However, at this point, I am tired of messing with this, and I'm just going to live with my quirky dual boot.

***Moral(s) of the story***: For my Toshiba laptop ([COLOR=#333333][FONT=Arial]Portege R935 / i5-3210M / 13.3" / 8GB / 750GB-5400) [/FONT][/COLOR]boot repair was more trouble than its worth, but resetting defaults in the Toshiba boot menu was likely what fixed things (possible that and a fresh install).  Installing Ubuntu stand alone on the device is problematic, and an issue I ultimately decided to avoid by using a dual boot, which somehow works?  I guess this "solved" now, but rather unsatisfactory.

> **oldfred said:**
> New Toshiba are now like Sony & HP. They violate UEFI standard and use description as part of boot. And only valid description is "Windows Boot Manager". Most prevent you making Ubuntu the default but many let you boot manually from UEFI menu.

Various work arounds, depending on configuration. Most make the fallback/hard drive entry which uses /EFI/Boot/bootx64.efi as a copy of shimx64.efi. All UEFI systems use that to boot external drives and it can be used on internal drive.
       
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
     'Use the standard EFI file' in advanced options. 

But Boot-Repair does not create an UEFI entry. Some systems already have a hard drive entry.
       sudo efibootmgr -v  
Your ESP - efi system partition is sda1 which efibootmgr uses as default
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi

If others see thread and have ESP on different partition, they have to specify that:
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sdX -p Y
sdX is drive, Y is efi partition example for sda2
sudo efibootmgr -c  -l *EFI*ubuntu/shimx64.efi -L "ubuntu" -d /dev/sda -p 2 

See also for details on efibootmgr commands:
man efibootmgr

Since not using Windows, you can delete the Windows entry and add a new "Windows Boot Manager" entry that uses shimx64.efi. Systems seem to check description, but not actual file used to boot.
      
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B 

  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

