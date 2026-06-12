---
title: "Grub Read Error Unless USB Connected"
date: 2013-12-01
forum: General Help
---

### Post by ryansharp331 on 2013-12-01
[SIZE=3][FONT=arial][COLOR=#333333]After installing Ubuntu 13.10, I can only load GRUB if I have the LiveUSB I used connected.[/COLOR]
[COLOR=#333333]What happens is I get a black screen with "Read Error". To circumvent this error, booting up with the USB connected, GRUB loads up completely fine and off I go. I don't even have to manually boot up the USB.[/COLOR]
[/FONT][COLOR=#333333][FONT=UbuntuRegular][FONT=arial]I have tried two solutions with no luck.[/FONT]
[/FONT][/COLOR]
[/SIZE]
[LIST=1]
[*][SIZE=3]sudo grub-install /dev/sda[/SIZE]
[*][SIZE=3]Automatic Boot-Repair[/SIZE]
[/LIST]
[SIZE=3][FONT=arial][COLOR=#333333]Neither solves my problem.
[/COLOR]
[COLOR=#333333][Fresh boot-repair log]("http://paste.ubuntu.com/6502530/")
[/COLOR]
[COLOR=#333333]Few things to note:[/COLOR]
[/FONT][/SIZE]
[LIST]
[*][SIZE=3][FONT=arial]I've just added a 3TB hard drive recently and reinstalled absolutely everything. However, the problem I am having has existed on my last installation, too. Just saying this in case someone makes the relation and this information helps.[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Ubuntu is on an SSD[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Windows is installed on a my second hard drive, so Grub isn't detecting it. I haven't solved this yet, if you guys notice that in the log.[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]While I understand that this question may have been asked many times before, no solution they have given has been successful.[/FONT][/SIZE]
[/LIST]

---

### Post by ryansharp331 on 2013-12-01
I managed to solve it a few minutes after posting this.

While I waited, I decided to hop into BIOS and mess around to troubleshoot. Turns out the one thing that caused this issue was having Quick Boot enabled!
After having this issue for over a year, having the solution something as simple as disabling Quick Boot is such an anti climax of sorts. I'd rather it be something very complicated to save me the shame.
I swear I've tried disabling that in the past, so I don't know if it was a combination of problems that have been fixed since initially troubleshooting.

Anyway, for future reference to people in my situation, start off with what I did and rid yourself of any embarrassment quickly.
Sorry for wasting anybodies time.

---

### Post by Cavsfan on 2013-12-01
It's **sudo grub-install /dev/sda**

---

### Post by oldfred on 2013-12-01
Is BIOS set to boot drive that is sda first?
Script does not totally parse grub in MBR so it is difficult to tell if it is installed correctly but if you reinstalled to sda, it should be ok.
Do you have drives in AHCI mode in BIOS? Not IDE nor RAID. If no AHCI mode use LBA or large. Does booting from one time boot key (f12 on my system but varies) work?

When you installed Windows to sdb, was sda the default boot drive? And then you installed Linux to all of sda? Windows has a separate (hidden in Windows) 100MB boot/repair partition as its standard install. And that partition will be on the drive set as boot in BIOS when Windows is installed. Usually sda and install is on sda, so no issue. You probably overwrote the Windows boot partition on sda.
You can either create a new boot partition, but your install in sdb can be repaired with a Windows repairCD or flash drive. You need to add bootmgr & BCD with configuration for your system which all the repari/update commands in Windows will do.

I prefer to have each operating system on a different drive as you have done, but also have an operating system on every drive. And now I prefer to use gpt for all new drives. It is only required for drives over 2TB, but can be used on any drive. I have used gpt on my flash drives. But Windows only boots from gpt with UEFI, so the Windows drive has to stay MBR until you have a new system with UEFI booting. Ubuntu will boot from gpt partitioned drive with BIOS or UEFI if correct partitions are on drive. UEFI should have efi partition first, so I always add that first as when I get my new UEFI system (only said that now for 2 years) I do not have to totally reformat drive.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by ryansharp331 on 2013-12-01
My bad, typed it out wrong. I used the correct command in the terminal though. :oops:
Fixed it in the OP to stop any confusion for people who find this thread through Google. Thanks for the catch.

---

### Post by ryansharp331 on 2013-12-01
> **oldfred said:**
> Is BIOS set to boot drive that is sda first?
Script does not totally parse grub in MBR so it is difficult to tell if it is installed correctly but if you reinstalled to sda, it should be ok.
Do you have drives in AHCI mode in BIOS? Not IDE nor RAID. If no AHCI mode use LBA or large. Does booting from one time boot key (f12 on my system but varies) work?

When you installed Windows to sdb, was sda the default boot drive? And then you installed Linux to all of sda? Windows has a separate (hidden in Windows) 100MB boot/repair partition as its standard install. And that partition will be on the drive set as boot in BIOS when Windows is installed. Usually sda and install is on sda, so no issue. You probably overwrote the Windows boot partition on sda.
You can either create a new boot partition, but your install in sdb can be repaired with a Windows repairCD or flash drive. You need to add bootmgr & BCD with configuration for your system which all the repari/update commands in Windows will do.

I prefer to have each operating system on a different drive as you have done, but also have an operating system on every drive. And now I prefer to use gpt for all new drives. It is only required for drives over 2TB, but can be used on any drive. I have used gpt on my flash drives. But Windows only boots from gpt with UEFI, so the Windows drive has to stay MBR until you have a new system with UEFI booting. Ubuntu will boot from gpt partitioned drive with BIOS or UEFI if correct partitions are on drive. UEFI should have efi partition first, so I always add that first as when I get my new UEFI system (only said that now for 2 years) I do not have to totally reformat drive.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.


GPT Advantages (older but still valid) see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

Yes sda was first in priority.

I installed Windows first and chosen the second HD, and it installed the 100MB partition on my SSD which I later removed. So I assume from that, sda was still the default boot drive.
The issue was existent even when I had Windows, Ubuntu and the 100MB partition on my sda.
Windows booted fine before I installed Ubuntu and also after I removed the 100MB partition and repaired with disk. Is the removal of the 100MB partition the reason Grub can't find my Windows OS?

I use GPT on my 3TB drive. Would I have been better off converting all of my drives to GPT to have consistency? 
I did have problems installing this Ubuntu after adding the 3TB HD. Windows installed fine, but Ubuntu wouldn't work without going into BIOS and changing the CD/DVD boot option into Legacy mode. I don't think my LiveUSB works anymore to install onto this machine.

I've marked this question as solved as the main issue is fixed, though I'm still curious about your response.

---

### Post by oldfred on 2013-12-01
Bootscript is not showing two main boot files anywhere.
       Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 
But a Windows repairCD or flash can fix it.

I only am converting new drives or a drive I totally reformat to gpt as it is the future. If you have a new motherboard that is UEFI capable, you do need to be careful booting installers for both Windows & Ubuntu. How you boot installer is how it installs, but you really want consistency or all systems BIOS booting or all systems UEFI booting. You cannot easily dual boot if they are not the same. Once you start booting in one mode you cannot switch or grub will not let you boot another system in different mode. Only from UEFI can you dual boot mixed installs.

For my new drives I make sure these are the first two partitions. Then I can boot either UEFI or BIOS. Neither take much room on new larger drives so even if not currently used not much space is lost.

 Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

---

### Post by ryansharp331 on 2013-12-01
> **oldfred said:**
> Bootscript is not showing two main boot files anywhere.
       Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 
But a Windows repairCD or flash can fix it.

I only am converting new drives or a drive I totally reformat to gpt as it is the future. If you have a new motherboard that is UEFI capable, you do need to be careful booting installers for both Windows & Ubuntu. How you boot installer is how it installs, but you really want consistency or all systems BIOS booting or all systems UEFI booting. You cannot easily dual boot if they are not the same. Once you start booting in one mode you cannot switch or grub will not let you boot another system in different mode. Only from UEFI can you dual boot mixed installs.

For my new drives I make sure these are the first two partitions. Then I can boot either UEFI or BIOS. Neither take much room on new larger drives so even if not currently used not much space is lost.

 Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

So in my case, as the only GPT is on my 3TB drive which is used only for data which I will shortly be symbolic linking to my /Home drive, I'm in the clear?
Is there a reason why my LiveUSB won't work when trying to install or 'Try Ubuntu'? I get an error with something about not 'finding any medium' or something to that effect. Do I have to format my USB to a GPT partition in order for it to work?
I'm confused as the LiveUSB worked completely fine before I installed Windows.

---

### Post by oldfred on 2013-12-01
Your live installer should not have changed. Sometimes grub gets installed in MBR mode and then it may not work, Boot-Repair should not have modified it.
The error sounds like a UEFI/BIOS error, but with the live installer it should offer to boot in either mode even new systems with secure boot.

I just do not like one very large partition, just because you have a very large drive. How are you backing up that partition?

---

### Post by ryansharp331 on 2013-12-01
I'm just storing music and videos on that drive. I can't afford to back up such large amounts of data so that is why I'd like to keep those on a separate drive.
My graphic design projects and college work will be backed up on my 350GB drive.

As for the LiveUSB problem, is there anything I can do to fix that? Perhaps the Quick Boot problem is what effected that. I will try that now, actually.
EDIT: Still broke.

The error is:
"BusyBox v1.20.2 (Ubuntu 1:1.20[...]) built-in shell (ash)
Enter held [...]

(initramfs) Unable to find a medium containing a live file system
_"

I am unable to type in this interface. Not sure whether it is an incompatibility with my keyboard or it's frozen.

---

