---
title: "Grub Shows Windows 10 In The Menu But Gives An Error When Selected"
date: 2019-03-13
forum: General Help
---

### Post by shanasman450 on 2019-03-13
As the title states, I'm having some issues with a dual boot system. Grub loads fine, Ubuntu boots fine, but when I try to boot into Win10 from grub is tells me something like "the efi partition cannot be found" (or something like that anyway, I'll have to look when I get home for the exact message). I've tried sudo update-grub multiple times as well.

I'm not sure if it has something to do with my boot settings. I don't seem to be able to disable secure boot. I'm on an Asus ROG Strix B450-F Gaming motherboard and the secure boot options are Windows 10 and OtherOS so it's not exactly and On/Off type selection.

Any help would be greatly appreciated. Thanks in advance ):P.

---

### Post by yancek on 2019-03-13
> when I try to boot into Win10 from grub is tells me something like "the efi partition cannot be found"

The first thing you would need to do is to verify whether you do in fact, have an efi partition.  You can do that from Ubuntu by opening a terminal and typing in the following command:

```
sudo parted -l
``` 

That's a lower case Letter L in the command and if you have an EFI partition, it will show in the output.  It will also show whether the partition table is gpt or not.  

It might be simpler to use boot repair which you can get at the site below.  Use the 2nd option when booted into Ubuntu, use the ppa and run it per instructions selecting the Create BootInfo Summary option and do NOT try to make any repairs.  When boot repair finishes, you should get a link which you can post here for members to view and make suggestions.  

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by shanasman450 on 2019-03-13
Will do. I'll throw the link up as soon as I get off work.

---

### Post by oldfred on 2019-03-13
"Other OS" is Secure Boot off as somewhere fine print will say if installing Windows 7 use Other OS as Windows 7 does not support UEFI Secure Boot.

Have you checked that you have latest UEFI from Asus? Even new motherboard may have updates.

Grub only boots working Windows and Windows 8 or 10 has always on hibernation called fast start up. Then grub cannot boot it.

Did you install Windows in UEFI boot mode?

---

### Post by shanasman450 on 2019-03-13
```
taylord@taylorgang:~$ sudo parted -l
[sudo] password for taylord: 
Model: ATA CT500MX500SSD1 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   120GB  119GB  ext4


Model: ATA CT1000MX500SSD4 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   629MB   105MB   fat32        EFI system partition          boot, esp
 3      629MB   646MB   16.8MB               Microsoft reserved partition  msftres
 4      646MB   1000GB  1000GB  ntfs         Basic data partition          msftdata

```

There's the output for parted. There is indeed an EFI partition.

And here's the bootinfo summary: [http://paste.ubuntu.com/p/ttYBrxSdRk/](http://paste.ubuntu.com/p/ttYBrxSdRk/)

---

### Post by shanasman450 on 2019-03-13
> **oldfred said:**
> "Other OS" is Secure Boot off as somewhere fine print will say if installing Windows 7 use Other OS as Windows 7 does not support UEFI Secure Boot.

Have you checked that you have latest UEFI from Asus? Even new motherboard may have updates.

Grub only boots working Windows and Windows 8 or 10 has always on hibernation called fast start up. Then grub cannot boot it.

Did you install Windows in UEFI boot mode?

Not sure. It's been a while since I installed. I believe it was though. Anyway, fastboot is off and secure boot is set to other os, so that should be fine.

Edit: Yes, my BIOS/UEFI is up to date.

---

### Post by oldfred on 2019-03-13
Does Windows boot ok from UEFI boot menu?

Grub only boots working Windows and that includes Windows cannot be hibernated. And fast start up sets the hibernation flag.
Normally script will mention that, but I do not see it.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
Note that Windows updates may turn fast start up back on, then you have to boot Windows from UEFI and turn it back off to use grub to dual boot.

Report does show this:

 GPT PMBR size mismatch (234441647 != 976773167) will be corrected by w(rite). 

I might try this on both drives:

 [URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
      [/URL]
 sudo gdisk /dev/sda
Command (? for help): 
    
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :

---

### Post by shanasman450 on 2019-03-14
I'm able to boot into windows from grub now. Strange thing is, I didn't change any setting anywhere though. I got home yesterday and sat down in front of the computer, turned it on, and mindlessly selected windows from grub before I could even remember that option doesn't work...but it worked?

Kind of confused by that, but it works so I'm not complaining.

---

