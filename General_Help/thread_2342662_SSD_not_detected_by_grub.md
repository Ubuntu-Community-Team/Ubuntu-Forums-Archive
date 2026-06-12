---
title: "SSD not detected by grub"
date: 2016-11-08
forum: General Help
---

### Post by davidv1992 on 2016-11-08
I am currently in the process of upgrading my laptop (ASUS N751JK) with a samsung ssd 750 evo 500GB. It has an existing working harddrive with a windows and xubuntu installations. The drive is successfully detected both by the bios and the existing xubuntu installation and to the best extend i can tell it is working (can save files to it and they seem to be actually saved best i can tell).

Next up tried to install xubuntu 16.04 to the ssd. The installation seems to function, it installs the new grub correctly, and upon reboot the uefi bios transfers control to it. However, at this point, i'm guessing it cant find the ssd and drops directly into grub console prompt (it does not give any visible error messages). Using the grub console (using ls) i can confirm that it only lists the harddrive, not the ssd.

Has anyone seen similar issues, and have any suggestions on how to fix them?

---

### Post by oldfred on 2016-11-08
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Some Asus have needed pci=nomsi and mode nVidia need nomodeset boot parameter until nVidia driver installed.

      If UEFI boot, you have to press escape somewhere after UEFI/BIOS but before grub. Maybe more than once. If BIOS boot you hold shift key.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by davidv1992 on 2016-11-09
> **oldfred said:**
> May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Done, see [http://paste2.org/vHx6n6Xn](http://paste2.org/vHx6n6Xn)

An interesting note is that during boot, grub currently does not even see usb disks when booting from the hard disk, even though when booting from a usb with xubuntu install disk on it, it sees everything in the system.

> **oldfred said:**
> 
Some Asus have needed pci=nomsi and mode nVidia need nomodeset boot parameter until nVidia driver installed.

      If UEFI boot, you have to press escape somewhere after UEFI/BIOS but before grub. Maybe more than once. If BIOS boot you hold shift key.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

As mentioned above, I'm not even getting to the stage that the linux kernel is loaded. Will keep it in mind for when I get to that stage.

---

### Post by JayKay3OOO on 2016-11-09
Have you checked your bios settings? Is uefi enabled (sounds like it is) and when you press F8 for boot menu is there a different entry to boot from?

---

### Post by oldfred on 2016-11-09
You have UEFI installs.
Grub only installs to drive seen as sda, so ESP - efi system partition on sda will have new entry in a small grub.cfg that is a configfile to boot into the full grub.cfg in which every install has grub installed last.

You cannot see your ESP. Older installs used defaults, but newer installs set 0077 permissions which lock it. My entries (different ESPs as UUIDs are different).
 # /boot/efi was on /dev/sda1 during installation
14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    [COLOR=#ff0000]defaults[/COLOR]        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    [COLOR=#ff0000]umask=0077[/COLOR]      0       1 
Running Boot-Repair will change that entry back to defaults, as it has to modify files in ESP. You may have to reboot as I found when manually editing it, just remounting with sudo mount -a did not reset it , but reboot did.

You do not need to reboot to experiment with grub settings like the nomodeset. You press escape just after UEFI. May have to press more than once. And if in UEFI  you still have fast boot on, you may not have time to press a key. Fast Boot in UEFI is different than fast start up in Windows. UEFI fast boot assumes no system hardware or configuration change, so UEFI does not have to review it and (re)write the settings for operating system to use. That does speed boot as usually systems are not changed. But when making lots of changes you need to have fast boot off.

Best to also remove old kernels.
      
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a 

 [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

---

### Post by davidv1992 on 2016-11-09
I know i have an efi install, and noticed already that grub prefers installing on what /dev/sda is (the hard drive in my case).

I'm not exactly sure what you want from the ESP and why i should fiddle with the fstab entries, but i have access from my existing installations (xubuntu 14.04) to the efi system partition and noted that grub has a config file there which chains into the config files on the partition of the installation. Any potential issue with kernel parameters are however moot because of the following point

The real issue is the following: GRUB gets located fine, however, it does not see the ssd using whatever method it uses to enumerate drives when installed on a harddisk partition. GRUB does either not see the config files it needs (when i instruct it to load them from the new install on the ssd), or it cannot find the partition it needs to boot the entries for the new install on the SSD when it reads those configuration files from the old 14.04 installation on the harddrive, that does have the entries for the kernel in its config.

TLDR; Grub does not see the SSD when booting from harddrive(not listed by ls at grub command prompt). My question is: why is that? How can I fix that?

---

### Post by oldfred on 2016-11-09
Is it not booting directly from UEFI to grub in ESP that chains to SSD.
Or from UEFI to grub in ESP to hard drive's grub that has entries to SSD?

Is the SSD in a USB caddy that is newer?
 Older ones have had issues with gpt, large drives, SSDs, USB3 and some other issues. Some just purchased new drive caddy & found it worked.
Some also have had issues with certain ports on system. Some worked and some did not. Have you tried different ports, both USB2 & USB3?

If you boot into old install (may have to edit grub in ESP) and then plug in USB. May work from booting with live installer, but then you have two USB ports used.
       If issues, plug in device and see if shown or error in syslog, contol+c to exit tail listing
lsusb
tail -f /var/log/syslog

---

### Post by davidv1992 on 2016-11-10
The ssd is an internal SATA installed ssd (/dev/sdb in the boot-info stuff), so no usb involved in it's connection. Furthermore, I currently have no extra free sata ports (its a laptop), so testing whether it helps to move it to another port will have to wait for this weekend when i have access to better tools (to swap it with the harddrive), although I doubt it will make much of a difference.

The efi partition on the ssd is currently unused, it is a remnant of me trying to instruct the installer to setup the bootloader on /dev/sdb (something I will try to do manual later today). There is no chaining going on in the sense you are currently suggesting, it is simply that, when grub comes up, it sees no other device than the hardrive it booted from.

---

### Post by davidv1992 on 2016-11-10
Have tested booting from an efi loader installed on the ssd, and that sees everything. 

I have an hypothesis why this is, and good reasons to believe it is true (see below): Grub is using UEFI firmware calls to read the harddrive, and the uefi firmware for some reason hides the rest of the disks in the system.

Turns out there is a reason for this, called fast boot in my firmware settings. It initializes only the hardware needed to read the harddisk when bootting from it, ignoring absolutely everything else in the system (including cd, usb or extra disks on sata interfaces). Disabling this removed all issues. Though i sort of understand the reasoning they had for this, given the setup of my laptop the speed gains (which i have tried and failed to measured, there within my measuring error of about .2 second) are so low I dont see the point of breaking the boot process this badly for it.

TLDR; fast boot does not initialize enough hardware, disabling it works.

---

### Post by oldfred on 2016-11-10
Glad you found that.

One of our first suggestions is normally to turn off both fast boot in UEFI and fast start up in Windows. Windows was/is slow booting and these were changes to make it seem like it booted faster.
Fast boot was also a Windows requirement and it does speed total boot time. Most systems do not have hardware or configuration changes, so it just skips the UEFI/BIOS scan of what hardware you have and the write to drive for system to use.
But when making changes, it has to be off. 
A cold boot can usually reset to new hardware as then it does the full check for new/changed system configuration.But laptops with internal battery can be difficult to cold boot from full power down.

---

