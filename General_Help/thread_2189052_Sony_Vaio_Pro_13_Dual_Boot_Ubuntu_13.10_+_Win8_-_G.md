---
title: "Sony Vaio Pro 13 Dual Boot Ubuntu 13.10 + Win8 - Grub2 hangs on initrd"
date: 2013-11-20
forum: General Help
---

### Post by DarwinsBuddy on 2013-11-20
Hi folks,

This is my first thread here and I've solved many problems with the threads stored here.
But this time, I have a problem, which I can't solve following suggestions in threads of ubuntuforums.

I bought a Sony Vaio Pro 13 (SVP1321C5E) last week with Win8 pre-installed.
It has an EFI partition on it and a pre-installed Win8 partition, as well as a recovery partition and a SonyCare partition (it's like the recovery of the recovery partition)

I wanted to install ubuntu 13.10 alongside my Win8 (I want to keep it because my laptop is too new for Win7 since there are no drivers available for particular built-in hardware)
With a ubuntu bootstick I tried to install Ubuntu 13.10 alongside Win8, but did not succeed, because this option was not available, maybe there is a little mixup between MBR and GPT and it can not find the installed Win8 partition.

So I installed it by clicking "Something else", using the previously freed space by shrinking the Win8 partition.

After the successful installation I rebooted and came right back to Win8. No Grub2, no EFI bootmenu whatsoever.

So I started with my pendrive in a Live Ubuntu, downloaded boot-repair and executed it with the recommended options.
Success! I got Grub2 running. Booting into Win8 is no problem from here.

Now there are many boot entries. I guess they are the ones for every recovery partition etc.

BUT if I want to start Ubuntu using one of the "3" entries (5 if you count recovery mode entries). I get stuck on "Loading initial ramdisk..."

I tried everything: Install Ubuntu with secure boot on/off, boot-repair with many different settings (ending up in most of the cases in a bricked env, had to recover the efi partition), chroot into my ssd-ubuntu installation and grub reinstall/update, etc.

I have no damn clue what I must do to get Ubuntu 13.10 running.
The LiveUbuntu13.10 works like a charm, but from my built-in SSD I have no success.

I would appreciate any help.

For boot-repairs output, please see [http://paste.ubuntu.com/6448878/](http://paste.ubuntu.com/6448878/)

Thanks in advance.

(Since I'm new, please tell me if I forgot some output, which you may need for further diagnostic)

best regards,

Christoph

---

### Post by oldfred on 2013-11-20
Can you boot to grub menu from ubuntu entry in UEFI? 
Boot-Repair has done a rename of the Windows boot entry in UEFI to really be grub as many UEFI have been modified to only boot Windows. If you can boot the ubuntu entry you can undo the rename. If you cannot boot the ubuntu you have to leave the rename, but then can only boot Windows thru grub menu.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
[http://askubuntu.com/questions/377252/restore-backup-of-winefi-or-uefi-not-sure-that-boot-repair-made/377288#377288](http://askubuntu.com/questions/377252/restore-backup-of-winefi-or-uefi-not-sure-that-boot-repair-made/377288#377288)

    
Does the recovery mode work? It already has the nomodeset video option that works for most video issues. But some Intel chips need other boot options. And some laptops actually boot but just  have screen brightness set all the way down, so you cannot see it working.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
What video chip do you have? LIve installer uses the lowest level video and install does not seem to default to that.
from live installer if you do not know what you have:
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

And if you have dual video, you need to know which chip it is defaulting to on booting. As then the boot parameter may be different.
Some other Haswell based systems. Since Intel similar settings may be required.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

      
 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

---

### Post by DarwinsBuddy on 2013-11-20
Yes, I can boot to grub menu.
I don't think that the problem is the renamed boot entries, because I can still boot into Windows.
Just Ubuntu 13.10 will not boot up.

Following error appeared while booting up in recovery mode (nomodeset, avoiding root=UUID=<myUUID> and instead using root=/dev/sda7):

```
[COLOR=#333333][FONT=Ubuntu Mono]libahci: module verification failed: signature and/or[/FONT][/COLOR]required key missing - tainting kernel
```[COLOR=#222222][FONT=Verdana]

For a particular reason the recovery mode hangs on "Loading initial ramdisk..." if I try to boot by uuid.
Moreover /dev/disk/by-uuid does not exist. I have only a directory called /dev/disk/by-id and this contains just 2 things my ssd (which is not named with an uuid) and something else.

Could have somthing to do with secure boot?

If I boot with above settings I'm able to access the recovery menu, but only after a while since there are many errors followed by above error.(see my dmesg output [http://pastebin.com/HBQKfLKD](http://pastebin.com/HBQKfLKD))

My video chip is an Intel HD 4400. (This should not be the problem, I guess.)

Maybe I can try to install ubunut 13.10 with secure boot off (but this should not be relevant, since it uses the signed shimx64.efi loader if necessary).

Your supposed boot options are not working either.



[/FONT][/COLOR]

---

### Post by oldfred on 2013-11-20
May still be something in UEFI/BIOS. I thought UEFI systems had in effect AHCI on. 
My old BIOS system I have to go into BIOS and  turn on AHCI for my SSD drive to work correctly with trim.

Since Intel, did you try any of the boot options above?

You have this which is a problem:
 [   93.738708] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x6 [COLOR=#ff0000]frozen[/COLOR]
More info here on frozen

 [https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)

---

### Post by DarwinsBuddy on 2013-11-21
Thank you for your quick reply.

I have accomplished to boot now, by altering the /etc/default/grub config file and updatin grub.
This issue had taken me 5 days straight to discover.
If somebody has similar problems to boot, here is what I did summarized.
I can't guarantee that this is a complete documentation of what I did, since I may forgot something during my journey to the successful boot.


[LIST=1]
[*]secure boot turned off 
[*]install ubuntu 
[*]boot with livecd 
[*]download boot-repair (ppa) [https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair) 
[*]do recommended repair with boot-repair 
[*]restart into LiveCD 
[*]mount ubuntu partition 
[*]change /etc/default/grub:
[LIST=1]
[*]uncomment GRUB_DISABLE_LINUX_UUID=true (necessary to avoid uuid error as described in first post) 
[*]change following line to: GRUB_CMDLINE_LINUX_DEFAULT="libata.force=noncq splash" (required to boot properly with out hanging on "Loading initital ramdisk...") 
[/LIST]
  
[*]Try to restart in recovery mode (should succeed, if not try to alter boot options in grub menu as described in the previous step) 
[*]run update-grub 
[*]if wifi card does not work try: modprobe iwlwifi (which worked for me since I have an Intel 7260 wifi card and this module was not loaded) 
[*]apt-get update 
[*]apt-get upgrade 
[*]apt-get install linux-firmware-nonfree 
[*]restart 
[*]now it should boot as expected 
[/LIST]

I hope this helps if somebody has the same issue.


[B]UPDATE July 2014:
[/B]After updating Win8, my grub was purged. Just running boot-repair was not enough.
I booted into Win8 and executed following in the admin-shell:**bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi**

---

### Post by oldfred on 2013-11-21
Thanks for the update. It should help others if they search forum.

---

