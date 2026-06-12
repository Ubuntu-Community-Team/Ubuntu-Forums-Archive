---
title: "New Windows 10 install Over Existing Windows 7 Partion"
date: 2020-03-27
forum: General Help
---

### Post by wewantutopia on 2020-03-27
This is a pretty noob question (been using Ubuntu since 8.04) but I haven't needed to adjust my current setup (16.04) in years.  I need to use some Windows software for work so I need to update my W7 partition.  

If I remember correctly, if I do a new install it will mess up my GRUB configuration.  What would I need to do to fix GRUB/get back into my Ubuntu install?

Thanks!

---

### Post by oldfred on 2020-03-27
If a BIOS system, be sure to backup partition table.
Windows has a bug where it rewrites partition table on major updates & "forgets" to include Linux logical partitions.
Partition is still there & just needs to be added back to partition table.
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
parted rescue or testdisk can also restore partition table, but best to know details like sectors:
So you know sectors:
sudo parted /dev/sda unit s print

Then be sure to have full backup. Any major change can cause issues.
You do not normally need to backup Ubuntu as easy to reinstall, but need all your data, settings from /home, list of installed apps to make it easy to reinstall. You may need some settings from /etc if you made system wide changes. I edit grub files, but copy into /home the changes so my backup of /home includes a copy of my /etc changes. If you have installed server type apps, then those folders in / will also need backup.

If newer UEFI system, now would then be a good time to convert to UEFI boot on gpt drive. But that will redo entire system and both Windows & Ubuntu would need to be reinstalled in UEFI boot mode. You can convert a drive from MBR to gpt, but Windows wants a lot of additional partitions with UEFI, so better to just totally reinstall.

---

### Post by ipv on 2020-03-27
> **wewantutopia said:**
> I need to use some Windows software for work so I need to update my W7 partition.

i would advice you to upgrade to 10. 

if you need 7 for some specific software to be used i would say you stay offline if possible.

just my 2 cents.

---

### Post by wewantutopia on 2020-03-27
Thanks for the replies.  My system is older; still has bios.  

I backed up my partition table and saved my drive data.

I haven't used my W7 partition in years.  New software for work requires Windows so I will be install W10 OVER the existing W7 installation so no more W7.

Thanks for the replies.  I will check back if I have any other hangups.

---

### Post by Impavidus on 2020-03-27
Ubuntu 16.04 is getting a bit old too, so you may take the opportunity to fresh install both Linux and Windows to a new release.

---

### Post by wewantutopia on 2020-03-27
I know that 16.04 is pretty old but it is still supported and it is setup just how I like it; I'm not ready to switch yet.

So... I tried to install W10 but now I am plagued with the "Windows cannot be installed to this disk. The selected disk has an MBR partition table. On EFI system, Windows can only be installed to GPT disks"  problem.

Is there anyway to "convert" my old MBR disk to a GPT while keeping my current Ubuntu install and dual boot setup??

---

### Post by oldfred on 2020-03-27
You said system was older and BIOS.
But you must have booted Windows installer in UEFI boot mode.
Windows only installs in BIOS boot mode to MBR.
Windows only installs in UEFI boot mode to gpt.
You can convert MBR to gpt, but at minimum have to reinstall grub and update fstab. Often easier to reinstall & restore from backups.

If you boot Windows installer in BIOS boot mode, it should then install in BIOS mode to your MBR drive.
Windows in UEFI mode wants lots of extra partitions, But can be installed to unallocated space on gpt drive with Ubuntu and usually (not always) Ubuntu is ok. But you still need good backups.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by yancek on 2020-03-27
I've installed windows 10 on an MBR drive with no problems so you should be  able to do it.  According to the link below at a windows forum (see the last post), you need to enable Legacy/CSM in the BIOS firmware and disable secure boot.  I'm not sure that secure boot needs to be disabled but Legacy/CSM boot must be enabled.  If you convert to GPT and install windows UEFI you will need to do the same with Ubuntu.

[https://www.tenforums.com/general-support/2448-windows-10-mbr.html](https://www.tenforums.com/general-support/2448-windows-10-mbr.html)

---

### Post by wewantutopia on 2020-03-27
So my bios has support for uefi which i turned off.  I then used the --workaround-bios-boot-flag for WoeUSB to make the bootable W10 usb.  That worked and I was able to install W10 alongside my existing 16.04.

Now... When it restarts there is no grub, no w10, it appears to be in a bootloop. 

I tried a Ubuntu live USB session with boot-repair doing the "recommended repair" but that didn't change anything. 

Any ideas? 

Thanks!

---

### Post by yancek on 2020-03-27
> Any ideas?  

If you don't understand what is happening, the best thing is to ask for advice and running the "recommended repair" was definitely not the best first step.  When you run boot repair, you should see an option to Create BootInfo Summary which you should select.  When it finishes, you should get a link which you can post here so that some of the experts here can take a look at what happened.  There are a number of possible problems and rather than have people guess, best to run boot repair and post the link here.

---

### Post by wewantutopia on 2020-03-27
I had this happen to me in the past so I was just trying to do what I remembered doing then. In retrospect it was a bad move running the tool first. 

So, here is the current boot info summary:

[http://paste.ubuntu.com/p/NRcHwRYHX6/]("http://paste.ubuntu.com/p/NRcHwRYHX6/plain/")

THANKS FOR THE HELP!!

---

### Post by oldfred on 2020-03-27
I cannot get your link to work, but I copy & paste and I can get it to work. May look same but leads me directly to report.
[http://paste.ubuntu.com/p/NRcHwRYHX6/](http://paste.ubuntu.com/p/NRcHwRYHX6/)

Move boot flag back to sda1 and run Windows repairs.
You are missing boot files.
The primary Windows NTFS partition with boot flag has to have these. Often with Windows 7 or later, they are in a separate NTFS Boot partition, but do not have to be.
/bootmgr /Boot/BCD

Once you fix Windows and with Windows 10 you have to turn off fast start up. Grub only boots working Windows which also means it cannot be hibernated. Fast start up sets hibernation flag.
Then you can install grub boot loader to MBR and dual boot. You have grub installed to partition boot sector of sda2. With grub2 that is not recommended and Windows will not boot Ubuntu. 

The disadvantage of Windows 8 or 10 on same drive as Ubuntu in BIOS/MBR mode is that Windows updates will turn fast start up back on. You may not even see those update, but then grub will not boot Windows.
You then need your Windows repair disk to temporarily restore a Windows boot loader to MBR, turn off fast start up or make other Windows repairs, then restore grub manually or with Boot-Repair.

Or you always need two flash drives, one for Windows repairs and one for Ubuntu/grub repairs.

With UEFI, you can always directly boot Windows from UEFI boot menu, so do not have to temporarily reinstall Windows boot loader. Still with UEFI good idea to have repair flash drives, but not as essential.

---

### Post by wewantutopia on 2020-03-28
Thanks oldfred! ! That worked nearly perfectly. Moved the bootflag and now I have my previous dual boot setup working with W10.

But... Now my 16.04 has 2 issues it didn't before.

The system hangs at shutdown. Tried adding acpi=force apm=power_off to grub after quiet splash but no luck. I have since removed them from my grub config

I have no internet. I can connect to wifi, connect to my router and other devices in my network but no internet. All other devices work fine and the W10 install so has internet.  I can ping the dns server fine but host [www.google.com](www.google.com) gives me connection timed out; no servers could be reached.

I've changed nothing else with the system other that the w10 installed and grub changes. 

What do you think?

---

### Post by wewantutopia on 2020-03-28
I'm going to post the internet question in the networking forum.

---

### Post by oldfred on 2020-03-28
See also the sticky note in the networking sub-forum.
You can run the suggested WiFi script to output lots of info on both WiFi & network, so those who know those issues can make better suggestions. 
My networking has always worked, so not up to date on those kinds of issues.

---

