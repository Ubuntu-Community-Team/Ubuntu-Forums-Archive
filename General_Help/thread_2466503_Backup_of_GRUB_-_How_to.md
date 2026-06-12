---
title: "Backup of GRUB - How to"
date: 2021-08-29
forum: General Help
---

### Post by robert71 on 2021-08-29
Hi Everyone. 

                I would like to make a backup of my grub installation so that i can reinstall my ubuntu installation and then restore GRUB. 
So that i can keep my current boot loader configuration. 

Anyone knows the steps to accomplish this, 

thanks in advanced.

---

### Post by oldfred on 2021-08-29
Generally you do not need to backup grub.
You just reinstall it. That will restore defaults on settings.
I do backup /etc/default/grub & /etc/grub.d/40_custom as I have modified them & restore those after new install of grub.
I just copy into /home so my normal backup of /home includes those files.

You can backup /EFI/Boot & /EFI/ubuntu if UEFI.
But the entry in UEFI to load the ubuntu entry depends on the GUID/partUUID of the ESP - efi system partition. So if not same ESP, you have to create new UEFI boot entry. Reinstall of grub does that with efibootmgr. You can restore ESP & use efibootmgr yourself to create new UEFI boot entry, also. But in most cases, it just is easier to reinstall grub.
I always keep a flash drive with current version of Ubuntu, so I can use it to reinstall grub if needed.

---

### Post by robert71 on 2021-08-29
Thing is i have Win10 installed and Ubuntu, My ubuntu is broken so im going to reinstall. I am also using proxmox on another drive in the system. 

All are handled by the GRUB boot loader. 

There will be no change to the disks or their configurations just a reinstall of Ubuntu.

So if i get what youre saying is that i can backup :  

1. [COLOR=#000000]backup /etc/default/grub & /etc/grub.d/40_custom
2. [/COLOR][COLOR=#000000]backup /EFI/Boot & /EFI/ubuntu

[/COLOR][COLOR=#000000]upon re-installing ubuntu if i restore these files i should be able to go back to my old bootloader configs ??? 

[/COLOR]

---

### Post by oldfred on 2021-08-29
Without seeing details difficult to know for sure.

I periodically run Boot-Repair report, just to document my own system.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by robert71 on 2021-08-29
Hello here is the report: 

[https://paste.ubuntu.com/p/W7BrnFvc4r/](https://paste.ubuntu.com/p/W7BrnFvc4r/)

---

### Post by oldfred on 2021-08-29
Do not run any autofix with Boot-Repair.
If reinstalling grub only use Boot-Repair's advanced mode booted in UEFI mode & choose one install & one ESP.

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You have multiple drives some gpt & some MBR.
You have two ESP with different boot loaders & grub BIOS boot loaders in most drives.
Since UEFI, you always should use UEFI and only boot in UEFI mode.

You can see details on UEFI boot entries. UEFI uses GUID to find ESP partition. This is the command used in report.
sudo efibootmgr -v
This will show which partition has GUID that UEFI is looking for.
lsblk -e 7 -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

It looks like Windows & one Ubuntu entry boots from 
75423061-9f85-4995-8404-8b64ad302813
And another Ubuntu entry & Proxmox use this ESP.
e4bc227b-1c89-4a15-88ac-36645ac62aaa

Report does not auto mount encrypted LVM partitions. If you want those in report you have to mount & decrypt before running report.

It looks like you are not using NVMe drive for booting?
It is large enough for Windows & Ubuntu / & others if desired. And then have data on HDD if needed. And HDD for backup.

Since UEFI system and installs are UEFI, you may eventually want to convert MBR(msdos) drives to gpt. Best to have full backups. If not boot drives you can convert. Boot drive conversion gets more complicated & often better to just do new install & restore from backups.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by robert71 on 2021-08-30
@[[COLOR=#C61919]oldfred[/COLOR]]("https://ubuntuforums.org/member.php?u=852711") 

Thank you for taking the time to reply. 

This is alot of info to go through so im taking some time to process it all and go through the material you sent,

---

### Post by robert71 on 2021-09-01
After reading the materials im guessing the safest thing to do would be to backup the ESP. 

This way if i re-install Ubuntu and somehow after running [COLOR=#000000]Boot-Repair [/COLOR]my system still does not recognize the 
bootloaders or how i have them setup i can always restore my ESP after booting from a ubuntu live cd etc... 

would this be a good assumption ? Does that make sense at all ?  Sorry if im not quite getting this 

Also the Nvme drive is used to allow a the calculation of  flow data and microparticle simulations so I don't use it for booting, 
i just need the speed to be able to provide those numbers really quickly.

---

### Post by oldfred on 2021-09-01
Boot in UEFI mode is from UEFI boot entries which you can see with efibootmgr. 
See also
man efibootmgr
Only showing part of mine, as I have not housecleaned it recently.
```
[FONT=monospace][COLOR=#54ff54]**fred@z97-focal-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo efibootmgr -v [/COLOR]
[sudo] password for fred:  
BootCurrent: 0001 
Timeout: 1 seconds 
BootOrder: 0001,0003,0002,002C,002F,0030,001C,0000,0025,0004,0031,0032 
Boot0001* ubuntu        HD(1,GPT,[COLOR=#ff0000]3195d314-ce88-42ac-beac-d9f80289ac11[/COLOR],0x800,0xf9dcd)/File(\EFI\UBUNTU\SHIMX64.EFI) 
Boot0002* focal HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\FOCAL\SHIMX64.EFI) 
Boot0003* impish-k      HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\IMPISH-K\SHIMX64.EFI)
[/FONT]
```

The UEFI boot entry uses the GUID/part UUID of ESP to know where to find boot files. If new ESP, then you will need new entry in UEFI to find correct ESP. Grub uses efibootmgr, but you can manually create entries also if other boot files are in ESP.

Again only showing part of output as I have many partitions:

```
[FONT=monospace][COLOR=#54ff54]**fred@z97-focal-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid [/COLOR]
NAME    FSTYPE   SIZE FSUSED LABEL PARTLABEL MOUNTPOINT UUID       PARTUUID 
sda            119.2G                                                                             
&#9500;&#9472;sda1  vfat   499.7M  16.3M  efi  efi       /boot/efi  F626-A4D4  [COLOR=#ff0000]3195d314-ce88-42ac-beac-d9f80289ac11[/COLOR]
[/FONT]
```

You then need all the files grub installs into /EFI/ubuntu & /EFI/Boot.
And the /EFI/ubuntu/grub.cfg file must be a configfile entry to your full grub.cfg in the default boot usually in /, but could be in /boot.
And correct ESP must be in /etc/fstab so any reinstall or major update to grub is to correct ESP.

While you can restore all the files, edit if necessary, add new UEFI entry, it really is just easier to reinstall grub.

---

### Post by robert71 on 2021-09-02
Ok Thanks i think I got it now. 

Will have a shot at reinstalling this weekend, 

Thanks for taking the time to assist. 

regards,

---

