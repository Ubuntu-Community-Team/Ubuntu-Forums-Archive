---
title: "Dual boot Ubuntu 18.04 Windows 10"
date: 2018-05-05
forum: General Help
---

### Post by Trelo on 2018-05-05
So I had a computer with Windows 10 and I added a second SSD. Using a USB drive I installed Ubuntu 18.04 into it.

Now, I'd like Windows boot manager to let me choose between W10 and Ubuntu during startup but I had no success.  The only way I can currently boot into Ubuntu is by pressing F11 on startup so I can select the new SSD drive, that takes me to GRUB, I select *Ubuntu and that's it... but it's a bit clumsy.

In Windows 10, I've tried adding the Ubuntu entry into Windows Boot Manager via the command line and bcdedit, but I have little idea of what I'm doing.  W10 is drive C: and Ubuntu is drive E:   This is how bcdedit looks like:

Windows Boot Manager
----------------------------------
identifier           {bootmgr}
device                  partition=\Device\HarddiskVolume3
path                    \EFI\MICROSOFT\BOOT\BOOTMGFW.EFI
description             Windows Boot Manager
locale                  es-ES
inherit                 {globalsettings}
default                 {current}
resumeobject            {4908f788-50a4-11e8-9d0b-806e6f6e6963}
displayorder            {current}
                        {ec0f7111-a97e-4ba4-89f6-1ef647b6e7a6}
toolsdisplayorder       {memdiag}
timeout                 5

Windows Boot Manager
-----------------------------
identifier           {current}
device                  partition=C:
path                    \WINDOWS\system32\winload.efi
description             Windows 10
locale                  es-ES
inherit                 {bootloadersettings}
recoverysequence        {7810b357-2966-11e8-89b6-e1f1b7cc2e79}
displaymessageoverride  Recovery
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \WINDOWS
resumeobject            {4908f788-50a4-11e8-9d0b-806e6f6e6963}
nx                      OptIn
bootmenupolicy          Standard

Real-mode Boot Sector
------------------------------
identifier           {ec0f7111-a97e-4ba4-89f6-1ef647b6e7a6}
device                  partition=E:
path                    \EFI\ubuntu\shimx64.efi
description             Ubuntu Linux

When I click on Ubuntu Linux in Windows Boot Manager the computer just reboots. 

Any ideas?

Any help is very much appreciated.

Regards,

---

### Post by oldfred on 2018-05-05
Ubuntu cannot be drive E:.
Did you install Ubuntu in UEFI boot mode?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

If only booting Ubuntu occassionly, and normal booting Windows, you should be able to directly boot Ubuntu from UEFI boot menu whether installed in UEFI or BIOS boot mode. But better if UEFI.

---

### Post by Trelo on 2018-05-06
Hi, thanks for your reply.

This is the link I got using Boot-info from a live-USB.

[http://paste.ubuntu.com/p/fhvfcWRPPd/](http://paste.ubuntu.com/p/fhvfcWRPPd/)

---

### Post by rohitsuman86 on 2018-05-06
1) Well, boot into UBUNTU using F11, it will show windows boot manager in GRUB. Just use that to boot into windows. simple.

GRUB should add windows boot manager in its menu automatically. No editing, no hassles.

2) Go to BIOS and set first boot device to be UBUNTU.

This way whenever your computer will start, it'll automatically start GRUB menu and then you can chose what to run - Windows or Linux.

---

### Post by Trelo on 2018-05-06
That&#8217;s a smart workaround.

What would be the simplest way to edit the GRUB order/default OS?

---

### Post by rohitsuman86 on 2018-05-06
Install GRUB customizer App. Using it you can edit GRUB menu graphically. It has GUI so no manual editing of files required. Anyone can use this,

Installation procedure :

[http://tipsonubuntu.com/2018/03/11/install-grub-customizer-ubuntu-18-04-lts/](http://tipsonubuntu.com/2018/03/11/install-grub-customizer-ubuntu-18-04-lts/)

---

### Post by Trelo on 2018-05-06
Thanks! :)

---

### Post by Trelo on 2018-05-06
Oh no.  I had no problem editing GRUB, all fantastic.  But:  Ubuntu was on a Kingston SSD and Windows on a Vertex SSD.

Now in the BIOS I can't select the Kingston SSD where Ubuntu is as my boot device, it just doesn't come up as an option.  The Kingston SSD is detected though in the BIOS and listed if I go to Storage devices.  

I also noticed that when I press F11 on startup and I can choose the boot devices, the Ubuntu option I was selecting to take me to GRUB was actually on the other Windows SSD, as in Ubuntu (Vertex).  I'm so confused...

---

### Post by yancek on 2018-05-06
You should not show Ubuntu as on drive E as windows does not assign drive letters to Linux partitions.  You did not post the command you used with bcdedit to create the Ubuntu entry so this is a lot of guess work.  Do you know/remember what command you used.  You are using UEFI and although your Ubuntu was installed on the Kingston, the EFI partition is on the Vertex so you need that attached for it to access the Ubuntu efi files to boot Ubuntu.  Was the command you used in bcdedit similar to that shown in the link below?

[https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/)

Your Ubuntu is on /dev/sdc which is a 55.9GB drive which I guess is your Kingston drive.  This is a Legacy install which you can see in the grub.cfg file which shows partitions as msdos rather than gpt but you have no BIOS boot partition.  Windows on its drive is EFI/GPT and you will have major problems booting with that mix.  If you can set the Ubuntu kingston drive to first boot priority, you might be able to boot Ubuntu and windows.  I would suggest you either convert Ubuntu to GPT or simply reinstall Ubuntu after reading over the Ubuntu documentation at their page below on dual booting windows 10/Ubuntu UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-05-06
Your configuration is very confused. 
Do both systems actually boot from UEFI boot menu?

You have UEFI hardware.
You have Windows booting in UEFI mode from sdb and Ubuntu booting in UEFI boot mode from sdc which is MBR(msdos) partitioned, not gpt which UEFI recommends. And you originally installed in BIOS boot mode since drive is MBR & grub in MBR of drive.
Both sda & sdc are MBR and sdb is gpt partitioned.
Windows requires gpt for UEFI, Ubuntu does not require it, but gpt is the UEFI standard.

Once you start using UEFI/gpt it is better to have all drives as gpt. And gpt has some advantages, so I started my conversion to gpt with BIOS boot back in 2010. Back then my XP was still on a MBR drive. Every one of my new or reformatted drives and even larger flash drives now use gpt. But I did not get an UEFI system until 2014.

With UEFI install, grub installs to first ESP - efi system partition it finds. So that is why both Windows & Ubuntu have folders in the ESP on sdb for UEFI boot.

For newer users, the easiest way to install to a second drive is to turn off in UEFI or disconnect all the other drives and install just to the one drive. Some sudo grub-updates, then may be required.  If not disconnecting, you have to manually gpt partition in advance to include the ESP (FAT32 with boot flag). 

How you boot install media from UEFI boot menu, UEFI or BIOS, is then how it installs. You must have booted Ubuntu installer in BIOS mode originally, and then converted install to UEFI mode.

What brand/model system or motherboard?

I might suggest you back up /home (which you already should be doing) and reinstall Ubuntu in UEFI boot mode. I do normally let grub install to sda with every install, but make sure I have an ESP on every drive that could boot install on that drive. And I do have an install (even if small) on every drive, even if just a data drive.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
            [http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd) 
    
For lots of info and then many more links to more info on UEFI install, see link below in my signature.

---

