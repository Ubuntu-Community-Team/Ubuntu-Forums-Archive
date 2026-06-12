---
title: "The dual boot problem"
date: 2020-10-05
forum: General Help
---

### Post by Panawe on 2020-10-05
I have built a new computer and duly installed Ubuntu after Windows 10 and have lost the GRUB dual boot option. You all know this I realise but does anyone have a simple low-tech solution? At the moment I have to reconfigure my boot options to get into Windows.
I tried making the CDRom the first option and sticking a Win10 Rescue Disk in there but it doesn't give me the option to proceed to Windows.
Something involving a USB stick?

TIA

---

### Post by metacell on 2020-10-05
Did you lose the ability to boot to Windows when you installed Ubuntu? That's strange, since Ubuntu usually handles Windows quite well.

Does the Grub boot menu show up and Windows is missing, or does the boot menu not show up at all?

---

### Post by Panawe on 2020-10-05
No sign of the dual boot menu on startup - I did install Ubuntu last.
From Googling I know it is a problem because of something called EFI which is the latest Windows boot option.

Thanks for responding.

---

### Post by yaminb on 2020-10-05
I'm not sure what stage you're at. Do you have a lot of data and everything already set, or are you free to play with stuff?

Judging by your sig: "1st drive partitioned for Ubuntu 18.04 and Windows 10 - both 64bit, 2nd as storage.", I'll take it you have 2 drives.

When I installed Ubuntu a while ago, I tried a few times and partitions and mucked things up a bunch of times... I've found the following to be pretty good for not messing things up.

1. Install Windows on Drive 1
2. Install Ubuntu on Drive 2 (Note, Ubuntu installer was pretty stupid when I did it as I had to do the 'advanced' install just to use the second drive. So you do have to create the partitions manually. Be sure to create a second EFI partition on Drive 2 for ubuntu)
3. As for storage, in my case, I don't need a lot of shared storage. That is the Windows Drive has the rest as NTFS. The Ubuntu drive has the rest of space as ext4. But once your base drive is configured you can resize and play with all of that.

I find this pretty solid. If one EFI partition breaks, you have the other one on the other drive. It's happened to me once or twice, and makes everything a bit easier. People say sometimes Windows mucks around with UEFI, in this case, if it does so, it will only muck up the EFI partition on it's own drive.

Then on BIOS, you of course choose the drive you want to boot from.

Yes, U lose a few hundred MB as you duplicate the EFI partition, but you have a TB drive... space is cheap these days.

---

### Post by Impavidus on 2020-10-05
So you can see the grub menu, but it doesn't show Windows, and you can boot Ubuntu? And you can boot Windows by going through the UEFI menu? Sounds like a classic case: grub-update didn't detect Windows. Have you disabled FastStartup in Windows?

---

### Post by yancek on 2020-10-05
Can you boot windows by accessing the windows option in the BIOS?  A default preinstalled windows 10 will be UEFI so did you install Ubuntu UEFI also?  You can post more details about your system by using boot repair which you can download on Ubuntu from the link below.  Use the 2nd option described on that page using the ppa and after downloading it, run it only with the option to Create BootInfo Summary and post the link you get when it finishes here.  That will give members more details on your system and hopefully enable someone to suggest a solution.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Panawe on 2020-10-05
First of all let me apologise for not updating my signature with the actual computer I am using and not the one in the cardboard box in my bedroom!

I can easily swap between Windows and Ubuntu by going into the BIOS and changing the boot sequence, that is my situation at the moment and, truth to be told, I can live with it. But I wondered if there is something I can put on a USB drive that l;et's me choose on start-up.

Thanks to all responders.

---

### Post by Panawe on 2020-10-05
This is annoying, my signature isn't updating. My current  computer is this:

I have an AMD Ryzen 5 3400G running on a Gigabyte B450 AORUS PRO motherboard with 16GB DDR4 3600mhz RAM. There are two WD Blue SN550 1TB SSDs in M.2 slots. The first SSD has two partitions of 500 Gb each with Windows 10 running on one and Ubuntu 20.04 on the other partition, second drive (NTFS) used as storage.

---

### Post by coffeecat on 2020-10-05
> **Panawe said:**
> This is annoying, my signature isn't updating. 

The text of your sig is exactly the same as the text in the signature field of your profile. Obvious question: did you remember to click on the "Save Signature" button under the Edit Signature editor in the Settings -> Edit Signature page? If you save your edited signature, the new text will appear in all old posts that were made when you had text in your signature field.

---

### Post by Panawe on 2020-10-05
Test!

---

### Post by Panawe on 2020-10-05
Fast start up now disabled.

---

### Post by Panawe on 2020-10-05
Here's the output from Boot Repair:

[https://paste.ubuntu.com/p/bvh82R6QsV/](https://paste.ubuntu.com/p/bvh82R6QsV/)

TIA

---

### Post by oldfred on 2020-10-05
Boot-Repair is giving you the info you need.
You have newer UEFI based system and Windows installed in UEFI boot mode. Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012.

User can install in UEFI or BIOS mode and that depends on how you boot USB flash drive. Normally you get two options one clearly UEFI like UEFI:flash and one "flash" which is BIOS & where flash is name or label of your flash drive installer. My system just uses PMAP. 

But you installed Ubuntu in 35 year old BIOS boot mode.
UEFI and BIOS are not compatible, or once you start booting in one mode, you cannot switch. Or grub can only boot other installs in same boot mode.

Also to repair Windows or Ubuntu you have to boot installer in correct boot mode. So boot Ubuntu live installer in UEFI boot mode. Boot-Repair's advanced mode should give you the option to totally uninstall grub (grub-pc for BIOS) and install grub-efi-amd64 for UEFI boot. That just reinstalls grub, you do not have to do a total reinstall of Ubuntu.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Windows updates will turn fast startup back on. And if system supports UEFI update from Windows that may also be updated resetting UEFI to defaults. I keep a list of UEFI settings.
If not auto updated, you should regularly check & keep UEFI at most current available version.

---

### Post by Panawe on 2020-10-05
Did that had got the options at the Boot screen.

Many thanks to all especially oldfred.

---

