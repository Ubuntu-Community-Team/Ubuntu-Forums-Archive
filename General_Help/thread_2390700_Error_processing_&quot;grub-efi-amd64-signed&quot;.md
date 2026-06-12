---
title: "Error processing &quot;grub-efi-amd64-signed&quot; in a working 18.04"
date: 2018-05-01
forum: General Help
---

### Post by raysa on 2018-05-01
I installed Xubuntu 18.04 on a new laptop (with help from this forum!), and it works well except for a recurring problem.  (The laptop is an Acer Spin 1 and the Xubuntu is the only OS on it - I over-wrote the Windows).
The problem is when I try to install new software apps. At first I get an "unable to install" message with an instruction to type in a terminal "dpkg --configure -a" . When I do that I get the following:
```

Setting up grub-efi-amd64-signed (1.93+2.02-2ubuntu8) ...
Installing for x86_64-efi platform.
grub-install: error: efibootmgr failed to register the boot entry: Unknown error -1.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Errors were encountered while processing: grub-efi-amd64-signed

```
If I clear the error messages away and try to proceed with the app installation it appears to start downloading and then stop and just hang incomplete.  
But then if I close everything and re-boot, lo and behold, the app is installed and working fine ... actually this applies only to some app downloads - three successful and two failures so far.
Best way to fix this problem?
Thanks.

---

### Post by oldfred on 2018-05-01
All Acer requires you to set UEFI password & enable trust on .efi boot files.
But if the grub/Ubuntu folder was not created in the ESP - efi system partition, that is a separate issue.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
 [https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
     Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238)

---

### Post by raysa on 2018-05-02
I've tried the various things in the links provided and nothing seems to change this. I keep being asked to "dpkg --configure -a" during various operations like trying install new software or running some (but not all) installed packages. I duly type the line and the terminal often says things are happening but with some error messages - the one in the code box above is a common one. Having done that I can usually (but not always) proceed successfully, but the problem keeps recurring and I'd really like to fix whatever is wrong with the 'grub-efi-amd64-signed' thingie.

---

### Post by raysa on 2018-05-02
After a few more occasions of getting errors, I notice that although the terminal contents vary, the consistent part each time is:

Setting up grub-efi-amd64-signed (1.93+2.02-2ubuntu8) ...
Installing for x86_64-efi platform.

Then nothing happens and however long I leave it I don't get the $prompt back in the terminal.

---

### Post by oldfred on 2018-05-02
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by raysa on 2018-05-02
Thanks oldfred. I tried to do this from the faulty working install, but after quite a lot of terminal processing it came up with the same old error message and hang. So I closed down and fired up the live installer to do it. Here's the report link: [http://paste.ubuntu.com/p/RNM9htYkzS/]("http://paste.ubuntu.com/p/RNM9htYkzS/")

As this is a new laptop with very little data on it yet, it wouldn't be too bad to start all over again with a new installation, but unless there's something I should do differently this time I fear I'd up with the same problem.

---

### Post by oldfred on 2018-05-02
What brand/model system?
It must be one of the very lightweight systems as it is using MMC card as disk.
And script does not yet fully parse MMC nor NVMe drives, but Boot-Repair will reinstall grub.
Are you using the original ESP - efi system partition? Or did you let installer create new one?

Does Boot-Repair correctly install grub? Use advanced mode and full uninstall/reinstall options.

---

### Post by raysa on 2018-05-02
It's an Acer Spin 1.  Yes, very lightweight - only 32GB but that's fine for my intended use of it.
I'm afraid I'm out of my depth with this, and I don't know about such things as ESP-efi, but when the installation initially didn't boot at all, I used boot-repair and it certainly did some good because the installed system does start now and basic applications work fine, but as soon as I do anything that needs system actions - like installing new software - the stuff happens as described in my first post above.

---

### Post by oldfred on 2018-05-02
All Acer require you to enable a UEFI password and set "trust" on the grub/ubuntu .efi boot files from within the UEFI.

 Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238) 

Some explain details better than others. Many also have had to update UEFI from Acer. Older threads mention downgrading UEFI to get it to work.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392

      [/URL]Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
    [URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

### Post by raysa on 2018-05-02
Thanks ... yes, I came across the EUFI password and "trust" advice before, and I did both. But the "error processing grub-efi-amd64-signed" hitch still persists.
Infuriating to have a computer that works a bit, for simple stuff that I could do on my phone, but just hangs as above when I want it to install something useful.
I'd gladly re-install if I could do it without just re-introducing this problem.

---

### Post by oldfred on 2018-05-02
Did you try reinstalling grub in UEFI mode with Boot-Repair?
Sometimes it works where installer does not.

If still errors try this then try reinstall of grub again.
       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted, example is sdb1, yours is probably /dev/mmcblk0p1 

sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by raysa on 2018-05-06
Thanks. I tried this and it looked promising at first - the dosfsck appeared to do its thing and clear a dirty bit. But then when I re-ran boot-repair set to reinstall grub it did a lot of unpacking and processing but got stuck on "setting up boot-sav-extra" and just hung there. A boot-repair run just before this produced the following report:
[http://paste.ubuntu.com/p/h3tmDKZyXQ/](http://paste.ubuntu.com/p/h3tmDKZyXQ/)

---

### Post by oldfred on 2018-05-06
The boot-sav-extra is just the report & the logs.
Did the grub install finish with error 0, or no errors?

---

### Post by raysa on 2018-05-07
The grub-install didn't finish, so I got no final info.  This seems to be the problem with anything I try ... the process starts promisingly but then hangs incompleted. I leave it for a few hours just in case, then try rebooting, get the "No bootable system" message and can only resort again to the usb installation stick as live user.

---

### Post by oldfred on 2018-05-07
No Bootable system can be just that you have UEFI set to boot in Secure Boot mode and grub is installed in UEFI boot mode. Or UEFI is set for BIOS boot mode and grub is UEFI.
Double check UEFI settings.

My system does not have UEFI or UEFI Secure Boot setting. It has Windows & "Other".  And fine print says if using Windows 7 use "Other". Windows 7 does not support UEFI Secure Boot so that really is the setting for Secure boot on or off.

---

### Post by raysa on 2018-05-07
Thanks, but I'm not sure what you mean by "double-check UEFI settings".  Where do I do that and what am I looking for? When I go into the F2 BIOS area I don't see any option to choose UEFI or BIOS boot modes. Note there is no Windows on this machine - I chose to install Xubuntu as the only OS, wiping Windows off.

---

### Post by oldfred on 2018-05-07
Do you have a Windows or "Other" setting.
May be under CSM/BIOS/Legacy or whatever your UEFI calls it.

---

### Post by raysa on 2018-05-08
I don't see a Windows or Other setting. There is an option for enabling or disabling smart boot. If enabled I get the "No bootable device" screen if the live installation stick is not inserted. If smart boot is disabled I just get a command line 'grub>'.  Also if smart boot is disabled the live installation usb stick doesn't boot (even though it is top of the boot list) - the 'grub>' command line comes up whether the usb stick is inserted or not.

---

### Post by oldfred on 2018-05-08
What brand/model system?
This smart boot may be too smart for its own good.

Generally grub> means it tried to boot, but grub is miss configured. 
Often you have BIOS grub in MBR, but system is configured for UEFI or vice-versa.
Or older grub did not get updated with new install and UUIDs do not match. Then Boot-Repair full reinstall of grub from advanced options ususally fixes it.

Boot-Repairs full reinstall of grub is essentially the same as Chanath's suggestion above on a full chroot from live installer into your install to reinstall grub.

---

