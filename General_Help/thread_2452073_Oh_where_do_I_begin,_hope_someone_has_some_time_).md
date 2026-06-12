---
title: "Oh where do I begin, hope someone has some time :)"
date: 2020-10-16
forum: General Help
---

### Post by sigurdsk on 2020-10-16
Well I have 3 SSD disks in my computer. I would like to perhaps run a couple of different Linux versions on them or even maybe to RAID system on them.
Besides that... They seem to be crashing, something is going wrong. Like now when i try changing a disk I get this message: target is bussy.
I get that. ON the other disk that i just mount that I cannot access I get this message when trying to read from it: structure needs cleaning.
I would like to know what it means.. and uhm oh if my hard disk is gone :(
And also a program that can start my computer in linux so i can delete, format and rewrite the disks to ext3 and stuff if i cannot fix this 
and try from scratch but only got CD-ROm- I DO HAVE a Kingston 20+ gb thumb drive. So any linux version that can fit on it I could try,
but ubuntu is my favourite but I just wanna fix the disks so I dont have any more annoing issues. 
thanks

---

### Post by HermanAB on 2020-10-16
First decide what you really want to do, then divide and conquer:  
Install one SSD and get it to work, before adding another.

---

### Post by helen314 on 2020-10-16
I would suggest the following approach.
 1. Casually scan thru this forum to find Ubuntu version with LEAST issues.

   I have been using 16.04.6  for years, after &#8220;upgrading &#8221; to 16.04.7 &#8220; I cannot watch CNN.
 
 
 2. Use whichever  computer has UEFI hardware setup , life will be easier then with DOS.

 3. Download selected Ubuntu version ISO  file to your USB stick.
 4. Choose your PC WITH your single  SSD and boot the ISO file.
 5. Pick  &#8220;Try  Ubuntu &#8220; at the prompt, it gives you better view what will come next.
 5a. Run &#8220;load Ubuntu &#8220;  (or something like that) application.
 6. Follow the instructions (on screen) and hopefully you will see your SSD to install Ubuntu onto.  
 7. Make sure you pick UEFI if asked .
 8. In your case I would do &#8220;clean&#8221;  (erase disk) install.  
 8. Use default settings as much as possible
 9. It takes  some time to finish the install from USB .
 10. Follow the instructions&#8230;.
 
 
 When you are ready to play with RAID, post it here.

---

### Post by oldfred on 2020-10-16
UEFI or BIOS based system?
What brand/model system? 
What video card/chip?
Some need special parameters, others just work.

Have you updated UEFI and SSD firmware on all the SSDs. That often avoids unknown issues.

Are you unplugging & replugging in drives?
Then how are they connected? SATA, eSATA, USB, or Other?

---

### Post by Impavidus on 2020-10-17
> **sigurdsk said:**
> Well I have 3 SSD disks in my computer. I would like to perhaps run a couple of different Linux versions on them or even maybe to RAID system on them.
Besides that... 
This sounds very confused. I can't give you any solid suggestions based on that. What do you want to do with that computer? Can you be more specific about the hardware?

> **helen314 said:**
> I would suggest the following approach.
...


There are a few things in there that I wouldn't do or wouldn't suggest to new users.
1: If you have recent hardware, you need a recent kernel and therefore a recent release of Ubuntu. These days (october 2020) I would suggest 20.04 LTS, or if you have some really special needs 18.04 LTS. For bleeding edge hardware you may need 20.10, which will be released very soon. Most applications get frozen when the OS is released, so old versions of Ubuntu come with old versions of applications. 16.04 LTS will reach end of life in six months and should not be installed. The older a release is, the more issues with it have been discussed on the forum and the more of these issues were caused by a bug that has been fixed by now. For beginners it's best to use an LTS release.
2: UEFI is best, but if you're not dual booting with Windows 8/10, BIOS (or UEFI in legacy mode) works too. On some older UEFI hardware (about 8-10 years old), the UEFI may not be standards-conforming, making it hard to use other than in legacy mode.
8: With multiple hard drives it's best to use manual partitioning.

---

### Post by helen314 on 2020-10-17
[QUOTE=Impavidus;13993332]This sounds very confused. I can't give you any solid suggestions based on that. What do you want to do with that computer? Can you be more specific about the hardware?



There are a few things in there that I wouldn't do or wouldn't suggest to new users.
1: If you have recent hardware, you need a recent kernel and therefore a recent release of Ubuntu. These days (october 2020) I would suggest 20.04 LTS, or if you have some really special needs 18.04 LTS. For bleeding edge hardware you may need 20.10, which will be released very soon. Most applications get frozen when the OS is released, so old versions of Ubuntu come with old versions of applications. 16.04 LTS will reach end of life in six months and should not be installed. The older a release is, the more issues with it have been discussed on the forum and the more of these issues were caused by a bug that has been fixed by now. For beginners it's best to use an LTS release.

Respectfully disagree and stand-by my original. 
The original poster did not indicated which hardware is he going to  experiment with / use and what is his current OS version. If it works , don't fix it , do not  "skip" to the  "latest" which may not  always work ( for you) - for whatever reason. 



2: UEFI is best, but if you're not dual booting with Windows 8/10, BIOS (or UEFI in legacy mode) works too. On some older UEFI hardware (about 8-10 years old), the UEFI may not be standards-conforming, making it hard to use other than in legacy mode.

OP intents to experiment with different Ubuntu versions , perhaps multiboot is in the works...


8: With multiple hard drives it's best to use manual partitioning.

Huh?  I specifically suggested to use SINGE SSD (to start with) , so why such comment?
Even  if he used all 3 drives during install - I still believe to "follow the instructions" and let the ISO do the work - automatically setting the 3 Linux partitions. 

/QUOTE]

---

### Post by oldfred on 2020-10-17
Ubuntu in UEFI boot mode only installs grub boot loader to the ESP on the first drive. First drive will be defined by UEFI/BIOS and even can change. 
The selection option during install for UEFI, does not work with Ubiquity installer. As long as you want grub on first drive, it is no issue. And that grub can boot other installs on other drives.

But if you want each drive to have boot loader, you either have to reinstall grub if you do not want it on first drive, disconnect other drives, so drive seen a first drive, or do a work around to get grub to install to the ESP/drive you want. Very important if drive is an external drive, but if internal not as critical.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive. 
grub
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

---

