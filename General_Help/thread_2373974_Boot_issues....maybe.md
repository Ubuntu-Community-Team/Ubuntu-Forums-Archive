---
title: "Boot issues....maybe?"
date: 2017-10-11
forum: General Help
---

### Post by aviator1 on 2017-10-11
Hello All:
 
 A few months ago, I received a lot of help from some really knowledgeable folks here on the forum. I sincerely thank all who commented and helped.
 
 In the end, there was a &#8220;work around&#8221; to one of my issues about having to logoff and logon in order to use some of the programs. That &#8220;work around&#8221; is still working OK.
 
 In a recent boot up, I took a look at my boot sequence, and wonder if I may have a problem there.
 
 My main drive is a 256GB SSD, and my secondary is a 2 TB HDD. Both have fresh installs of Ubuntu 16.04. Both previously were dual boot with Windows 7, but I eliminated that with the fresh installs.
 
 Here is what I see on bootup:
 
 Boot Priority:
 
 256GB SSD P1: MA-CT256M4SSD2 (244198MB) This _**does not**_ have a UEFI banner across it.
 
 CD-PO:Hl-DT-ST BD-RE WH14NS40 This _**does not**_ have a UEFI banner across it.
 
 2TB HDD Windows Boot Manager P4: 2000DL003-9VT166 This _**does**_ have a UEFI banner across it.
 
 2TB HDD Ubuntu P4: 2000DL003-9VT166 This _**does**_ have a UEFI banner across it.
 
 2TB HDD Ubuntu P4: 2000DL003-9VT166 This _**does**_ have a UEFI banner across it.

Any comments, or suggestions?

Thanks for any response.

---

### Post by oldfred on 2017-10-11
Not sure what you mean by UEFI banner?


May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by aviator1 on 2017-10-11
It's a blue banner withe the letters UEFI written on it. It runs diagonal across the HDD symbol.

Is there a way I could copy it?

I will read the links you provided.

Thank you.

---

### Post by aviator1 on 2017-10-11
I have run Boot Repair in the past few days. No change.

Here is the link for the info. [http://paste.ubuntu.com/25720996/](http://paste.ubuntu.com/25720996/)

---

### Post by aviator1 on 2017-10-11
Forgot. I also have a 2 TB external USD HDD

---

### Post by oldfred on 2017-10-11
You have a mixed install.

You have UEFI/gpt on external drive and BIOS/MBR on internal drive.
So you must have newer UEFI hardware.

Often best to have system all UEFI or all BIOS boot. Often limit is Windows as it only boots with BIOS from MBR and only with UEFI from gpt.
But Ubuntu can boot with either BIOS or UEFI from gpt if correct supporting partitions ESP or bios_grub are on gpt drive.

UEFI systems normally check UEFI boot first, then try BIOS boot, then post fail to boot message.
So that may be part of the boot issue you have.

Did we have you copy shimx64.efi or grubx64.efi to /EFI/Boot/bootx64.efi on external. As that is only way you can boot an external drive in UEFI boot mode. Normal install of grub as part of a full install does not create bootx64.efi.

If internal drive is a fresh install, I might suggest reinstalling in UEFI boot mode. Be sure to fully back up all your data, /home, any customized settings you manually changed in /etc (usually not many) and if you manually added many apps, back up list of installed apps to make it easy to reinstall.

How you boot install media UEFI or BIOS is how it then install. But UEFI suggests gpt and the conversion from MBR to gpt will in effect erase drive. If you had a data partition on sda, I would also suggest manually changing MBR to gpt first, so you could probably preserve data partition on reinstall.
I normally use 25GB as my / (root) partition on SSD and have at least 2 root partitions on SSD, previous install and current install. I use LTS so currently on my SSD I have 14.04 which should still boot, but has not been booted for a while & will be 18.04 eventually. And I boot 16.04 as main working install. I have all data on HDD as well as several more / as test installs.

My current / uses 9.2GB but /home is tiny as all data is on HDD. I do keep /home inside /, but for newer users, having /home on HDD is a bit easier to set up as then mount in fstab, owership & permissions are all set during install. Use of data partition requires you to manually do all that.

---

### Post by aviator1 on 2017-10-11
Oldfred. Thanks very much for your response. I apologize, but I do not understand most of what you posted. I am a long time user of Ubuntu, but simply do not understand the technical side very well.

I would not know how to reinstall in UEFI boot mode.

The external drive is just used for backups. I have never booted from it. Disconnecting it does not change the boot problem. I did not copy shimx64.efi or grubx64.efi to /EFI/Boot/bootx64.efi on external.

I appreciate your help.

To my knowledge both fresh installs were done without partitions.

---

### Post by oldfred on 2017-10-11
You have to have partitions, you have at least / (root) and swap on sda.

If you have a new install on sda and nothing to save, boot installer in UEFI boot mode.
That should be a choice in UEFI boot menu for flash drive. Normally you get two boot options, one UEFI:flash and the other "flash" ( which is then BIOS) where flash is the name or label of flash drive.

See also link in my signature.

---

### Post by aviator1 on 2017-10-11
Sorry to be dense about this....

When you say "boot installer in UEFI boot mode", do you mean using the install disk, which I made to do the fresh install?

Should I just do a backup and another fresh install using the choice you mentioned?

Thanks very much.

---

### Post by aviator1 on 2017-10-11
The Primary SSD drive has a File System Partition 1 and has and extended partition 2 of 17 GB over a swap partion of 17GB
 
 
 It says it has a Master Boot Record partioning.
 
 
 The internal HDD has a file system  partition 1 of  537 MB FAT,  a file system  partition  2 of 2.0 TB Ext 4, and a swap partition 3 of 17 GB This drive is a GUID Partition Table
 
 
 It says disk is OK, but with 328 bad sectors

---

### Post by oldfred on 2017-10-11
You use the same live installer you used. How you boot it is then how it installs.

Just boot in UEFI mode to install in UEFI mode.
It will then convert drive from MBR(msdos) to gpt. If you have any data you want to save be sure to back that up first.

---

### Post by aviator1 on 2017-10-11
Got it. Thanks. Will report later tonight or tomorrow.

Have a great evening.

---

