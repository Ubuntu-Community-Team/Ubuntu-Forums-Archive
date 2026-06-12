---
title: "Help moving  GRUB2 config"
date: 2014-02-04
forum: General Help
---

### Post by Melvin_Cook on 2014-02-04
I have a netbook (it is what I use to tinker around) with a 250 GB HDD with 4 primary partitions:
[LIST=1]
[*]sda1 50 GB ext4 mounted to /
[*]sda3 ~162 GB ext4 mounted to /home
[*]sda4 ~20 GB ext4 empty and unmounted
[*]sda2 3 GB swap
[/LIST]

I want to move my grub config to sda4 along with my live isos. I want to be able to install any distro and not affect those GRUB settings (or be able to return them quickly), and boot the live discs from grub. I know how to add them to the grub menu, but I want to move GRUB's config to the other partition. I know I can move /boot, but if I change to a wrong distro it may not boot.
Thank You.

Edit: I had one idea: install a small OS to sda4 and run grub from there, but every time I install a new OS, I will have to change the default boot. If it is set to boot the last booted one, I would have to remember to change it back. I want a way to do it without doing any of those things.

---

### Post by Herman on 2014-02-05
The conventional way to do things with GRUB2 would be to add your CD boot stanzas to  a file in /etc/grub.d/ and name it something like 06_custom. Run the  chmod command and set it to 755. Run update-grub. Your CD boot entries should be added every time update-grub is run after that.
If you want to install different operating systems frequently you could  use a USB flash memory stick and install the new operating system's  GRUB2 to the stick so it will leave your sda MBR alone. Just boot Ubuntu and run update-grub each time you install a new operating system to have it added to your Ubuntu GRUB's boot menu.

There's nothing wrong with having fun though. Your idea of installing GRUB2 in sda4 sounds like what we used to call a 'Dedicated Grub Partition' back in the Legacy Grub days. You could make sda4 your 'Dedicated GRUB2 Partition' by re-installing GRUB2 there.
```
e2label /dev/sda4 GRUB2
```
```
sudo grub-install --root-directory=/media/GRUB2 /dev/sda
```
Where: '/media/GRUB2' is the mount point for the file system I want to have GRUB files created in
Where: You want to make a new /boot/grub directory in the GRUB2 partition and fill it with GRUB2 files.
Where: '/dev/sda' is the hard disk in which I want to write the stage1 code to MBR in
Your GRUB2 partition should be mounted before running this command or it won't work.
That command creates a new /boot and /boot/grub/ directory if one doesn't already exist, and creates or refreshes GRUB files in /boot/grub, all except for grub.cfg.
If you want a GRUB Menu you need to make a grub.cfg file and copy it to /boot/grub.
You can make your own grub.cfg file and customize it in any way you like. It won't be under the control of any operating system so you will be edting it manually each time like we used to back in the Legacy Grub days.

---

### Post by oldfred on 2014-02-05
Glad to see Herman posted here. He was  one of the main sources, that I learned to create a dedicated grub legacy partition from. 
But with grub2 that is not required. But I do install grub2 to every device and I still use Herman's commands to install grub2 to every flash drive, manually edit grub.cfg and boot ISOs, or boot stanza's for installs on hard drive.

But from a hard drive. I copy all ISO to another partition and add a configfile in grub2's 40_custom. Then in iso folder in other partition I add the config file with all my other boot stanza. Then I do not have to run sudo update-grub everytime I change an ISO ( always forgot and had to reboot to run it.)

 this will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

My ISO are on a different drive or hd2 and in partition 4. I also turn off os-prober and add only other installs boot that I want since I have too many old installs.
      
 gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu after any change
sudo update-grub

    
```
menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

```


This is my first entry and some notes to myself, so I do not forget what I am doing. I also have gpt partitioning, but still boot with BIOS, so I have to add the insmod gpt. I have so many ISO that I run a small script to add desciptions to make it easier to copy & edit titles & ISO names.

This is livecdimage.cfg file in my iso folder in my partition.
```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

menuentry "Ubuntu 14.04 Trusty ISO 64bit" {
    set isofile="/iso/trusty-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by Herman on 2014-02-05
That's the best way to do it oldfred! So you retain your Ubuntu's GRUB as the main bootloader and when you want to boot an iso, you boot via the config file in the iso partition. Very cool, you have the best of both worlds. Fully customisable where you need it but still automatic and worry free for the main part. I like that, you guys are very inspiring, I might go and  make a setup like that myself. It's been a while since I have taken the time have fun with grub2.  Thanks oldfred! :)

---

### Post by oldfred on 2014-02-05
@Herman
I use your commands to create a flash drive with grub2. And manually edit grub to boot ISO. Somewhat a combination of your commands and drs305's commands to make it work.
I have been planning a new system for now 2 years, so all new drives are gpt partitioned so I can more easily use with UEFI. But I also now partition larger flash drives with gpt and have space for a future efi partition at beginning. 

I somehow copied a Windows repair DVD to a flash drive and made it a bootable Windows repair drive. But it was tiny & flash drive was large enough for several more ISO. So I installed grub2 to Windows partition and created a boot stanza to boot Windows. The only thing to be careful of is you can only have one /Boot folder. Both grub & BCD must be in same /boot folder but you may get both /Boot & /boot. So if grub is wrong move it or move BCD.
Then I shrank Windows partition, created ext4 partition without journal and copied gparted, parted magic and a couple of other repair ISO into Linux partition. MultiUse repair flash drive.

---

### Post by Melvin_Cook on 2014-02-05
I am using this way (since I am still a noob when it comes to editing files like this or anything other than simple command line things), and I am going to use grub-customizer to edit it for now. At this moment, I am coping the isos and hope everything goes well.

---

