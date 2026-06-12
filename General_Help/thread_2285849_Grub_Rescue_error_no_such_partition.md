---
title: "Grub Rescue error no such partition"
date: 2015-07-08
forum: General Help
---

### Post by sports fan Matt on 2015-07-08
Howdy all,

I have a Toshiba L875 S7209 with Intel Graphics that I screwed up the partitioning several years ago and I'm now just getting around to try and fixing it.  When it boots I gewt the error: Grub Rescue error no such partition, entering rescue mode: grub rescue prompt.

I do not have a Windows 7 disk and when I try and run an older Ubuntu disk, nothing loads.

My question is: Do you think the data is still there from W7 and Ubuntu 14.04 and how hard of a fix could this be?

Matt

---

### Post by yancek on 2015-07-08
How old is this hardware?  Can you post some details on it particularly RAM?  
Grub is looking for a partition which doesn't exist which is the cause of the error.  You will need to boot an Ubuntu (or other Linux) Live CD/flash drive.  Get the output of the sudo fdisk -l command or the output from GParted showing your partitions.  You could also get the boot repair script from the site below and run that on any Linux and post the output of the option to "Create BootInfo Summary".  Without more information, there isn't enough information on your problems for anyone to do but guess.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sports fan Matt on 2015-07-08
I'd say two years old.  Toshiba Satellite L875-S7209 17.3" HD LED Laptop - Mercury Silver-4 GB
Hard Drive	640 GB Intel Graphics. [http://www.amazon.com/Toshiba-Satellite-L875-S7209-17-3-Laptop/dp/B00AIJ3D2U/ref=cm_cr_pr_product_top?ie=UTF8](http://www.amazon.com/Toshiba-Satellite-L875-S7209-17-3-Laptop/dp/B00AIJ3D2U/ref=cm_cr_pr_product_top?ie=UTF8)

I've tried an older 9.04 , 9.10 CD with no success, because the same error pops up.  I even tried to download boot repair from USB but can't change the partitions because I cant get into the bios.  

I'll try the  sudo fdisk -l command..Thanks!

---

### Post by sports fan Matt on 2015-07-08
Wonder why i'm getting an "unknown command" sudo fdisk-l?

---

### Post by oldfred on 2015-07-08
You need a current version Ubuntu, not any of the now obsolete verisons of Ubuntu. 
Version of Ubuntu at minimum must be a year newer than hardware to have good support for that hardware. Older software will not have drivers for new hardware.

Toshiba's usually use f12 for one time boot key and f2 for UEFI/BIOS. You may have an early UEFI system but Windows in BIOS mode? Need Boot-Repair info to know how systems are installed.
To get into UEFI/BIOS you may need to fully shutdown, remove battery and hold power key for 10 sec to drain residual power. So system has total cold start, and immediately press f2 or correct key to get into UEFI/BIOS.

---

### Post by sports fan Matt on 2015-07-08
Let me try to get into BIOS

---

### Post by sports fan Matt on 2015-07-08
Can't get into BIOS even after powering down and removing battery.  Could the next step be purchasing a 14.04 disk from the UK and going from there and picking this up when it arrives?

---

### Post by oldfred on 2015-07-08
Getting into BIOS has not relation to which version of Ubuntu or any system you have. 

Always best to have a current version bootable live DVD or flash drive so you can make repairs. But easier to just download it.
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

If Ubuntu is still bootable, you may be able to manually boot from grub rescue.
      
 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)


 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg

   
Or, if above does not work. Assumes no separate /boot. And also change sda5 to correct partition ( or all 5's must be same partition with Ubuntu).
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

### Post by sports fan Matt on 2015-07-08
Since I have a fresh set of Cd/r's, would it be better to download a fresh 14.04 or Super Grub Rescue disk>

---

### Post by sports fan Matt on 2015-07-08
And this had Windows 7 installed, not 8, if that helps

---

### Post by sports fan Matt on 2015-07-08
Also when I tried these commands:set boot=(hd1,msdos2)
set prefix=(hd1,msdos2)/boot/grub
insmod normal

I got an error of " hd1 cannot get C/H/S values"

same result if the variables are flipped

---

### Post by oldfred on 2015-07-08
What did ls command show?
And you can continue the ls to see if you have found Linux. With each drive & partition. 
 ls (hdX,Y)/    
ls (hdX,Y)/boot

And usually sda1 & sda2 are Windows, so partitions 1 & 2 would not be Linux formatted.

---

### Post by sports fan Matt on 2015-07-08
(hd0, msdos2) (hd0, msdos1)

So does that mean the partitions are somewhat intact?

---

### Post by oldfred on 2015-07-08
So it only shows two partitions? That typically is Windows unless you totally erased Windows and just have Ubuntu?
And if just Windows grub in MBR cannot find the Ubuntu partition for the grub menu & rest of grub to boot with.
Did Linux partitions get deleted? Did you reinstall or update Windows, as it does not see Linux partitions and rewrites partition table without Linux partitions. Testdisk often can fully restore it if drive was not otherwise modified.

---

### Post by sports fan Matt on 2015-07-08
I honestly cant remember.  I had this pc sitting in the closet and just had time to mess with it. It had Windows 7 on it before hand though...is there a way to check ?

---

### Post by oldfred on 2015-07-08
The only way we can tell anything is to boot Ubuntu and run Boot-Repair and post link to summary report.

---

### Post by sports fan Matt on 2015-07-09
So if I can't get into Ubuntu (because it won't get into bios even after powering down) im stuck.

---

### Post by VMC on 2015-07-09
> **sports fan Matt said:**
> Wonder why i'm getting an "unknown command" sudo fdisk-l?

Your missing a space in that command. It's ```
[FONT=courier new]**[SIZE=3]sudo fdisk -l[/SIZE]**[/FONT]
``` [that's a "el" and not a "1". enlarged font so you can see the difference]

---

### Post by oldfred on 2015-07-09
You should always be able to get into BIOS.
Did you try removing battery on motherboard.

Are you pressing correct keys to get into BIOS, while often del or f2, some brands require various key combinations. Check what is correct for your system.

---

### Post by sports fan Matt on 2015-07-09
I haven't because I'd have to have someone help me do that just because of my paralysis. I'll look for the correct keys to a Toshiba and I did order a 14.04 boot CD last night.  Once it arrives, would that boot into Ubuntu even with the GRUB Rescue?

---

### Post by oldfred on 2015-07-09
My old 2006 Toshiba uses f2 for BIOS and f12 for one time boot key. It also gave me the option to boot from flash drive when I had a valid bootable flash drive plugged in. BIOS screen shows for a few seconds and says what keys to use.

You should be able to use f12 and boot DVD.
Are you not able to download ISO and write to DVD or flash drive.

---

### Post by sports fan Matt on 2015-07-09
I have blank iso's ...In theory the machine SHOULD work if I can "jump" it into the BIOS.  let me try digging it out again and going back over the steps.  The issue is it's not able to recognize that I'm trying to boot from CD Rom.

---

### Post by sports fan Matt on 2015-07-09
MAKING PROGRESS!  I can now get into BIOS and change boot so a boot summary will appear shortly!

---

### Post by sports fan Matt on 2015-07-09
Now at a Ubuntu live session. What specific info do you need?

---

### Post by oldfred on 2015-07-09
You should be able to go into terminal in live installer, add ppa and run Boot-Repair. 
Run the Summary report and post link it gives so we see all your data.
Since live installer saves nothing, if you reboot live installer you have to reinstall Boot-Repair.
Or you can download Boot-Repairs own live version which includes Boot-Repair. I think it is currently based on Lubuntu so it fits on a CD, where now Ubuntu needs DVD or flash drive.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sports fan Matt on 2015-07-09
Turns out you were right, Fred.  I was just going to go from live session to 13.04 then upgrade to 14.04 when I saw this.   It DID have Windows 7 on it and I will just upgrade to 14.04, is that a better solution?

---

### Post by oldfred on 2015-07-09
I did upgrades every 6 months from 2007 thru 2009. And every upgrade I had issues.
I did a new clean install with 9.10 as I was converting from 32 bit to 64 bit and that install just worked. So I like clean installs. 

But others have reported good success with updates. What seems important with upgrades is that you have no proprietary drivers like nVidia and no ppa for special software, even Boot-Repair.
If ppa for new version does not exist then upgrade stops and then nothing works. While usually repairable often not easy.

Or whatever you decide to do, make sure you have all your data and /home backed up. Then you can easily restore your data & configurations. If you have installed a lot of applications, best to export that list also.

---

### Post by sports fan Matt on 2015-07-11
One thing I did see is the fact I have two Windows 7 entries.  I'm not sure why.  [http://paste.ubuntu.com/11863565/](http://paste.ubuntu.com/11863565/)

---

### Post by yancek on 2015-07-11
The first partition (sda1) is the boot partition for windows while the second partition is your windows system files.  This is show in the output of the parted -l command near the bottom of your boot repair output.

---

### Post by oldfred on 2015-07-11
There were many users who deleted the 100MB Windows boot partition as they did not see it in Windows and did not know what it was for. But once that is deleted, you had no bootmgr nor BCD and system was difficult to restore, if you did not have backups.

So one of the first things Boot-Repair does is copy bootmgr & BCD to main install. Then either partition is bootable. And then grub2's os-prober sees both as bootable and adds boot entries.

If you want you can manually add your own single Windows boot entry and turn off os-prober so it does not add entries.

---

### Post by sports fan Matt on 2015-07-11
Have you done this?  Is it easy or hard?

---

### Post by oldfred on 2015-07-12
I always edit my grub.cfg. Usually I just add my own boot entries into 40_custom and turn off os-prober. I also regularly houseclean old kernels.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[URL="http://ubuntuforums.org/showthread.php?t=2076205"]http://ubuntuforums.org/showthread.php?t=2076205

[/URL]
 In /etc/default/grub I added this line for os-prober:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
```
GRUB_DISABLE_OS_PROBER=true
```

      
 gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub
     
If you install another system, and do not know your own boot stanza to add, you can either comment out the os_prober line or change to false.

---

