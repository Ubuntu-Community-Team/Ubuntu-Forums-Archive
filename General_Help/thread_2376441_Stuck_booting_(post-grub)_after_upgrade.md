---
title: "Stuck booting (post-grub) after upgrade"
date: 2017-11-02
forum: General Help
---

### Post by Chesslover on 2017-11-02
I have ubuntu with gnome fallback session. After upgrade to 17.10 (partial, because full gave me error - details here: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1510841](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1510841) ), I had to restart computer. Now I can not get to ubuntu. I get to grub menu and after that I get row "Ubuntu:clean, 998941/2949120 files, 8509242/11796480 blocks" and it is just stuck there. Please someone help me

---

### Post by oldfred on 2017-11-02
Before you upgrade, you are supposed to disable all proprietary drivers and ppas as they may not be fully supported in new version and cause upgrade to fail.
Often then better to just install in a new / (root) partition.

I keep 16.04 LTS as my main working install and will keep it until 18.04 is out. But have all the newer versions in additional 25GB partitions just to confirm they work ok. I normally change to gnome-fallback, but have not booted my 17.10 install enough yet to convert. I want to try gnome for a while. But so far I still prefer fallback.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Chesslover on 2017-11-02
Hello, I am not an experienced ubuntu user, so be patient:)
Do you mean I run ubuntu from CD or USB live image? I can not do that, because my keyboard doesn't work in my "boot menu". I manage to use it in BIOS menu to change priorities of disks to boot, but after that I get another menu ("boot menu") and I can not get past that.

---

### Post by oldfred on 2017-11-02
Many BIOS/UEFI require you to turn on a USB setting or enable USB keyboard/mouse settings.
On one of my older systems BIOS worked, Windows worked, Ubuntu worked once booted, but without BIOS setting grub did not work.

What brand/model system? What video card/chip?

You must have been able to boot live installer before as you had it installed?

---

### Post by Chesslover on 2017-11-02
I have USB keyboard enabled in BIOS perkpherals menu. I tried ps2 and usb keyboard. It works everywhere exept in "boot menu". I have Gigabyte GA-MA770-UD3, my video card is Radeon RV730... 

Update: by changing usb port I got keyboard working (if I press num lock I get light on/off), but can not find key which would work (get me to boot usb). If I hit delete key, it reboots, so it's working.

This "boot menu" has rows:
CPU ID
CPU CLOCK
Base Memory
Extended Memory
...
Last row is:
DDR2 at DIMM : 1 2 
(number 2 is underlined and blinking)

---

### Post by oldfred on 2017-11-02
Do not know if your model is similar, but many Gigabyte AMD based boards had IOMMU issues.

 Some Gigabyte boards need acpi=off boot parameter also
Gigabyte GA-990FXA-UD3 and 64bit Xubuntu 16.04 LTS install
[https://ubuntuforums.org/showthread.php?t=2370503](https://ubuntuforums.org/showthread.php?t=2370503)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by Chesslover on 2017-11-02
Update: I edited grub file (removed quiet and added nomodeset) and this is photo of booting process when it stucks: [https://www.dropbox.com/s/4qvlymlzufkd2j5/IMG_20171102_211651.jpg?dl=0](https://www.dropbox.com/s/4qvlymlzufkd2j5/IMG_20171102_211651.jpg?dl=0)

---

### Post by oldfred on 2017-11-02
Did you change IOMMU settings in UEFI?

---

### Post by Chesslover on 2017-11-02
I didn't. How to do that? What is UEFI? Is that BIOS? I don't find IOMMU in my BIOS...

---

### Post by oldfred on 2017-11-02
Acronyms:
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off. 

Is yours an older system that is BIOS only?
Many vendors still call UEFI systems as having BIOS even if not really correct.

---

### Post by Chesslover on 2017-11-02
If I hit delete key on start I get BIOS menu. Don't know how to get UEFI...

---

### Post by Chesslover on 2017-11-03
I managed to run live ubuntu image from DVD and reinstalled ubuntu 17.10 with success:)

The only problem is that I created new username and now I have new /home entry. I would like to get old username files as default /home entry. Should I reinstall ubuntu again and use old username? Wouldn't that create some kind of conflict? Or use Something else option in installation menu and chose right partition and right /home folder?

---

### Post by oldfred on 2017-11-03
You should choose /home as part of new install using Something Else option if a separate partition.
But user id internally is 1000, not your name or login.

If separate partition you can do the last steps of the move to a separate /home. You in effect have already done the first parts which are creating & copying.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

You may need to reset ownership & permissions.
       Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/$USER/.dmrc
sudo chown $USER:$USER /home/$USER

---

