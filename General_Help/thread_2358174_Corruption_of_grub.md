---
title: "Corruption of grub ?"
date: 2017-04-10
forum: General Help
---

### Post by Nosphky on 2017-04-10
For the past 3 years or so, I have dual booted my desktop to either Windows (7 originally and then 10 for the past year) or UbuntuStudio (by default), with no difficulty. If I wanted Ubuntu, I would just turn the power on and walk away. If I needed Windows, I would wait for the GigaByte splash screen to show and then press F12 for a start menu (looks like it is provided by the motherboard).

Then a couple of weeks' ago, I just got an error message "disk: 'lvmid/S9XbZC- ..... -NSLG8U' not found. Entering rescue mode ..."  Then a prompt 'grub rescue >' 

Nothing I tried was recognised as a command by this prompt, not even help, exit or quit.

Fortunately, I can still hit F12 on start up and get a menu but I would like to put things back to how they were originally.

I don't think I can blame Windows because I hadn't booted Windows for at least 2 weeks prior to this error. The night before the error, I had downloaded and installed a bunch of Ubuntu updates without paying too much attention because they have never caused me a problem before. Last night there was another bunch of Ubuntu updates one of which did concern grub but it has not fixed the problem. My machine is turned off every night and restarted each day.

Originally, I used UbuntuStudio 1404 LTS for 2 years or so and then did a clean install of 16.04.1 in June or July last year.

The error message starting 'lvmid/....' makes me think that this is connected with the logical volume manager which I used with 14.04 but I scrapped it when I did the clean install of 16.04.1 last year. I suppose grub probably installs something in sda1. Is it possible that some lvm debris was left behind in sda1 and this has now come back into play because something else has altered / corrupted with the grub entries that 16.04 was using ?

Any suggestions about a process for putting this right would be appreciated.

---

### Post by oldfred on 2017-04-10
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Nosphky on 2017-04-10
Hi Old Fred :  done - the Boot Info is here 

[http://paste2.org/c3GL34Fy](http://paste2.org/c3GL34Fy)

Thanks.

---

### Post by oldfred on 2017-04-10
You have a somewhat mixed install.
Your fstab shows the mount of the ESP - efi system partition, so configured for UEFI boot.
But have an old grub on sdb and you must have switched from UEFI boot to BIOS/CSM boot from sdb which has an old grub with lvmid/S.... as location it wants to boot from.

If you switch back to UEFI boot, you should be able to boot Ubuntu entry?

But you did not really install UEFI boot correctly. It should work, but UEFI really wants gpt partitioning. You have gpt on sda with the ESP, but still have the 35 year old MBR partitioning on sdb. But installed in UEFI mode which uses the ESP on sda. So old MBR on sdb using new ESP on sda to boot.

If you eventually reinstall, I would convert sdb to gpt with UEFI boot. Currently Ubuntu's grub only installs to the ESP on sda, but I suggest including an ESP on every gpt drive.

With an UEFI system, you need to always boot in UEFI mode, and not switch to BIOS/CSM/Legacy mode.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Nosphky on 2017-04-10
Thank you for your comments. I have been trying to make sense of the Boot-info. I don't understand how I came to have a 'somewhat mixed install'. Originally The machine had only sda with Windows 7. I added a new disk sdb (identical type to sda) to install Ubuntu 1404 LTS and let Ubuntu guide me thro so I supposed that the dual boot options and boot information would all be on sda somewhere, probably in sda1 which seems to be the case when I look at lines 20 to 30 in the Boot-info listing.

I don't ever remember being asked if I wanted UEFI or BIOS - I wouldn't have understood what that meant anyway. I'm not clear now but I see you have provided some links which I shall go through.

When I made the clean install of 16.04.1 last summer, I backed up /home and lots of other files that I was advised to do on this forum. I had thought that clean install included a reformat job on sdb but perhaps it excluded sdb1 with the old lvm info (although at this remove I cannot be certain). I was a little surprised afterwards to see the /boot in sdb1 but I didn't think it contained anything - in fact today it only contains 8.69/100M. When 16.04.1 had completed installing, I put back all my backed up stuff, installed missing applications and all went well. Boot time just went as it always had done during the previous 2+ years.

I don't recall having had to chose between GPT and the older MBR partitioning at 16.04.1 install time. Maybe it was there and I didn't understand the implications of the decision - but I don't remember it. fstab was written in August 2016 (the time of the 16.04.1 installation, I suppose) and shows /boot/efi was on /dev/sda1 

I think that my installation has fallen foul of some Ubuntu updates over the past two weeks. What could have caused my desktop to switch from UEFI boot to BIOS/CSM boot overnight a couple of weeks' ago ? More importantly, how do I switch back to UEFI boot as you suggest ?

I note that Boot-info dump suggests the following repair operation at line 1248 :

"The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sdb2, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s fix-windows-boot use-standard-efi-file"

Will this achieve what you suggested (ie switch to UEFI boot) or does that require some other action ?

---

### Post by oldfred on 2017-04-10
Boot-Repair fixes may not be required.

How you boot install media UEFI or BIOS is then how it installs. That is the only choice you have.
It is because once you start booting in one mode, you cannot switch, so only choice is within UEFI.

But you can choose to boot flash drive in one boot mode, but UEFI default boot mode may be different for your installed system.
There really are three boot modes, UEFI with Secure Boot, UEFI and BIOS/CSM/Legacy or whatever your system calls it.
Most systems have some combination of settings, not even all on same tab for changing boot type. 
Most if CSM is on, only boot in BIOS mode, but some like Dell, seems to need CSM on to still boot in UEFI mode(not sure why?)

       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
[http://www.rodsbooks.com/efi-bootloaders/csm-good-bad-ugly.html](http://www.rodsbooks.com/efi-bootloaders/csm-good-bad-ugly.html) 
    
If you update UEFI from vendor it also resets to vendor defaults and you have to redo all your changes. I keep a list.

Just by seeing which screen comes up with installer you can tell how you booted.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Nosphky on 2017-04-10
I'm struggling along here. Using the last link you provided  [[https://help.ubuntu.com/community/UEFI]](https://help.ubuntu.com/community/UEFI]), I checked from my running  Ubuntu booted from the HDD using this code  [ -d /sys/firmware/efi ]  && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

and I got the result "EFI boot on HDD"

The other similar test gives "Installed in UEFI mode"

I also have an /etc/fstab file which contains an UEFI partition (mount point: /boot/efi)

so it looks like my Ubuntu was installed in UEFI mode and is currently  running in that mode. The menu I get when holding down F12 on bootup,  looks very similar to the square blue illustration of a Hitachi menu shown in that article. In  practice I have to chose "Ubuntu P3: WDC WD10EZEX-00RKKA0" or "Windows  P3: WDC WD10EZEX-00RKKA0" depending on which OS I want.

Selecting Ubuntu brings up very rapidly another menu with white print on  a black screen with various ubuntu options; it defaults to the top  choice which I think is lowlatency. 

Prior to this problem, when I booted the machine, I only got the black  screen with the Ubuntu options [unless I specifically hit F12 because I  wanted to select Windows]. Now if I don't press F12 on bootup, it goes  into Windows.

I think I conclude that Ubuntu was installed to use UEFI, my system is  using UEFI so I do not need to go into setup to make any changes. But  something has changed my default so I am now obliged  to use F12 to be  able to boot Ubuntu. I still do not understand what specific thing(s) I  need to change to get back to a default boot on Ubuntu.

---

### Post by LostFarmer on 2017-04-10
2 possible problems, let 'oldfred' give his opinion

```
/dev/sda1: unknown GPT attributes

     8000000000000000
```  that attribute is 'do not automount' , have no idea if linux uses that attribute

```
/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

  
    /dev/sda1 ends after the last sector of /dev/sda

```

---

### Post by Nosphky on 2017-04-11
Hi LostFarmer, I see that attribute is shared with sda2 and sda4 has a similar attribute 8000000000000001

As for:  /dev/sda1 ends after the last sector of /dev/sda

this does not check with what gparted shows. gparted shows that each partition
is contiguous with its next higher number and there is an unallocated 244GiB at the end of the disk.

In any case, this is the disk that was first in the desktop and where Windows7 was originally installed.
I don't remember having changed anything at all to do with the partitioning - I suppose that was down 
to Windows.

I thank you both for your interventions. The various links OldFred supplied have made me better informed
on the mysteries of UEFI/MBR and GPT/mdos. Unfortunately, they all explain the differences, advantages 
and disadvantages of each but do not clearly explain, for me, how to select the one or the other.

By spending some time with gparted and the bios setup, I have come to the conclusion that GPT/MBR is 
something you select for the partition table at disk formatting time and UEFI / MBR is selected via
settings on the setup of the motherboard.

I have spent some time in the setup, this morning (first time ever in 3 years) and I found a setting
which decides whether Windows or Ubuntu is the default. It was set to Windows so I changed it to Ubuntu
and that seems to give me now a default boot into ubuntu. Time will tell.

I was reluctant to blame Windows for changing anything but now I wonder if W10 'did it'. Although it 
was about 2 weeks or more since I had been into Windows when I first found the desktop had defaulted to
a Windows boot and I do bootup and shut down every day.

I'm grateful for the learning experience. If all stays good in the next few days, I'll mark this thread solved.

---

### Post by oldfred on 2017-04-11
Major updates to Windows will generally turn on its Secure Boot, so grub menu entry will stop working. Then you have to boot Windows from UEFI (f12) and turn it off, if you want to use grub as boot manager. Or just use F12.
Windows will also make it first in UEFI boot order. It only assumes you have Windows.
Grub on major grub updates will reinstall & make it first in boot order also.

You can from Ubuntu reset boot order with efibootmgr. More details in links in my signature.
man efibootmgr

If you partition in advance with gparted select gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
You can also use gdisk.

You can convert from MBR to gpt and vice-versa. Be sure to have good backups.
 Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252) 

But you should not have to, but may want to convert.

The installer uses gpt on all drives over 2.2TiB and all UEFI installs if it is doing the partitioning. If you partition in advance, you can use MBR with UEFI if you have an ESP and use gpt with BIOS if you have a bios_grub partition. It just is generally preferred to use gpt with UEFI.

I converted to only using gpt with my BIOS systems on all new or reformatted drives back in 2010 or 2011. And When UEFI systems started to be standard, I added both the bios_grub so I could boot in current BIOS and an ESP, so later I could move a drive to a new UEFI system and not have to totally erase/repartition drive. The ESP is suggested by UEFI to be first, but Windows makes it second or even third in some installs, but near beginning of drive.

---

### Post by Nosphky on 2017-04-12
Thanks for all the links. I'm now much better informed. My desktop is holding up ok and next time I WILL suspect Windows. Marking thread solved.

---

