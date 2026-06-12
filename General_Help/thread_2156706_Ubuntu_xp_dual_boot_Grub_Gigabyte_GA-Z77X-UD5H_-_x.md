---
title: "Ubuntu xp dual boot Grub Gigabyte GA-Z77X-UD5H - xp will not boot"
date: 2013-06-22
forum: General Help
---

### Post by cscj01 on 2013-06-22
I have had a dual boot configuration for years with XP and all versions of Ubuntu back to 7.04.  I now have 12.04.1 with the 35.0.x kernel.  XP has been at SP3 for years.  I have had no trouble until I decided to build a system.  Now I can only get Ubuntu to boot.  When I try to boot XP, the logo comes up, the blue progress bar starts for a second or two, then the machine recycles back through Bios and the boot menu.  My hardware configuration is as follows:

[LIST=1]
[*]Intel I5-3570K @ 3.4 GHz;
[*]Gigabyte GA-Z77X-UD5H motherboard;
[*]4 G.Skill 8 GB DDR3 memory sticks;
[*]TSSTcorp CDDVDW SH224BB;
[*]Western Digital WD5000AAKS-0;
[*]Western Digital WD1501FASS-0;
[*]Western Digital WD1002FAEX-0;
[*]
[/LIST]
All the HDD's and the CDDVDW were in my old machine and are SATA.  My Bios has settings for UEFI and Legacy.  The setting for my storage devices is Legacy and UEFI.  I have tried it with Legacy only, but the results are the same.  I am unsure as to what is happening because I get no messages to check.  I wouldn't care except for one application that uses some hardware not supported by Ubuntu (a fax modem I still have to use on occasion).  Anyone have any thoughts?  Thanks.

---

### Post by oldfred on 2013-06-22
XP does not recognize gpt partition drives which are required with UEFI boot. I only have BIOS but converted my Ubuntu drives to gpt and dual booted ok.
But then I got a new SSD and had to change BIOS to support trim with AHCI. My XP did not have AHCI drivers so it finally forced me to stop using XP. :)
I have gone back into BIOS turned off AHCI and booted XP, so it still works, but that is too much hassle for what little I was using it.
XP has less than a year to go, it may be time to move on. But in BIOS can you set IDE mode for hard drive? That may be required for XP. But that may cause issues with everything else. You new motherboard may not even have a IDE mode anymore. I was also using LBA or Large for large block allocation with my XP.

We used to have a separate fax machine but I finally got my wife to retire it as we had not used it for 2 years.

I would think there is fax modem software somewhere for Linux.Just looked in synaptic. There is efax and several cups drivers for printers that have fax capability.

---

### Post by cscj01 on 2013-06-25
Well, I set the Sata mode to IDE, but trying to boot XP hangs.  The hang is a black screen with a non-blinking cursor.

I thought the hang might have something to do with XP not having AHCI drivers, but it seems I have to be able to boot into XP to install the drivers.  I tried to boot the XP install CD and try to use repair to install the drivers, but it acts similar to my original problem: displays an orange screen for a second or two, then recycles back through BIOS and the boot menu.  I may have to give up XP because I may never get it to boot again.

---

### Post by oldfred on 2013-06-25
I thought XP not working was a good thing. :)

Often Windows needs a chkdsk as the first repair option, then sometimes just reinstalling the boot files or running the standard fixBoot, bootcfg and chkdsk. If you want to install XP's boot loader to the XP drive set BIOS to boot that drive and then run the fixMBR command.

 Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[URL="http://support.microsoft.com/kb/307654"]http://support.microsoft.com/kb/307654

[/URL] FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

[URL="http://support.microsoft.com/kb/307654"]
[/URL]

---

### Post by cscj01 on 2013-06-26
I'm not sure I have clearly stated my configuration.  I have one boot drive that contains XP, Ubuntu, and swap.  I use Grub as my boot loader.  I can boot that drive with Ubuntu but not with XP with Sata Mode set to AHCI.  If I set Sata Mode to IDE, I cannot boot XP.  So I cannot boot XP no matter the setting of Sata Mode.  When I try to boot the XP install disk, it will not boot.  However, I can boot Ubuntu Live disks, Gpartd, and Clonezilla disks.  My boot order is CDDVDRW first and HD second.  The HD with the OS's mentioned above is the only bootable HD.  So I don't know how to accomplish what you suggest in your last post.  In any case, I do not want to use the XP bootloader.

I do have a Virtualbox XP VM under Ubuntu, but I don't think that is going to allow me to do anything you mentioned.  I believe all the commands you mentioned have to be run under a native XP.  Am I missing something here?

Finally, XP not working would be great if I could buy an internal fax card that would work with Ubuntu.  However, that seems to be a dicey subject within itself.  Also, I do not like 3 in 1 devices because if part goes out, you have to buy a new device if you need that functionality.

I do appreciate your assistance.  I suppose my germane question should be "How can I get XP to boot by only using Ubuntu to repair anything?"  Does that question make sense?

---

### Post by oldfred on 2013-06-26
I think with XP you can do almost everything in the way of repairs but chkdsk from Linux. I think some of the third party Windows repair tools will do chkdsk. Check out Hiren's boot CD, Easus & partition Wizard. Not sure what free versions offer.
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

    
I was never able to boot XP with AHCI on, but have turned it back off and did boot XP. Have not tried for about a year now. :)
I have to have AHCI on for SSD to support trim.

You should be able to boot XP install/repair disk with AHCI off. There may be other settings, but I have not tried to boot XP installer for 7 years. It took me most of a day to install as the legal copy I had was older and I had to add all the service packs. With all the updates & reboots it just reaffirmed my distaste for Windows. The only reason I kept it was one application and eventually I just gave up. The nearest Linux equivalent became good enough.

---

### Post by Rebelli0us on 2013-06-26
I used a GA-Z77X-UD5H for a while, XP needs an AHCI driver to boot. You can use nLite to slipstream the driver.

---

### Post by cscj01 on 2013-06-26
I finally got XP booting in IDE mode.  Seems the file system (NTFS) had some issues.  I used ntfsfix which got me to XP running chkdsk at startup.  The only problem is that XP no longer recognizes my data HD which is an NTFS single partition disk.  Device manager knows it's there, but Windows Explorer doesn't.

After booting, I installed the AHCI drivers.  So far, I'm not having any luck with booting XP that way.  Will try again tomorrow.

---

### Post by cscj01 on 2013-07-01
After a number of attempts to get XP to boot in AHCI mode, I have decided to quit.  I think I will search for a supported modem card within Ubuntu.  Since XP does not recognize (at least as far as using it) my data disk, it is practically useless in IDE mode.  I see no reason to spend money on Windows 7 just for a fax solution.  At that, I don't even know if Windows 7 supports the Winmodem card I have.  So I suppose it's sayonara to XP.  Now I just hope Ubuntu doesn't go in some stupid direction such as touch screen interface for desktops.  Personally, I still prefer and use Gnome Fallback on 12.04.

Thanks for all the help.  I'll mark this thread as solved, although surrendered would be a better designation.

---

### Post by oldfred on 2013-07-01
Surrender does sound more correct.

But I might experiment with whatever fax software/drivers Linux has. Often some of the older systems are better supported in Linux if not too unusual of a device.

---

