---
title: "Boot Loader Deleted"
date: 2016-01-27
forum: General Help
---

### Post by KenUBF on 2016-01-27
Hi. I've run into a big issue. I'm still very new with Ubuntu and I've hit a wall and not sure what to do. Here is my situation. 

I wanted to wipe some old hard drives so I connected them to my computer and unplugged my current hard drive from both the power and motherboard to make sure it also didn't get wiped. I successfully wiped the other drives but when I plugged my main hard drive back up it did not boot. Forgive me I am typing this on my phone since I have no other way to connect to the net. Do not see any place to upload pics of the screen I took last night but this is what comes up when I try to boot my hard drive:

GNU GRUB version 2.02~beta2-9ubuntu1

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions. 

Grub>

I read online that booting your computer while having your hard drive disconnected deletes your boot loader (wish I knew that before! Grrrr). I tried using boot-repair-disk that a friend burned to a cd and I got a message saying it was repaired but when I boot into my hard drive the same GRUB message still appears. I am at a loss as to what to do.  

Here is more info about my situation. When I tried to boot from a live cd it does detect my hard drive and it lets me enter my password to unlock the drive and see the files. My drive is also encrypted with LUKS. For some reason my computer will no longer connect to the Internet so I cannot use Terminal to down load the boot loader. My version of Ubuntu is fully updated with 14.04.3. 64-bit.  The live cd I have I believe is only 14.04.1. That is the latest live cd I have. 

It's so frustrating to know all my files are there I just can't access them. Any help will be greatly appreciated. Thanks.

---

### Post by grahammechanical on 2016-01-27
> I read online that booting your computer while having your hard drive disconnected deletes your boot loader

I do not believe that. Now, if the motherboard had a BIOS boot system then the boot loader would be in the first sectors of the hard disk. How could that be deleted if the hard disk is not connected?

It might be different if the motherboard has a UEFI boot system. The entry in the UEFI boot menu might become invalid. And that might be the situation in your case. There might also be another entry in the UEFI menu for that drive and that might be the one that works.

I have no experience of UEFI and we do not know if your machine is UEFI or BIOS or if Ubuntu is installed in UEFI mode and you are now booting in BIOS/Legacy mode.

The Boot Repair summary report would be a useful thing to see. Which we could do if you post the URL to it in this thread.

Regards.

---

### Post by oldfred on 2016-01-27
If UEFI, it loses the NVRAM setting for a drive that is removed. 
Either several hard/cold reboots and it will find entry. Fast boot in UEFI assumes no system changes, so it does not find new settings on a fast boot. Either several normal boots, or changing settings in UEFI will restore entries. Or worst case using efi boot manager from live installer can restore an entry.

If BIOS were you really booting from another drive. And copy of grub you now are using is not the most up to date version?

 grahammechanical's suggestion of Boot-Repair's summary report is best:
      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by KenUBF on 2016-01-27
Thanks for the reply. I can see my drive listed in the live cd and and under the Disks utility it says the Partition Type is "EFI System" for the first partition. For the other two partitions it says they are "Linux Filesystem". Perhaps partition 1 is the boot partition? So I am assuming it is EFI or UEFU (?). Unless those are different things. Forgive me I am very new to this. I did get a report for the boot repair disk but I am not sure how to access it or how to post a link. It looks to have just been a text file only. But I could copy what I see if I run it again if that helps.

---

### Post by Dennis N on 2016-01-27
The EFI System partition contains some or all the boot files when you install an OS in UEFI mode. The MBR does not have any boot files when using UEFI mode.

---

### Post by KenUBF on 2016-01-27
I tried oldfred's suggestion that the fast boot setting assumes no changes and disabled that. Still no change. Loading boot rescue now. Will post results soon.

---

### Post by KenUBF on 2016-01-27
When I start boot recovery disk I get the following message. /boot detected. Please check the options. I hit recommended repair. Let its do its thing. It tells me it cannot connect to the net. I click ok. I get a pop up saying Boot successfully repaired. 

Here is the text file that is generated. 

Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector 2048 of the same hard drive for core.img, but core.img can not be found at this location. 

Sda1:

File System: vfat
Boot Sector Type: FAT32
Boot Sector Info: No errors found in the Boot Parameter Block

Operating System [this field is blank, no entry on this line]

Boot Files: /EFI/Ubuntu/MokManager.efi /EFI/ubuntu/grub64.efi. /EFI/Ubuntu/shimx64.efi

sda2:

File System: ex2
Boot Sector Type: - [only shows a dash]
Boot sector info: [blank]
Operating system: [blank]
Boot Files: /grub/grub.cfg

Sda3

File System: crypto_LUKS
Boot sector type: Unknown
Boot Sector info: [blank]

Drive Partition Info:

Wow there is a lot there. If there are any sections that will be helpful let me know and I will copy them here. Thanks for your help everyone.

---

### Post by oldfred on 2016-01-27
Easier to post link so we can see entire file.

It looks from what little you posted that you have an UEFI system, but installed grub in BIOS boot mode. You need to always boot in UEFI mode including live installer with adding Boot-Repair.

You should get two boot options from UEFI boot menu to boot flash drive. 
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by KenUBF on 2016-01-27
Thanks for the link oldfred. I didn't know that. I only used a burned ISO image to install Ubuntu and allowed it to install with all default settings. I didn't choose any of those settings. Maybe I should list my hardware too since that might help. 

I have a self build. Asus ROG Maximus Hero VIII. LGA 1151. Intel i7 7600K. 4GHz. WD 4TB SSHD SATA  (hybrid drive) 64GB Ram Corsair Vengence LPX 16GB x 4.

---

### Post by oldfred on 2016-01-27
With my Asus Z97 motherboard, I did have to make a lot of changes in settings in UEFI.
Most critical were normal boot from cold (power off) boot, so then you have time to press a key to get into UEFI to make changes. Once I had system fully configured then I turned on fast boot for warm boots or reboots, but left a 3 sec delay, again just to give me a quick chance to get into UEFI if needed. I set grub to 3 sec also, so 6 sec of my 18 sec boot is just delays.
I changed from Windows to "Other" which I think is really the secure boot setting. 

And I had to turn on UEFI only to get it to boot in UEFI mode from flash drive. Even UEFI and CSM only booted in BIOS mode.
I also changed some other settings, USB boot allowed, USB on, Network boot last or off as I did not need it to even try that. Not sure what else now.

If a desktop do you really need full disk encryption? That has to use the advanced LVM or logical volumes which are logical partitions inside the physical partitions. You cannot use gparted and some other standard tools, but must use LVM tools.
And you must be careful to regularly houseclean old kernels. They did not make /boot generous and now with UEFI, you get several versions of kernels with every update which takes more space. Many users are not housecleaning and totally lock up system as it cannot download fixes when /boot is full. Many posts on how to fix issue, but not totally easy.

---

