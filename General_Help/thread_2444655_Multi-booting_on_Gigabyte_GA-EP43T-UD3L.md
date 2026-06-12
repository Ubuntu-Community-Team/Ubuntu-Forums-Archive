---
title: "Multi-booting on Gigabyte GA-EP43T-UD3L"
date: 2020-06-02
forum: General Help
---

### Post by levde on 2020-06-02
MoBo GA-EP43T-UD3L has an LGA socket 775 intel cpu. My mobo is a version 1.0. Specs page: [https://www.gigabyte.com/us/Motherboard/GA-EP43T-UD3L-rev-10/sp#sp](https://www.gigabyte.com/us/Motherboard/GA-EP43T-UD3L-rev-10/sp#sp)

This  is an old board, which I bought used. It had the features I wanted.  Except for the 2T hard drive and the PCIE expansion cards, everything is  used or previously owned. 

My machine  wasn't starting with the hardware I installed, so pulled everything and  built it up one piece at a time. It finally started with the IDE hard  drive and  CD drive, so I started  Fedora from a CD disk and installed it  on a 19G IDE drive. This worked fine, so I  downloaded Ubuntu, burned it, and installed it on another IDE drive having 250G (using a swap drawer). This  system was working fine, so I tried again to install the critical new  hardware, the serial 2T Western Digital Blue. This time the system started  without trouble and I was able to download, burn and load Ubuntu Studio,  which I like very much, to my new serial 2 terrabyte WD drive. I was then able to add a few  old drives and a 6T external drive (because I planned to consolidate  decades of old files onto the one large drive). Everything was working  well. 

My plan has been to load windows10  to one of the hard drives. I had a partition set aside on the 2T drive,  and cleared off some of the other drives. A  friend came over yesterday with a copy of Windows 10 (I bought a key),  but the machine would not read any system instructions from the CD deck.  Again, I had used F12 to select the cd drive, and the system locked up.  this cd drive had read other cd-dvd disks, so the problem could have  been in the CD. Once or twice in our repeated attempts to load from the  CD we were told it was corrupt. 

After she left, because I was planning to  multi-boot this system, I began to experiment with loading the systems  from the other drives on which I had installed systems, just as proof of  concept. I used F12 to select the boot disk, and when I selected any but  the 2T drive, the system locked up. It sometimes would not get past the  welcome screen where bios and boot selection are listed, and sometimes  would lock up after the "checking DMI" message. I was able to restart  the system again only after disconnecting all but one of the drives  (2T), and adding the others back one at a  time. 

I used  a partition manager (gparted) to set flags to "boot" or "bios-grub"  (different drives), and restarted the system, adding one drive at a time. Even  with these flags set, only the 2T system would boot. It seems that  multi-boot is out of reach for this Motherboard. 


Is this board too old to accommodate multi-boot? 

Would you call the board faulty because this same model multi-boots for other folks? 
Are there settings in the bios I need to adjust? 

Do  I need to commit to one boot record type on all of my drives? Would  that be MS MBR or Linux GPT? Anticipating Windows 10, am I compelled to  use MBR? 

This board has a memory capacity of 8G. I have two 2G sticks and one 4G stick. Could this be a problem? 

The  Western Digital web site warns against using this drive for either  partitioning or booting (which I didn't know before I bought it), but  techs at the company assured me it would work. So now I am wondering if it is  working. 


I'm going to look up "multi-booting" on wikipedia and elsewhere to see what I can learn. I'll be back to see if anyone has any ideas. Thanks!

---

### Post by oldfred on 2020-06-02
I retired my Gigabyte EP43-UD3L in 2014 with a new UEFI build.  I built it in 2006, but video card blew out motherboard. Replaced original motherboard with the EP43, not sure now what original was, but same CPU and hard drives.

I was going to retire it much sooner, but put a small 60GB SSD in 2011, and it was so much faster/better that I could not justify new system.

Originally had XP on one 160GB drive & Ubuntu on another 160GB drive. Added a 640GB drive with more installs & my data. Then added SSD with another install, then 2 installs using gpt with bios_grub. About 2010 converted 160GB drive to gpt and then all new or reformatted drives including large flash drives are gpt.

Windows only installs in UEFI mode to gpt drives and only in BIOS mode to MBR drives. So you have to have a MBR drive or a blank drive for Windows to install on your system.

Have you updated BIOS to latest available? Are attached the same as your BIOS? I had IDE when still using XP, but had to have AHCI for new SSD. And then XP did not work, so XP was retired. Screen shot is before new SSD.

My installs, only Windows XP and my older data drive were still MBR when I retired system.
```
/dev/sda1    WinXP
/dev/sda2    backup
/dev/sda4    Share
/dev/sdc2    Maverick
/dev/sdc3    swap
/dev/sdc4    MavData
/dev/sdd1    grub
/dev/sdd10    newhome
/dev/sdd11    swap
/dev/sdd12    Puppy
/dev/sdd13    natty
/dev/sdd14    kubuntu
/dev/sdd15    swap
/dev/sdd16    oneiric
/dev/sdd17    server
/dev/sdd18    
/dev/sdd2    Shared
/dev/sdd4    bios_gpt
/dev/sdd5    Karmic
/dev/sdd6    Data
/dev/sdd7    LUCID
/dev/sdd8    Test
/dev/sdd9    OLDg
/dev/sde1    EFI
/dev/sde3    Precise
/dev/sde4    quantal
```

---

### Post by levde on 2020-06-03
OldFred: 

Thank you for answers to some of my questions. 

I'll see if I can pull answers to my questions from what you have said. 

[INDENT]Is this board too old to accommodate multi-boot? *Apparently not, since yours multibooted. *

Would you call the board faulty because this same model multi-boots for other folks? [I]Maybe. 
[/I]
Are there settings in the bios I need to adjust? *This question didn't evoke a response, so probably not. *

Do  I need to commit to one boot record type on all of my drives? Would   that be MS MBR or Linux GPT? Anticipating Windows 10, am I compelled to   use MBR? *You seem to be saying this board allows different drives to have different boot records, but on a this machine Windows will install only to a drive with an MBR, since it is a BIOS machine. *

This board has a memory capacity of 8G. I have two 2G sticks and one 4G stick. Could this be a problem? *You didn't say anything, so probably not. *

The  Western Digital web site warns against using this drive for either   partitioning or booting (which I didn't know before I bought it), but   techs at the company assured me it would work. So now I am wondering if  it is  working. *Not likely a problem. it would be weird! *
[/INDENT]

You asked if I have updated the Bios. I have not. Certainly I can try that. 

Since I haven't been able to get more than one OS to work, and this board does support mult-booting, I'll assume I am doing something wrong. I will investigate software engineered to provide multi-booting. If you or anyone has ideas, please let me know!  

Thanks Again! Levde

---

### Post by oldfred on 2020-06-03
Windows has to have MBR to boot in BIOS mode. Your system is BIOS.
But  Ubuntu can boot from gpt partitioned drives if you have a bios_grub partition. I suggest gpt has it has some advantages over the now 35 year old MBR which all its kluges to make it work on newer systems.

I did change some BIOS settings, I think screen shots showed my defaults, but I did change from IDE to AHCI.

It only boots from MBR whether drive if MBR partitioned or gpt partitioned. The gpt partitioning has a protective MBR, so it has one large gpt partition in MBR, so old partitioning tools see it has been partitioned and do not damage it by trying to make changes. But then it also has the MBR space used for booting. But then actual partition structures are in the gpt tables.

Does BIOS show all your RAM? There were rules in manual on what combinations would work. 
Then does live installer show all of RAM?
Do not remember system, and do not have manual handy. But I thought it required RAM in pairs & all RAM had to be same spec, best if same brand/model RAM, but that may be my newer system. Check manual on RAM requirements.

---

