---
title: "Lost GRUB functionality, can't order drives in BIOS"
date: 2020-11-02
forum: General Help
---

### Post by von Stalhein on 2020-11-02
Hi!

I cloned a 1TB drive containing Ubuntu 20.10 on to an Crucial SSD using Clonezilla. 

I did a similar thing when I built this machine, moving WIN10 from an old Samsung 250GB HDD on to a 1TB nvme m2 SSD.

Prior to this last operation the system booted in to either OS from GRUB without any issues (nvme M2 ssd/1TB Seagate HDD).

Now I need to mash F11 to select which disk I want to boot - this is annoying.

I have run Boot Repair from a live USB and GRUB is OK. It just won't start  WIN10 from a manually selected boot into Ubuntu - just sits there.

The mobo is an MSI Tomahawk. I can see the ADATA SSD and the Crucial  (latest one) OK but just not in the same dialogue - i.e if one is in the  BBS dialogue it doesn't appear in the boot order menu & vice versa.  

The Crucial needs to be the first drive to start in GRUB. 

What am I missing? Some UEFI thingy I haven't sorted?

---

### Post by oldfred on 2020-11-02
Post link to the Summary Report from Boot-Repair.

UEFI & BIOS are not compatible. Once you start booting in one mode you cannot switch.
Or grub can only boot other installs in same boot mode.
If grub booting in UEFI mode, then BIOS/BBS mode installs will not be in grub.

Grub only boots Working Windows. Windows cannot have hibernation flag set and fast start up also sets hibernation flag.
And Windows updates turn fast start up back on, so directly boot Windows from UEFI and check if fast start up back on.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by von Stalhein on 2020-11-03
Thanks heaps oldfred, I'll go over those links.

Pastebin link here - [https://paste.ubuntu.com/p/WWVc2dkpPJ/](https://paste.ubuntu.com/p/WWVc2dkpPJ/)

---

### Post by tea for one on 2020-11-03
> **von Stalhein said:**
> What am I missing? Some UEFI thingy I haven't sorted?

You are not booting in UEFI mode so you haven't missed anything yet - but you **should** use UEFI mode.

Did you originally have Windows 7 and then upgrade to Windows 10?

You [COLOR="#0000FF"]could[/COLOR] boot into Windows and make sure it is fully shut down [COLOR="#0000FF"](not hibernating or suspended)[/COLOR] and then update grub via Ubuntu. This is a bit of a guess because I am not very familiar with a BIOS mode of Windows 10.

Alternatively, following the info in your boot-repair report:-

Windows not fully shut down [COLOR="#0000FF"](lines 37 -39 and 43 -45)[/COLOR]

PPA repositories problems [COLOR="#0000FF"](lines 58 -63)[/COLOR]

Both Windows and Ubuntu are installed in older BIOS mode [COLOR="#0000FF"](lines 230 -231)[/COLOR]

Windows 10 now requires EFI mode with GPT (i.e. partition table).

It would be difficult to predict how Windows 10 will behave with future upgrades if installed in the non-recommended way?

The current best practice is to boot both Windows and Ubuntu in EFI mode.

Therefore, in order to be trouble-free for the future, I would suggest some radical action:-

Back up all your data from Windows and Ubuntu
Install Windows in EFI mode with GPT
Disable, de-activate or remove the Windows drive
Install Ubuntu 20.04 LTS in EFI mode with GPT 
Verify integrity of both OS by booting via UEFI screens (or boot menu)
When you are satisfied that it is OK, restore your data.
Then, you can configure/update grub2 to boot both Windows 10 and Ubuntu. (I would boot via the UEFI boot screens simply to avoid dealing with grub2 and dual booting).

I realise that this is a time-consuming task but it will be easier to troubleshoot in the future.

This website provides some interesting points about UEFI.

[https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

---

### Post by oldfred on 2020-11-03
+1 for tea for one's suggestions.

If you really want to keep the now 40 year old configuration of BIOS/MBR, you have to boot Ubuntu live installer in BIOS mode.
Do not run auto fix in Boot-Repair as you want old Windows BIOS boot loader in MBR of NVMe drive and grub only in MBR of sda.
Boot-Repair in BIOS mode and multiple drives installs one grub to MBR of all drives.

Microsoft has required vendors to install in UEFI boot mode with gpt partitioning since Windows 8 released in 2012. The BIOS mode was really only for upgrades from Windows 7, or so large customers with 100's or 1000's of systems could maintain one configuration.

---

### Post by von Stalhein on 2020-11-04
Thanks guys!

Yes, I installed Win with my Ubuntu disk unplugged and then installed Ubuntu on to another hdd. I had been on XP in the dual boot forever and hardly ever used it but I had to update it to win10 so I could continue any flight simming.

Recently, I built a new machine (the old one had a 9 y.o mobo etc) and cloned the Win install on to the nvme m2 SSD from an old Samsung 250GB HDD. So far so good.

Enjoying the speed of the ssd, I then got a bit ahead of myself when I saw the Crucial ssd on sale and thought as the win cloning went so well I'd do the same with the Ubuntu install.

I'll set aside a day and go through tea for one's process I think.

Is it possible to do the partial windows install (the one not losing docs etc) in EFI with GPT or do you have to hose the drive entirely?

Thanks!

---

### Post by CelticWarrior on 2020-11-04
Changing to GPT will delete all partitions so you better have backups.

---

### Post by von Stalhein on 2020-11-04
I will make very sure!
Cheers.

---

### Post by tea for one on 2020-11-04
> **von Stalhein said:**
> Is it possible to do the partial windows install (the one not losing docs etc) in EFI with GPT or do you have to hose the drive entirely?

I’m not sure what you mean by partial Windows install? Sounds a bit unusual to me.

As far as setting up GPT on your disks, you have to prepare the disk before running the OS installation process.

I have used gparted from a [COLOR="#0000FF"]live[/COLOR] Ubuntu session:-

Open gparted > Device > Create Partition Table > Select New Partition Table Type > Select gpt

When you re-install your OS, make sure that you boot in UEFI mode.

Boot in UEFI mode = Install in UEFI mode.

As mentioned by CelticWarrior, [COLOR="#0000FF"]backups[/COLOR] are your lifejacket.

---

### Post by von Stalhein on 2021-09-07
Thread disinter.

I've been back here heaps over the last 3 or 4 days to re-read the info provided above - it was very helpful! 

I know you've all had your lives on hold wondering how I went so I thought I'd put you out of your misery.

Another great learning experience.

Everything worked fine until the latest Win11 update turned up last week - I'm on the dev channel because thrill seeker.

 I could no longer boot to Win with full functionality as the system said the hardware was "unsuitable". Initially the symptoms were that of a disk failure (black screen "no media found") but after a few experiments I managed to get back in to Win to find out that the lack of secure boot & TPM was the culprit - the latter easily fixed, the former not so much.

As I was warned above, I needed to change things to be "trouble free in the future", the only suitable remedy being reinstall of both OSs. I did read about a couple of other methods using [this]("https://docs.microsoft.com/en-us/windows/deployment/mbr-to-gpt") but it didn't fill me with confidence.
Coincidentally I had ordered another SSD to replace a dead laptop drive. I do have backups of everything on another ssd in the system but it in my mind it was less stressful to copy things directly across the original drive from an external dock. This was of course, wrong.

Before reloading Win I copied files to another spare disk drive via the dock. Then I changed the BIOS to secure boot as recommended above and installed Win. Various unpleasant mucking about got me back to where I was before, the most painful bits being the reinstall of a couple of flight sims which were around 100Gb + each in downloads. Obviously reinstalling Office and other stuff was a PITA as well but that was all sorted in a day.

I couldn't access the Ubuntu drive as the secure boot had been changed from legacy, so when the new SSD turned up yesterday I started researching the next step. 

Win is on an NVME M.2 ssd so I thought I'd just disable it in the BIOS and then remove the old Crucial, replace it with the newer one, reload Ubuntu under the UEFI regime, re-order the boot sequence and be back up and about in no time.

Nope. The system wouldn't "see" the bootable usb stick with Ubuntu on it unless the NVME was enabled in the BIOS so I just went ahead with the Ubuntu install with it being operational, carefully confirming which drive was which in Disks & Gparted prior to install.
 
After some fiddling about with the options to make sure the partitioning was correct, I installed Ubuntu the same way I'd done the last time, to an LVM volume. This ended up causing hours of research afterwards but at the time I didn't know what I didn't know. Last thing was to perform a ```
sudo update-grub
``` and check that the Win install was found. Success.

Back in to the MSI BIOS and the methods of re-ordering the drives were (to me, used to old BIOS's) counterintuitive but I eventually got the machine to boot straight to a GRUB menu. From there both OSs were able to be accessed. I had installed GRUB to the Ubuntu drive - although reading that it wouldn't overwrite the Win bootloader I also read that it was a viable option.

So, feeling pretty happy with myself (!) I plugged in the older Crucial to my external dock & after about 2 hours worked out that it couldn't be "seen" in the file manager because both the old drive in the dock & the new install in the machine were included in the "vgubuntu" group. 
It took me a while to work out what the correct UUID for each drive was as I got different data from Disks, Terminal & Gparted. I renamed the older drive (vgrename) and it instantly appeared in the file manager -  Huzzah!! 
Even better, all my emails have been restored and most programs - I will wait a week or so before repairing the laptop with the old drive in case there's something I've missed - regardless of that I've still got 6 recent backups on the other 1Tb drive.

I reckon the hardest part was renaming the drive in the "vgubntu" group as the stuff I read was initially confusing until I found some cli examples.

Thanks again for the info above, it was very useful. =d>

---

