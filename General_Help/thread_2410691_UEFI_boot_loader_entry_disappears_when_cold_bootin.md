---
title: "UEFI boot loader entry disappears when cold booting, ASRock motherboard"
date: 2019-01-19
forum: General Help
---

### Post by Jugdish on 2019-01-19
In the beginning, I just had one HDD and it was running Ubuntu. Then I bought an SSD, and installed Ubuntu on that, repurposing the HDD to be a secondary data drive. But I never wiped the HDD. Now I'm in a situation where the system SSD drive has the EFI partition, but the secondary HDD is the only one with a bootloader in its MBR. I don't know how this happened (didn't realise it was possible tbh). But it means that apparently my SSD is completely reliant on the HDD to be present in order for booting up to work.

This is what boot-repair reports:
```

[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99-2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 
    2048 of the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img, but core.img can not be found at 
    this location.
 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/sdb.

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
```
/dev/sda = secondary data HDD
/dev/sdb = primary system SSD

What I want is to somehow install a GRUB bootloader into the MBR of the SSD, so that it can be self-reliant and my computer can still boot up if the secondary HDD were removed.

Is it possible to do this? Preferably without having to wipe and reformat the SSD?

Thanks for any help!

---

### Post by westie457 on 2019-01-19
Hi Jugdish
You have posted incomplete info, could you post the complete report or the link to it, then we can come with the correct suggestions to help you.

---

### Post by yancek on 2019-01-19
An EFI install does not need nor should it have any boot code in the MBR.  Have you set the SSD to first boot priority in the BIOS?  What is the result?  And also, please post the entire output of boot repair.i

---

### Post by Jugdish on 2019-01-19
Sorry about that, here is the complete report! [http://paste.ubuntu.com/p/sgM3hHgm7Z/](http://paste.ubuntu.com/p/sgM3hHgm7Z/)

---

### Post by yancek on 2019-01-19
Have you set the SSD (sdb drive) to first boot priority in the BIOS?
If you have the large drivee (sda) set to boot, I would not expect it to boot anything as you have Grub code in the MBR of that drive but the core.img file and other Grub files needed to boot are gone as you have apparently formatted that partition.  In any case, no files show.

---

### Post by Jugdish on 2019-01-21
Ok, I've done a bit of experimenting. I tried booting up with only the SSD attached, moved it to SATA slot 1, ensured it was boot priority #1 if UEFI setup, and all that.
[https://imgur.com/5EbMRm9](https://imgur.com/5EbMRm9)
[https://imgur.com/ldYrzPy](https://imgur.com/ldYrzPy)

It seems that this drive simply cannot boot up on its own. I get this error on the screen:
```
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
```
[https://imgur.com/gQhncM8](https://imgur.com/gQhncM8)

Then, I re-attached the large HDD drive, on SATA slot 2, still kept the SSD as boot priority #1. This time, the screen was stuck at a black screen with a flashing cursor and no error message.

Here's what I've noticed -- if I boot with a boot-repair USB drive and run the default boot-repair option, I can then restart and get back into my system like normal. This will continue to work as long as I am restarting each time. But as soon as I actually shut down the computer completely, when I turn it back on I am stuck in the situation described above, and have to run the default boot-repair option to bail myself out again.

How have I gotten into this situation and what can be done to fix it??

---

### Post by westie457 on 2019-01-21
This is probably the cause of your issue ```
[COLOR=#000000]sdb1: [/COLOR][COLOR=#000000]File system:       vfat[/COLOR]
```
The EFI partition must be formatted as fat32.

Give this a try.
Leaving only the SSD connected boot using your install media.
Start Gparted unmount all partitions, select your current efi partition and reformat to 'fat32'. Apply the changes. Then 'manage Flags' set these to 'boot,esp,hidden' again apply the changes. Exit Gparted.
Open a terminal and run these one at a time ```
[COLOR=#333333][FONT=UbuntuMono]sudo add-apt-repository ppa:yannubuntu/boot-repair
[/FONT][/COLOR]sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```
When the window opens click 'Advanced' check each tab to possibly purge Grub and reinstall to the correct partition and boot the correct OS. Follow the prompts as they appear, only clicking 'continue' after running the terminal (not sure if there is two or three short terminal sessions).
Make a note of the generated link so you can post it here if there is any issues.
Shutdown. Reconnect the other hard drive.
Start the computer.

You should now be booting properly.

---

### Post by oldfred on 2019-01-21
It says it is FAT32. The Linux driver is vfat.

```
    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  FAT32

```

What brand/model system.
Some systems do not like to boot ubuntu UEFI entry. (HP for one).
If UEFI updated, some users have reported changing boot order in UEFI works, where efibootmgr boot order setting does not stick.
The reinstall of grub uses efibootmgr to both add entry & change boot order to make Ubuntu first.


UEFI normally loses UEFI settings when a drive is unplugged. They seem to auto find Windows, but not Linux installs.
You then often have to use efibootmgr to update UEFI entry or reinstall grub.

---

### Post by Jugdish on 2019-01-21
It's an AMD system, the motherboard is an ASRock FM2A85X-ITX.

I'm not clear on what steps I should take, if the problem is the way the UEFI boot entries are formatted on disk, or with the motherboard & UEFI boot sequence itself. Reformatting the EFI partition makes me nervous (and is potentially unnecessary, according to oldfred). What else should I try?

---

### Post by oldfred on 2019-01-21
Reformatting the ESP (FAT32) is a last resort fix to some issues. Often just  a dosfsck works, if issues with the ESP.
But Boot-Repair did not show any issues.

Your Boot-Repair report originally did not show any ubuntu entry in UEFI. But after update, your UEFI now shows an ubuntu entry.
Not sure with Asrock, but have you tried the UEFI boot entry for ubuntu? Often f12 or what ever key you originally used to boot USB flash drive to get UEFI boot menu.

Have you checked that UEFI is latest version from Asrock? That often fixes many issues.
Most motherboard vendors will not say they support Linux, but often work better than some brand name systems.

---

### Post by Jugdish on 2019-01-22
I'm keeping the secondary HDD disconnected for now, to remove it from the equation while I troubleshoot. So all tests now are with only the SDD connected, on SATA slot 1.

Here is what's happening:

After running the default boot-repair option, a NEW entry shows up in UEFI Setup's boot options, called "ubuntu", and is set to boot priority #1:
[https://imgur.com/wKSn1gj](https://imgur.com/wKSn1gj)

As you can see, this entry is a separate entry from the SSD drive.
Booting up with this "ubuntu" UEFI entry, I am greeted with a GRUB menu which then successfully gets me into the Ubuntu system installed on the SSD.
[https://imgur.com/bomxaiR](https://imgur.com/bomxaiR)

After a soft reboot, the "ubuntu" entry stays intact and everything continues to work.

**However**, when I completely shut down and disconnect the power, and then COLD boot, the "ubuntu" entry goes away! There is now only my SSD listed in UEFI setup, and once again I get the "Reboot and Select proper Boot device" error.

So, whatever boot-repair is doing is adding a temporary "ubuntu" boot option to UEFI which does not last through a power loss.

Also, I've tried updating UEFI setup on my ASRock board, and it says I already have the latest version :(

What are my options at this point? Do I have to abandon UEFI boot and somehow revert my drive to legacy boot?

---

### Post by oldfred on 2019-01-22
Is that a Samsung system?
A few brands do not like any entry other than "Windows Boot Manager".
See if this works.
If only booting Ubuntu we can change label to be the required Windows label, but boot shim.

**d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

And most systems will boot a fallback or hard drive entry (similar to the boot of an external drive) at /EFI/Boot/bootx64.efi. Most Windows systems make bootx64.efi as a copy of Windows boot manager. If you run Boot-Repair, it backs up bootx64.efi and makes a new one that really is shimx64.efi. Then it adds an entry to boot the bkpbootx64.efi.
So if then you want to also boot Windows, see if you can add & boot /EFI/Boot/bootx64.efi (as really shimx64.efi), entry label may be "Hard Drive" or something similar. Then you do not need ubuntu entry and can add Windows entry.

Boot-Repair now auto copies shimx64 to bootx64.efi. Before we had to manually do that.
Older Samsung threads.
       Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.

---

### Post by Jugdish on 2019-01-22
It's not a Samsung system, the motherboard is an ASRock FM2A85X-ITX.

---

### Post by oldfred on 2019-01-22
Most of the Asrock systems I have seen have been Intel based.
They have issues with Asmedia ports or never connect any drive to one of those. Do not know if you have Asmedia or not.

Gigabyte boards with AMD, need IOMMU settings changed in UEFI and boot parameter. So not know if that also applies to Asrock or not.

---

### Post by kema77 on 2019-01-22
Have you tried to reinstall Grub to your SSD?. I am asking because I have found myself stymied on several occasions trying to get my primary OS to boot  because I messed around with my dual-boot (and at one time triple-boot with two physical disks) setup. By messing around, I mean doing things like moving partitions and deleting swap files. Each time, using the method shown in the link below rescued me.  I use legacy boot, rather than UEFI because I still dual-boot 32-bit Windows + Ubuntu. Frankly, I don't know if that makes any difference, but maybe it does.

 [https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by oldfred on 2019-01-22
UEFI & Legacy/BIOS/CSM boot are totally different.

Windows has to have gpt partitioning for UEFI boot and MBR(msdos) partitioning for BIOS boot.
With BIOS, you install grub to the MBR or first sector of a drive and before the first partition. Only one system can be installed in MBR.
UEFI uses an ESP - efi system partition (FAT32). Any number of systems can have folders in ESP and be directly booted from UEFI boot menu.

---

### Post by Jugdish on 2019-05-20
Hi, I am resurrecting this old thread because I'm still having the problem and I finally have some time to devote to fixing it.

Short recap:
- SYSTEM: Ubuntu 16.04, motherboard is AMD-based ASRock FM2A85X-ITX.
- PROBLEM: The UEFI bootloader disappears when cold booting. When I run boot-repair, it adds a new "ubuntu" entry to the boot menu, which works so long as I'm always hot rebooting. But as soon as I disconnect power and reconnect, the "ubuntu" entry disappears from the boot menu, and I get stuck at a black screen with flashing cursor because the system HDD has nothing to boot into.
- TRIED SO FAR: I tried oldfred's suggestion of renaming the "ubuntu" bootloader to have the label "Windows Boot Manager", with the idea that maybe my mobo only officially supports UEFI booting into Windows. Unfortunately this suffered the same problem - the "Windows Boot Manager" entry disappeared when cold booting.

I'm thinking at this point I should probably just abandon UEFI and revert back to Legacy/BIOS/CSM boot, because my motherboard clearly does not support UEFI booting into Linux. Does that sound like the right course to take? How exactly do I revert back to Legacy boot?

---

### Post by oldfred on 2019-05-20
Have you updated UEFI to latest version available for your motherboard?
That behavior is similar to when a drive is fully unplugged and UEFI removes entry from UEFI boot or changes to a default, but not standard boot.
Does system maintain date correctly? If coin battery is old, it may need replacing.  And then system loses settings when not connected to power.

You can add a tiny 1 or2MB unformatted partition with the bios_grub flag anywhere within the first 2TiB of a drive and install grub-pc, the BIOS version of grub. 
If you boot Ubuntu live installer in BIOS mode and use Boot-Repair's advanced options that should be an option.
The bios_grub partition is required for BIOS version of grub to install to gpt partitioned drives. Grub has another file normally in empty sectors just after MBR, core.img, but with gpt those sectors do not exist, gpt just has the protective MBR.

---

### Post by Jugdish on 2019-05-20
Yes, I've upgraded to the latest UEFI for the motherboard. And yes, my system does retain date correctly over power loss, so don't think the CMOS battery is the culprit.

In order to install a BIOS boot partition at the beginning of sda, I will need to delete the EFI boot partition and replace it. Is it ok to do that?

---

### Post by oldfred on 2019-05-21
You only need to shrink the ESP or any other partition by 2 or 3MB and create a 1 or 2MB unformatted partition with bios_grub flag.
I normally used to have both ESP & bios_grub partitions particularly on my full installs to flash drives. But now have used UEFI and old BIOS system is not working, so stopped adding the bios_grub by default.

---

