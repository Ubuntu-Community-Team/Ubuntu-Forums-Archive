---
title: "Ubuntu on separate disk (MBR) from Windows (GPT,NVME)"
date: 2020-02-13
forum: General Help
---

### Post by blaz-mandl on 2020-02-13
Hello guys,
Recently I installed Ubuntu on separate SSD alongside Windows, which is installed on NVME SSD disk. I recently changed partition table on windows disk (NVME) from MBR to GPT to support UEFI boot. I have my Ubuntu SSD as first boot device and I use grub to boot in Ubuntu or Windows 10. But after I changed windows disk to GPT, I can't boot in Windows from Grub menu (only if I select windows disk as first boot device from bios). I googled a lot about this issue and non of solutions work for me (repairing grub and updating it and such things, even manualy adding grub entry). My first question is, should I convert my Ubuntu disk to GPT as well to boot with uefi and should I share one uefi boot partition for both windows and ubuntu (but OSes are on separate disks)? Please, help me set up ideal configuration, because I want to use UEFI on both Windows and Ubuntu (since my motherboard supports it, why not?). If I need to post some outputs from terminal, please let me know.

---

### Post by mastablasta on 2020-02-13
you need to have both system in UEFI mode. see **Converting Ubuntu to UEFi mode** here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-02-13
I like to have an ESP - efi system partition on every drive. But Ubuntu Ubiquity installer will only install grub to first drive's ESP, usually sda or first NVMe drive. Grub can be separately installed to any ESP. But sharing with Windows normally works without issue.

You can convert an Ubuntu install to UEFI boot manually or with Boot-Repair and convert to gpt with gdisk. But must have an ESP on the drive if you want to install grub on that drive.

       Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr) 
    
There are two versions of grub, grub-pc for BIOS boot and grub-efi-amd64 for UEFI boot on 64 bit PCs. You can boot in UEFI boot mode on live installer and use Boot-Repair's advanced mode to uninstall grub & reinstall grub.
        [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by blaz-mandl on 2020-02-13
I managed to change ubuntu disk to GPT and Uefi mode (I copied ubuntu partitions in gparted to external disk, deleted them from original disk and created partition table for UEFI mode (GPT), then I copied partitions back to original drive (ubuntu)). But now my problem is, that update-grub cant find my ubuntu installation. It only adds windows boot manager. I checked fstab file and UUIDs are correct. Also if I run os-prober, I can see ubuntu on my sda1. I would add ubuntu entry manualy to custom script, but I dont know what is the structure. Can you help me please?

---

### Post by oldfred on 2020-02-13
How did you copy data?
With gpt you cannot use dd on partitions, nor copy MBR to gpt. You can copy data with rsync or cp commands.

With gpt, there are GUIDs in the primary partition table, backup partition table and each partition that must match. Best to either re-install or use gpt tools like gdisk to do a conversion. And if converted you have to reinstall grub as now it needs to see gpt partitions & the ESP.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by blaz-mandl on 2020-02-14
I copied data with ctrl+c and ctrl+v in gparted (copied whole partitions). Its funny, because I managed to boot ubuntu once after conversion. But then I messed something woth grub nd I cant get it in entry anymore. i tried to manualy boot it with grub console, but i seem to cant find vlinuz file on root (its keeps saying file not found)

---

### Post by blaz-mandl on 2020-02-14
I reinstalled Ubuntu on my sda drive. I selected sda to install boot-loader in installation process, but now grub installed to my windows disk (nvme0n1) on efi partition. I didn't want that, because I want to have grub only on my Ubuntu disk. Now I have two entries in UEFI for Ubuntu. One from my windows disk, and one from my ubuntu disk. The difference is, that one on ubuntu disk doesn't have any entries and redirects me directly to grub console. I want to have totally separated ubuntu with grub and efi partition from my windows disk with its own efi partition. If I open gparted, I see that my windows uefi partition has mounting point to /boot/efi. Why did that happen? How can I delete grub from my windows disk and reinstall it on my ubuntu disk?

---

### Post by dragonfly41 on 2020-02-14
Much of the advice I read here is to install EITHER mbr OR gpt.  In fact I have a triple boot configuration where for historical reasons I have an mbr external drive containing Ubuntu and my internal drive is gpt containing Windows and another Ubuntu image. In addition I have a third image (gpt) on an SSD. It is a mixed bag of worms.

Starting afresh I would aim for UEFI across all drives but mixed gpt and mbr drives does appear to work .. somehow.

[This is one of the most informative threads I have read in searching around.]("https://forums.linuxmint.com/viewtopic.php?t=287353")

This prompted me to install rEFInd which can sit alongside grub. I would give it a try since it can be easily uninstalled without affecting grub.

I now create an EFI partition for external drives which is scanned by rEFInd.  Indeed you can power disconnect the main Windows drive and it will still boot into external Ubuntu drive.  I am in favour of drawing a line between Windows and Ubuntu and now for future installations I leave Windows owning its only drive and place Ubuntu in separate drives (HDD or SSD).


[P.S.] [Another helpful blog here on UEFI.]("https://www.zdnet.com/article/hands-on-linux-uefi-multi-boot-my-way/")

---

### Post by oldfred on 2020-02-14
Do you have an ESP on Ubuntu drive?
You can reinstall grub manually or with Boot-Repair to Ubuntu drive's ESP and then delete the /EFI/ubuntu folder in the Windows ESP. You should also rename the /EFI/Boot entries. Windows normally has a copy of its boot loader as bootx64.efi, but grub puts a copy of shimx64.efi as bootx64.efi.

If you want to reinstall, you should know that all the selections on where to install grub boot files do not work with UEFI install. It is Ubuntu's Ubiquity installer as I have installed other distributions and they install where ever you specify. And I have just booted into one of my installs on sdb and installed grub to the ESP on sdb.

We have filed multiple bug reports for years, but Ubiquity still not fixed. I did this on my 20.04 install.
       Posted work around to manually unmount & mount correct ESP during install #23 & #26
[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379"]https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379
      [/URL]
 Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457) 
    
Probably easiest to use Boot-Repair and its advanced options to do a full reinstall of grub. I think that only works from live installer, although you can run reports from your actual install.
If you do it manually you have to install grub-efi-amd64.efi, may have to edit fstab with correct UUID of Ubuntu's drive's ESP and add UEFI boot entry. I think full reinstall of grub does all that.

Then once you know you can boot with newest entry, you need to remove old entries.
Check UEFI entries:
sudo efibootmgr -v
UEFI uses GUID to know which ESP partition to find boot files. Windows should show one & Ubuntu entries the other. But to see GUID also known as  partUUID.
       lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

---

### Post by blaz-mandl on 2020-02-14
When I did ubuntu reinstall, obviously Ubuntu created FAT16 partition for EFI instead of FAT32. Probably that was the reason that ubuntu installed grub on my windows efi partition and mounted it on /boot/efi. I formated ubuntu FAT16 to FAT32 and reinstalled grub onto it. Now it works ok. 
PS.: Is there any option to have all entries on my windows efi partition and no grub on my ubuntu drive? So that I dont chain boot windows with grub (grub -> windows boot manager -> windows) and I can directly boot ubuntu from windows boot manager? Do you even recomend that? Or all entries in my grub would also be a solution (Ubuntu, windows and windows recovery partition). But then I want grub to boot directly to windows if I select windows, not to windows boot manager. But what will happen if I remove ubuntu disk? Would I still be able to boot into windows?

---

### Post by oldfred on 2020-02-14
With UEFI you can always directly boot Windows from UEFI boot menu. Same key you used to load USB flash drive.

In fact you may need that as grub only boots working Windows. So if Windows is corrupted or if it turns fast start up back on, grub will not boot it.
Best to have Windows repair/recovery flash drive disk with repair console, but most times Windows recovery mode will work to fix Windows issues.

Some prefer to always boot from UEFI boot key & remove Windows entry from grub. If mostly  using Windows you can set Windows in UEFI as default & then only boot Ubuntu when desired from UEFI boot menu.

Have not seen Ubuntu create a FAT16 ESP since about 12.04. And that was soon fixed. I believe FAT16 is still valid, but not recommended.

---

