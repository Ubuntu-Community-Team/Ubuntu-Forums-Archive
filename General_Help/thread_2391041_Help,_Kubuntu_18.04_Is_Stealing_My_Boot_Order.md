---
title: "Help, Kubuntu 18.04 Is Stealing My Boot Order"
date: 2018-05-05
forum: General Help
---

### Post by Rocky_Bennett on 2018-05-05
Hello All,
 I need some help with this problem, or at least some suggestions that  I might be able to try. I am running Kubuntu 18.04 and Windows 10 1803  on two separate SSDs. My motherboard is an Asus 97 A. My problem is that  when ever I use Kubuntu it changes the boot order of my motherboard to  boot from the Kubuntu SSD first. My Microsoft Windows installation does  not create this change in boot order, just the Kubuntu installation.
  
 I really like the way that I have my system set up. I do not use GRUB  as a boot selector, I simply use the boot menu provided in the Asus  motherboard by pressing F8 during start-up. But I really want my Windows  SSD to be my first boot device because it makes life so much easier  when there is a Windows update. Linux Mint does not change my boot  order, either does Ubuntu 17.10 or Fedora 27. It is just the newest  version of Kubuntu that is wreaking havoc with my motherboard's boot  order. I know I can change and use a different distro but since Kubuntu  18.04 is an LTS distro, I kind of wanted to stick with this for awhile.
  
 Does anybody here have any ideas on this? Thanks in advance.
  
 Rocky

---

### Post by dino99 on 2018-05-05
As you have several linux OSs installed, then without grub, how can you select the one to load ? F8 can only select the device to start with.

---

### Post by Rocky_Bennett on 2018-05-05
I am so sorry for the confusion. I am a distro hopper on one of my free SSDs, I only have three SSDs connected to my motherboard. On my free SSD I have recently tried several different Linux distros, and Kubuntu 18.04 is the only distro that actually changes my boot order. I am not running all of these distros at the same time.

Rocky

---

### Post by oldfred on 2018-05-05
I also have Asus z97 and assumed it was my UEFI. 
As I only have sda as boot drive until now, and only occurred when I did a test install of 18.04 to an external USB SSD.

I know with my other system which is Gigabyte it remembers last system booted and always boots or reboots into that.  But that example was where I installed Fedora to sdb & its boot into the ESP on sdb. I have not checked for settings to see if that is something I can change.

Do you have different ESP, or an ESP on each drive. That could be part of issue as UEFI likes to boot from one ESP.

---

### Post by Rocky_Bennett on 2018-05-05
Thanks oldfred for that info. I will check into that ESP and post back once I find out for sure.

Rocky

---

### Post by Rocky_Bennett on 2018-05-05
I just checked and I have a healthy EFI partition on each SSD. I was thinking that I just might begin to use GRUB and select Windows to boot first. How hard would it be to add GRUB to my system? I assume a simple command in Kubuntu will add GRUB, is this true?

Thanks

---

### Post by adelpozoman-f on 2018-05-05
If you dont want to mess with your grub you could disconnect the other SSDs when installing on one, so each of them have their own bootloader and you boot on the one you want using the BIOS

---

### Post by oldfred on 2018-05-05
I do like to have ESP on each drive. 
But because I install with drives connected, grub always installs (with Ubuntu) to ESP on first drive or sda. It does seem that those with newer NVMe drives it finds the ESP on that drive. Not sure what it does with two NVMe drives?

Grub should be installed in the ESP your drive.
I usually use Boot-Repair to see details and just to document my system.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

And default settings in fstab to mount ESP now give no permissions (umask=0077  ). 
Boot-Repair changes to defaults and I do also. With 14.04 it used defaults, but I assume they changed to no permissions for security reasons as defaults would give access to any process. FAT32 only has permissions set at mounting time.

---

### Post by Rocky_Bennett on 2018-05-11
I was unable to correct this booting issue so uninstalled Kubuntu 18.04 and installed Ubuntu 18.04 instead. The issue has now been resolved.

---

### Post by Rocky_Bennett on 2018-05-11
> **adelpozoman-f said:**
> If you dont want to mess with your grub you could disconnect the other SSDs when installing on one, so each of them have their own bootloader and you boot on the one you want using the BIOS



Hello,
That is how I always install any new distro. I always disconnect every SSD and hard drive except the target. I have found that this makes installation much easier. Unfortunately something happened during my Kubuntu installation which I could not figure out so I just moved on.

Rocky

---

