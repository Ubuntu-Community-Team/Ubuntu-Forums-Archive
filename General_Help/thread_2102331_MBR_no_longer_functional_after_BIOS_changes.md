---
title: "MBR no longer functional after BIOS changes?"
date: 2013-01-07
forum: General Help
---

### Post by Synirex on 2013-01-07
Hello, today I decided to install Ubuntu on my Toshiba Satellite C855D-S5320 running Windows 8. In order to do that I disabled secure boot, however, I also disabled UEFI mode and enabled CSM (if I remember correctly). USB has the top priority when booting then after is the hard drive. When I tried to run Ubuntu after saving settings I got a black screen. 

I am no longer able to go into Windows 8 BIOS because Windows will not load. A trusted friend of mine claims my MBR is the issue. When I boot up it says: 

"...Realtek PCIe FE Family controller Series v1.24#...
PXE-E61: Media test failure, check cable

PXE-M0F: Exiting PXE ROM
No bootable device -- insert boot disk and press any key"

Is it possible to just stick in a bootable USB with windows 8 and use the repair? I'm on a ubuntu laptop and have no access to another Windows computer. If this is a solution, how can I put Windows 8 on a USB from ubuntu? Ubootnetin does not work.

---

### Post by dcstar on 2013-01-07
> **Synirex said:**
> Hello, today I decided to install Ubuntu on my Toshiba Satellite C855D-S5320 running Windows 8. In order to do that I disabled secure boot, however, I also disabled UEFI mode and enabled CSM (if I remember correctly). USB has the top priority when booting then after is the hard drive. When I tried to run Ubuntu after saving settings I got a black screen. 

I am no longer able to go into Windows 8 BIOS because Windows will not load.


The whole point of **secure boot** is that it is **secure**.

**You have turned off secure boot so Windows 8 will never, ever, boot.** It is only designed to run on a secure boot system.

If you want to install Ubuntu in a secure boot environment then follow the instructions.

---

### Post by Synirex on 2013-01-07
> **dcstar said:**
> The whole point of **secure boot** is that it is **secure**.

**You have turned off secure boot so Windows 8 will never, ever, boot.** It is only designed to run on a secure boot system.

If you want to install Ubuntu in a secure boot environment then follow the instructions.
Why wouldn't it boot up when I was following this guide: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Where are the instructions to install a secure boot of Ubuntu?

---

### Post by oldfred on 2013-01-07
You have to install all systems as either UEFI boot or BIOS (legacy,CSM, AHCI & various other names)  boot. And if Windows is pre-installed you cannot convert to BIOS boot unless you buy another legal copy and install that. 

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
Ubuntu is using the Windows key and should even boot with secure boot on. You have to have it off to install. Some have reported that you can install and it works, but others have issues and a few have major issues. Some are UEFI issues and a few are grub related.

Boot-Repair fixes some of the grub issues including installs in BIOS mode and incorrect chain load entries.
       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

    
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

    
Some are just UEFI designs that are not correct:
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by LinGNUbie on 2013-01-09
I too have tried to dual-boot (Win8+12.04) this particular model in UEFI. Unfortunately the process never takes due to the video never being relayed correctly to the ubuntu system after initial boot of the EFI partition.

---

