---
title: "Installed Ubuntu - now can't boot from USB or CD"
date: 2015-03-27
forum: General Help
---

### Post by natgwil on 2015-03-27
My laptop (Fujitsu Lifebook AH532) came with Windows 8, which I then upgraded to 8.1. I have now installed Ubuntu 14.04, completely replacing Windows. After I installed I realised I'd forgotten to setup a separate /home partition. So I want to follow the instructions at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

So I got out my Sysrescue CD (which has gparted on it) ready to boot from that, but I can't. Although after each restart the screen shows "F2 for Setup" "F12 for Boot Menu" pressing those keys causes a beep and nothing else. I can get into the UEFI BIOS setup by choosing "System Setup" from the Grub menu. However, although I move the CD drive and USB at the top of the boot priority list this does not work. The laptop still goes straight into Grub. And when I try restarting again and I look at the boot priority list again, Ubuntu is back at the top above CD and USB (yes I had pressed F10 to save and exit).

How can I restore the ability to boot from CD or USB?

---

### Post by oldfred on 2015-03-27
New Windows 8 systems are UEFI boot with gpt partitioning, but have settings to boot in CSM mode.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

The Windows & Ubuntu installers will boot in either mode which you select from the UEFI boot menu. Often UEFI is clearly shown, but BIOS mode is just the name of the flash drive.

Not sure if Sysrescue is UEFI capabile or not. You may have to switch system around to boot it. But if your install is UEFI that could create more issues.
Better just to use the flash drive or DVD you used to install Ubuntu as it has gparted on the installer. You can create the new partition from that.

Is drive gpt or MBR(msdos)? 
If MBR you have the 4 partition limit, but if gpt all partition are primarily and you have a soft (user can change to even more) limit of only 128 partitions. :)
Ubuntu can boot from gpt with BIOS mode or UEFI mode if correct supporting partitions are on drive. With UEFI you must have efi partition and with BIOS you must have bios_grub partition. I now partition all new drives with gpt and include both. Neither are really large and efi partition should be at beginning of drive and that would be difficult to add later when drive has lots of data.


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by natgwil on 2015-03-27
Thank you for your quick reply.

I can't boot from *any* CD or USB stick. Including the one that I used to install Ubuntu. 

I cannot access the UEFI boot menu to select USB or CD. But I could before installing Ubuntu.

The drive is GPT.

---

### Post by oldfred on 2015-03-27
You may have left UEFI fast boot or quick boot on.
Some are able to boot from a total cold boot. Turn off power, remove battery, hold power switch for 10 sec or so to remove any left over power. Then see if you can press correct key to get into UEFI and be sure to first turn off fast boot setting. And see it then you can choose to boot USB flash drive again.

       Some systems require password to turn off UEFI
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)
 Fujitsu Lifebook A512 [SOLVED] Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 
[http://ubuntuforums.org/showthread.php?t=2254442](http://ubuntuforums.org/showthread.php?t=2254442)

---

### Post by natgwil on 2015-03-30
I tried the cold boot idea. It didn't help.

I can get into the UEFI BIOS settings through selecting the System Settings option in GRUB. I checked and Fast Boot is disabled. I also tried again changing the boot priorities so that USB and CD Rom come before Ubuntu. This doesn't work. It still boots straight into GRUB. When I select System Settings and go into the UEFI BIOS settings again, it has not saved the boot priorities. Ubuntu is back at the top again.

---

### Post by oldfred on 2015-03-30
Does one time boot key work?
Most systems have another key that just gives the boot options often f10 or f12 but varies by brand, check manual if not sure.

---

### Post by natgwil on 2015-03-30
Yes it does have a key for boot options. That's the point. As I mentioned at the beginning of the thread, the startup screen shows "F2 for Setup" "F12 for Boot Menu". But when I press F12 there is a beep but nothing else. Then the GRUB menu appears. (Pressing F2 does nothing either - I can get into the UEFI BIOS setup but that's only because GRUB offers System Setup as one of the options.)

Incidentally I have managed to boot from a USB stick - however this was only achieved by going into the UEFI BIOS setup (through GRUB as mentioned above) and disabling Ubuntu in the boot menu options. Then I was able to boot from USB. However I would consider this is only a workaround, not a solution, because after using the USB and restarting, Ubuntu will not boot from the hard drive. I then had to boot from USB into a Live version of Ubuntu and run Boot-Repair. Now I can boot from the hard drive again, but I'm back to not being able to boot from USB or CD!

---

### Post by oldfred on 2015-03-30
Did you set a password (never lose that) as posted by several others in the links in post #4 above?

---

### Post by natgwil on 2015-03-30
Sorry, I don't understand what you mean. Set a password? 

If you mean do I need a password to enter to the UEFI BIOS setting then the answer is yes. I have set the password. And when I enter the UEFI BIOS using the GRUB menu entry "System Settings" I am using the password.

---

### Post by oldfred on 2015-03-30
Is there some other setting on fast UEFI boot or similar name?

My motherboard has a fast boot and normal boot for both warm reboot and cold boot. And then it has a delay setting for fast boot so you can get into UEFI, I set mine to 3 sec. 
But every vendor has done UEFI differently. And if links to the couple of users with Fugitsu above do not mention how they did it, cannot help much more.

---

### Post by natgwil on 2015-03-31
As I said, I can access the UEFI settings through GRUB. Fast Boot is *definitely* off. There are no other Fast Boot settings.

Is there any way to add an option to the GRUB menu for booting USB and CD? That would be a useful workaround.

---

### Post by dragonfly41 on 2015-03-31
I have no experience with UEFI since I'm still squeezing pips from my old Dell hardware.

However in your shoes I would run an experiment to *physically remove* the HDD from the laptop
and then see if I could then boot into LiveUSB or LiveCD (plugged in).

Perhaps if you then later plugin the removed HDD as an external resource (HDD placed in a USB container)
you could then get into it from the LiveUSB for hacking?

Just an untried theory.

---

### Post by oldfred on 2015-03-31
Almost everyone with booting issues of flash drive, were either settings in UEFI or flash drive was not correctly configured. Some also only could use certain ports for booting and a very few have flash drives that just do not work.

Often in UEFI with secure boot on, even thought Ubuntu will boot with secure boot on, the secure boot settings in UEFI prevent anything other than hard drive being used. And with secure boot off, you still have to separately turn on or allow the booting of other devices.

---

### Post by natgwil on 2015-04-04
Regarding suggestion in post #12, I have done something similar (see post #7). When I did this I was indeed able to boot from USB (and CD). However I then have to run Boot-Repair afterwards to be able to boot Ubuntu again. And then I lose the ability to boot from USB or CD again.

Regarding post #13 - there is nothing wrong with the flash drive, I have booted from it (again see post #7). The fact that after doing this, Boot-Repair restores the ability to boot Ubuntu again, suggests to me that there is something that could be done to restore the ability to boot from USB or CD drive.

---

### Post by oldfred on 2015-04-04
UEFI also has a one time reboot setting. It almost sounds like that is what is working, but then standard UEFI boot settings are not?

---

### Post by timschumi on 2024-04-19
I've recently looked into fixing this issue, and came up with a consistent way of restoring the laptop to full operation.

The boot menu entries can be partially restored by bridging the "CL1_CL2" test point  that is located under or next to the RAM slots.
It may be required to have the laptop powered (or even powered on) while bridging the contacts for the test points to have any effect.
This brings back the  device-based boot menu entries, but does not yet restore access to the  BIOS Setup menu.
For that, a USB stick with [Fujitsu's BIOS update tool]("https://support.ts.fujitsu.com/")  (search by serial number to make sure you find the correct hardware revision) needs to be prepared, booted from, and run.
This restores most BIOS  settings to their default, including the missing BIOS Setup menu.

Alternatively, if the currently installed Linux system is still  bootable, one can use [this tool]("https://github.com/timschumi/ah532-biostools") to restore all entries  without having to go through a BIOS update and reset.
This works by manually  rewriting all broken EFI variables with their expected content.
Please do make note of the list of supported configurations and of the  disclaimer (and let me know in case the tool does or doesn't work on  some previously untested configuration).
In case you want to know more about this works, there is a [post explaining the underlying details]("https://blog.timschumi.net/2024/01/20/ah532-bios-investigation.html").

Lastly, a [workaround for the issue]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=f45812cc23fb74bef62d4eb8a69fe7218f4b9f2a") has been merged into the Linux  kernel, which should keep this from occurring on any new  installations.
This patch already ended up in the current installation  media for the Ubuntu 24.04 beta (which I have confirmed to be not affected), and it will presumably be included in  all installation media going forward.

---

