---
title: "Fails to reinstall grub"
date: 2017-01-24
forum: General Help
---

### Post by lindsve on 2017-01-24
Hi,

First of all, I messed up. I had a dual boot setup, but decided to remove the Windows partition and resize my Ubuntu partition. All seemed fine, but my delirious mind decided to remove that "unnecessary ntfs boot partition". Yeah, that didn't work well.

I have now created a new boot partition at the start of the disk, but I can`t seem to get grub installed correctly. When I boot it keeps saying that no boot device was found.

Here is the pastebin returned from boot-repair: [http://paste2.org/52a70mdp](http://paste2.org/52a70mdp)

This is a HP EliteBook 840 G3 if that matters.

Any help is much appreciated.

---

### Post by yancek on 2017-01-24
So what exactly are you trying to accomplish.  You don't any windows partitions on the drive other than sda7 which is FAT32 and can't be a boot partition because it is not a primary partition.

Which version of windows did you have previously?  You have Grub in the MBR and msdos partitioning for it and the code points to the correct partition and the entries for Ubuntu are correct.  Did you change the boot priority back to the hard drive?  I see the message below in the boot repair output which is a problem.

> The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of sda5, using the following options: 

You don't have a UEFI install, check to see that Legacy or CSM is enabled in the BIOS rather than UEFI.

---

### Post by oldfred on 2017-01-24
It looks like you have a mixed install.
You have MBR(msdos) partitioning, but show the mount of the FAT32 partition as the ESP - efi system partition.
Generally you use MBR with BIOS.
And you use gpt partitioning with UEFI.

You can reinstall grub in BIOS boot mode with Boot-Repair.
Boot Ubuntu installer in BIOS boot mode & run Boot-Repair from the BIOS boot. In advanced options it should offer to uninstall grub-efi-amd64(UEFI) and install grub-pc(BIOS). Then you must set UEFI to CSM/BIOS boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

But you have newer UEFI based hardware. You may want UEFI boot, but HP is not one to make it easy. You have to do a work around which many have done.
How you boot install media, is then how it installs. Your UEFI should give two boot options for flash drive, but that may be a setting in UEFI to allow UEFI & BIOS or just one or the other.
So you know which way you boot.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by lindsve on 2017-01-25
A little update,

I might have ended up with the mixed install due to first trying the instructions listed in [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd) before I discovered boot-repair.
I didn't pay attention to the partition types (it's years since I knew much about this and I haven't really paid attention to it since before UEFI arrived), so I didn't catch the primary/extended partition issue with a boot partition.
I can't seem to figure out how to boot from my USB drive in legacy (BIOS) mode. The BIOS setup lists the USB drive in UEFI mode, but does not list the USB drive in the boot sequence for legacy mode. Unless I'm missing some setup to enable this in the BIOS setup, it looks like I'm stuck with discovering how to get this fully fixed in UEFI mode.

What I have done is remove the boot partition I created and shrink the extended partition. I have then created a new primary boot partition and reran boot-repair. Although I do still get error messages during boot which halts the boot, I can do some boot menu tweaking to load grub and actually boot into my ubuntu partition. What seems to remain is to get grub automatically loaded when I boot without navigating threw the BIOS setup. I'll try another run with boot-repair later today and post the results.

And thanks for the replies, both got me further so I at least can boot into ubuntu and get some work done

---

### Post by oldfred on 2017-01-25
If you have UEFI Secure boot on, you cannot boot in legacy mode. BIOS is not a Secure boot option.
And you often have settings in UEFI on external drive boot. One may turn on allow boot from USB and another may specify UEFI, CSM, or both type settings.
My motherboard (Asus) had a both setting but only booted in BIOS mode with both. I had to change to UEFI only to get it to boot in UEFI mode.
So each vendor has its own way of doing things and even that is not always what they say.

If you want UEFI, then you need to totally erase drive and change to gpt. There are tools to convert from MBR to gpt, but I have never used them. Either way you need good backups.

This shows screen as you first boot, so you know which way you have booted.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

Almost all the links I have on HP issues are for UEFI boot. Vendor issues are common across many models as they seem to use same UEFI with just differences for the different configurations.


 Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 

 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by lindsve on 2017-01-25
Final update, it's all working now :)

My main issue in this case was that I mixed up primary/extended partition and neglected to notice that I didn't set up my boot partition as a primary partition. As I noted on my earlier post today, booting halted with some errors after I ran boot-repair after fixing the boot partition, but it seems to work perfectly now.

Thanks again for the tips and prompt response!

---

