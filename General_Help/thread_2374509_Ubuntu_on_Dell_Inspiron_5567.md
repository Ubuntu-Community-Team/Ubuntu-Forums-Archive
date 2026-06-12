---
title: "Ubuntu on Dell Inspiron 5567"
date: 2017-10-16
forum: General Help
---

### Post by tomasoneto on 2017-10-16
Hi everyone!

I'm not being able to boot Ubuntu on my Dell Inspiron 5567. I keep getting the "Minimal BASH-like line editing is supported" screen. I've already tried with boot-repair and manually reinstalling grub.

Also with Secure boot enabled/disabled.

I've tried swapping the HDD to another notebook and it works well, so my guess is that it has to do with BIOS or a compatibility issue/setting. 

Can anyone give me a clue on where to continue trying?

Thank you very much!

---

### Post by dragonfly41 on 2017-10-17
It's not clear to me what you are trying to do.

Do you have a Dell 5567 which only contains default Windows 10 (UEFI) and you are trying to boot up an external Ubuntu on a HDD via USB without making any changes in your laptop? 

Or are you trying to setup a dual boot configuration? Plenty of references explaining that option.

Recently I setup a Dell 3268 and I had to jump through various steps.

First I had to create a Recovery USB before making any changes. I bought a SanDisk Ultra 32GB dedicated to this purpose.

After following Dell guides I now have the Dell Windows partition shrunk to create an internal new partition for Ubuntu 16.04.

In addition I have two external drives each containing different bootable Ubuntu systems (and indeed older Windows Vista OS) which I'm taking time to migrate files into the main Dell 3268 using rsync.

To get these various systems recognised and put into a single grub menu which I now see when booting up (Ubuntu first in menu. Windows further down) I booted up Live USB (tapping F12 to arrive at Boot Once) and then from LiveUSB first install boot-repair tool and then run boot-repair.  Make sure when running boot-repair that you copy the grub information to pastebin for reference.

So to summarise start by making a Windows Recovery USB then create a Ubuntu LiveUSB on flash memory (say 4 GB). Install grub-repair tool on your LiveUSB.

[Further Notes]

Here is just one thread from this forum with similar scenario.

[https://ubuntuforums.org/showthread.php?t=2340043](https://ubuntuforums.org/showthread.php?t=2340043)

Look for advice on UEFI posted by OldFred.

---

### Post by oldfred on 2017-10-17
With my Dell Inspiron-3647 which is a Mini desktop, I made a Windows backup, a Dell backup & then a full backup using Macrium Reflect.
That was over several days, multiple DVDs and 3 flash drives (had to go to store for more).
It took an hour to install and configure Ubuntu into a pre-formatted ext4 partition. Once partitioned, install is about 10 Minutes.

My Dell is now an older Haswell based system. Yours is much newer and has AMD video which I do not know about.

But you want to install in UEFI boot mode.
Dell seems to be unique in that it wants CSM/Legacy mode on, but you still can/must boot in UEFI mode.
Every other system has to have CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode,       in the OFF mode to boot in UEFI mode.

Lots more info on UEFI installs in link in my signature below.

---

### Post by tomasoneto on 2017-10-20
Hi. Thank you all for your replies.

I'm trying to install and run Ubuntu on a second hard drive (actually and ssd).

So as far as I understand, I can leave untouched the windows hdd while selecting from which device to boot from.

The problem is, that although I can get to install Ubuntu and run it successfully on another machine (swapping the ssd), nothing seems to get rid of the minimal bash like boot, boot-repair throws error (I'm going to post it later).

So my guess is that it has to do with some BIOS configuration or hardware problem. I'm now gonna try enabling legacy mode according to oldfred and come back.

Thank you very much again.

---

### Post by leunam12 on 2017-10-20
I had that problem with my computer and I solved it by disabling Fast Boot. Worth a try.

---

### Post by tomasoneto on 2017-10-20
Hi!

I enabled legacy mode (but still choosing to boot UEFI), and also set Fastboot to minimal (there's no option to fully disable it: [http://www.dell.com/support/manuals/ar/es/arbsdt1/latitude-13-7350-laptop/lat7350_om-v1/system-setup-(bios)-options?guid=guid-c888f8f1-a050-4418-99ea-033d1129152c&lang=en-us)](http://www.dell.com/support/manuals/ar/es/arbsdt1/latitude-13-7350-laptop/lat7350_om-v1/system-setup-(bios)-options?guid=guid-c888f8f1-a050-4418-99ea-033d1129152c&lang=en-us)).

I keep getting the same. I realized that when I turn the computer off and on again (instead of rebooting), then it shows the regular grub screen, asking where to boot from. But when I choose "ubuntu" it throws an error (roughly translated):

Error: failure reading sector 0x9311f800 from <<hd1>>
Press any key to continue...

Pressing any key does nothing. Both the sector and <<hd1>> changed on a different try.

Here's the paste bin from boot-repair: [http://paste.ubuntu.com/25778624/](http://paste.ubuntu.com/25778624/)


Thank you all again

---

### Post by oldfred on 2017-10-20
You also managed to install the BIOS version of grub to the gpt protective MBR for BIOS boot. Just do not boot in BIOS mode as you have an UEFI install.

You have run Boot-Repair many times and have multiple copies of Boot-Repair log in ESP on sda. Best to houseclean most of them.

In Disks (gnome-disks) and upper right corner icon is Smart Status. What does it say about sdb?

If Disks says drive is ok, I might just try a reinstall using Something Else. But start with a totally new download & write to flash drive installer. There just may be a minor hiccup somewhere.

---

### Post by tomasoneto on 2017-10-20
Hi, many thanks.

How should I clean the mbr?

I didn't understand this: 

write to flash drive installer

---

### Post by oldfred on 2017-10-20
With UEFI boot the protective MBR is just there to have one partition entry saying entire drive is gpt. That is so old partition tools do see drive partitioned, and do not automatically start to erase it. And then gpt has space for a BIOS install of grub, but we almost never erase that whether UEFI or BIOS. If later you really wanted the 35 year old BIOS boot, we would just reinstall grub in BIOS mode, overwriting the incorrect version.

It was just create a new flash drive installer with new ISO download. Just in case error is from some bit on installer not being correct. Or do not use same installer as then you may have same issue.

---

### Post by tomasoneto on 2017-10-20
Yes, I tried many times both with the beta and final release. Also Fedora and Debian. I'm gonna do a smart check, but I could boot using the same ssd in another computer (even the same installation).

That's why I think it has to do with some incompatibility but I find no options to tweak.

Maybe if I upload the folders containing boot could help?

---

### Post by oldfred on 2017-10-20
If you can boot in UEFI mode on another computer then install should be ok.
Or was it using that BIOS boot copy of grub, that I did not think would work?

Then it is either UEFI settings, Dell Drivers, or a required boot parameter.
But normally Dells just work, unless very new hardware versions. Then they may need Dell's Sputnik which has newer drivers that later get incorporated into Linux.

Info on Sputnik
 Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/) 

While various models of Dell, often UEFI is very similar. 
Only major differences are between Intel & AMD versions. Otherwise minor differences to support various options.


 Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)

---

