---
title: "Repairing grub partition??"
date: 2016-05-25
forum: General Help
---

### Post by z61p2 on 2016-05-25
A few months ago, I added a new hard drive to my system, installed Ubuntu on it, and set it up for multi-booting. My system had two other HDDs with Windows on them, and I followed the instructions for installing Ubuntu on the new (3rd) HDD, and for using GRUB to control which OS booted. This setup worked beautifully until yesterday, and the wheels came off completely!! Here's what happened: 

1. While it was working (since Oct 2015), GRUB would prompt me for which OS to boot: Windows or Ubuntu
2. Yesterday, after returning from extended travel, I booted into Windows (from GRUB), and first order of business was to get caught up on my updates. 
3. Applied several Windows updates... then after restarting, the system began misbehaving: No GRUB menu appeared, and Windows automatically booted.  
4. I booted from the Ubuntu install CD, and ran 'boot-repair' iaw some instructions I found on the Internet, but this did not repair the issue:[INDENT]a. 'boot-repair' reported that it could not fix the problem, and had me create a pastebin (??) URL:
b. paste.ubuntu.com/16674898 
[/INDENT]

Further research yielded nothing useful - at least not pertinent to my situation as far as I could tell. 

Any advice as to how to recover would be appreciated. I cannot imagine how or why the GRUB partition became corrupted, but it seemed to happen as a result of applying updates to the Windows install (on another HDD in my system).

Best Regards,
JM

---

### Post by yancek on 2016-05-25
The most likely scenario is that your update of windows has  overwritten or somehow damaged boot files.  Your boot repair link is non-functional.

>  I booted from the Ubuntu install CD, and ran 'boot-repair' iaw some  instructions I found on the Internet, but this did not repair the issue:

Generally it is best to avoid this practice, limit the sources to something official or at least semi-official.  Best to have posted the boot repair info rather than trying to repair.  Fix the link and someone should be able to help.

---

### Post by oldfred on 2016-05-25
Is this yours?
[http://paste.ubuntu.com/16674898/](http://paste.ubuntu.com/16674898/)
I use a working pastebin and copy last numbers to convert.

Do not run any autofix in Boot-Repair, only advanced mode.
Boot-Repair's auto fix installs grub to every drive's MBR, but with multiple drives and installs on separate drives(recommended) better to have each boot loader in the MBR of the same drive as install.
So leave Windows boot loader in MBR of sda.

You probably had a working grub in sda, as that is always the default install, unless you install with Something Else and select another drive.

But with gpt partitioned drives you have to have another partition for grub to install correctly.
You need to have a bios_grub partition which Boot-Repair recommended.
A bios_grub is a 1 or 2MB unformatted partition anywhere on drive with the bios_grub flag. 
Use gparted to shrink any partition on sdc by 1MB and create new partition, no format. Right click and add bios_grub flag.
Use Boot-Repair's advanced mode, choose your Ubuntu install and choose sdc to install grub.
Set BIOS to boot drive that is sdc.
Once in Ubuntu run this to make sure Windows is in grub menu, if it is not (you show entry now):
sudo update-grub

With gpt partitioning you need either an ESP - efi system partition for UEFI boot or the bios_grub for BIOS/CSM/Legacy boot.
I converted to gpt on all new or totally reformatted drives in 2010, and about 2012 started adding both the ESP & bios-grub at beginning of drive. Then I could move older BIOS only drive to new UEFI system if I wanted without having to totally repartition & reformat. Very difficult to add an ESP near beginning of new large drives if full of data.

---

### Post by z61p2 on 2016-05-25
> **yancek said:**
>  [...]  Your boot repair link is non-functional.

Fix the link and someone should be able to help.

Yes, I copied the link to a piece of paper, and then entered it exactly as I'd copied it down. Apparently I missed the trailing slash, and omitted the leading specifier, but my browser finds the correct page in spite of these omissions. So, the URL for my boot repair link is: "http://http://paste.ubuntu.com/16674898/".

---

### Post by z61p2 on 2016-05-25
> **oldfred said:**
> Is this yours?
[http://paste.ubuntu.com/16674898/](http://paste.ubuntu.com/16674898/)
I use a working pastebin and copy last numbers to convert.


Yes - that's mine. Apologies for the confusion; I thought I was following the instructions properly. FWIW, the URL I posted does get my browser to the correct location. 

> 
Do not run any autofix in Boot-Repair, only advanced mode.
Boot-Repair's auto fix installs grub to every drive's MBR, but with multiple drives and installs on separate drives(recommended) better to have each boot loader in the MBR of the same drive as install.
So leave Windows boot loader in MBR of sda.

You probably had a working grub in sda, as that is always the default install, unless you install with Something Else and select another drive.


I'll do as you suggest. Before posting last night, I actually tried advanced mode to repair only sdc, but did not effect a repair. I'm not sure if I had grub in sda or not. I followed a recipe I found when I set this up, and as I had much time and effort invested in the Windows configuration, I took great precautions not to do anything that might have put it at risk. In fact, this was the primary motivation for using a separate HDD dedicated to the Ubuntu install. I seem to recall altering the boot order in BIOS to get this working properly. But yes!  I am quite happy to leave the Windows disks (sda and sdb) untouched. 

> 
But with gpt partitioned drives you have to have another partition for grub to install correctly.
You need to have a bios_grub partition which Boot-Repair recommended.
A bios_grub is a 1 or 2MB unformatted partition anywhere on drive with the bios_grub flag. 
Use gparted to shrink any partition on sdc by 1MB and create new partition, no format. Right click and add bios_grub flag.
Use Boot-Repair's advanced mode, choose your Ubuntu install and choose sdc to install grub.
Set BIOS to boot drive that is sdc.
Once in Ubuntu run this to make sure Windows is in grub menu, if it is not (you show entry now):
sudo update-grub


I hope you can bear with me on this... I need to take baby steps as I now have a fair amount invested in my Ubuntu disk also. Following your suggestions, then: 

1. From my pastebin output at "[http://paste.ubuntu.com/16674898/](http://paste.ubuntu.com/16674898/)", I have a partition at /dev/sdc1. Is this the existing partition I should shrink by 2 MB? Does the new partition need to be located in some specific sector location? 

2. I'll use gparted as you've outlined to create a bios_grub partition, and set the bios_grub flag in it. Then, using boot-repair in advanced mode, choose sdc for install of grub. Finally, I will check my BIOS config to make sure that sdc is still above sda and sdb in the boot priority. At this point, I think I should be able to boot into Ubuntu from sdc, yes?  

3. I am unclear on your instructions to verify Windows is in the grub menu... could you clarify that bit for me? 

> 
With gpt partitioning you need either an ESP - efi system partition for UEFI boot or the bios_grub for BIOS/CSM/Legacy boot.
I converted to gpt on all new or totally reformatted drives in 2010, and about 2012 started adding both the ESP & bios-grub at beginning of drive. Then I could move older BIOS only drive to new UEFI system if I wanted without having to totally repartition & reformat. Very difficult to add an ESP near beginning of new large drives if full of data. 

I very much like the idea of "future-proofing" my installations. However, I have to confess that this part seems to be quite a bit over my head. Is this a recommendation/practice that I could apply to my current setup, or did you mean that I should consider this for future installs? 

Thanks very much for your help with this. 

Best Rgds,
JM

---

### Post by oldfred on 2016-05-25
The bios_grub as I understand it can be found by grub anywhere on drive. So you can shrink any partition. I would assume all your ext4 partitions in sdc have space.

You already showed Windows in grub menu, but that was probably left over from when grub worked. Not sure then if other updates may miss it, but running the sudo update-grub after booting into Ubuntu will/should refresh menu.

Future planning for ESP and/or bios_grub partitions. 
As mentioned I knew eventually I would get to using UEFI and wanted then to have drives as gpt. 
But UEFI recommends ESP be at or near start of drive. Not sure then with very large multiple TB drives if UEFI can find an ESP far into drive. The bios_grub supposedly can be anywhere on drive. But years ago any grub install to a drive over about 600GB (location of actual grub files) had problems which they fixed. So I like to have ESP first & bios_grub second on drive. And I normally have smaller 25GB / (root) partitions and large data partitions at /mnt/data.

But with large drives very difficult to add partition(s) at beginning of drive. Not worth risk of moving partition to make space, but if totally reparitioning or a new drive best to plan ahead and include the ESP & bios_grub or at least leave some unallocated space at beginning of drive for future use. 
I like to have a small copy (10 to 25GB) of Ubuntu on every drive even if only a data drive. Then I can in an emergency boot that drive.

Windows in BIOS boot mode is the only one that requires MBR(msdos) partitioning. Windows in UEFI boot mode also only boots with gpt partitioning. And even Windows 7 can be UEFI but you have to slightly modify installer on flash drive to boot in UEFI mode to install in UEFI mode.

---

### Post by z61p2 on 2016-06-04
REF: [http://paste.ubuntu.com/16674898/](http://paste.ubuntu.com/16674898/)

I'm unclear on several things here - I'm missing something I should understand: 

1. The REF above states at the top of the report (Line # 8): "Grub2 (v2.00) is installed in the MBR of /dev/sdc". 

2. Further down (Line # 51), it shows sdc1, and indicates there are 2 boot files: /grub/grub.cfg, and /grub/i386-pc/core.img  

QUESTION 1: Despite the two statements above, I gather the "bios_grub" partition is not sdc1 - correct? 

QUESTION 2: If the "bios_grub" partition was somewhere on sdc before Windows misbehaved, where did it go? Did Windows delete the entire "bios_grub" partition on sdc, or is it more likely that "bios_grub" was on sda?  

QUESTION 3: Would the OS (Ubuntu or Windows) have kept any records that would allow one to determine where "bios_grub" was located before my system was mis-configured? 

3. Line # 139 shows that sdc1 Start Sector is at sector 2,048.  

QUESTION 4: When I create the "bios_grub" partition, can/should I create it in the space between sector 0 and 2,047? 

Many Thanks,
JM

---

### Post by oldfred on 2016-06-04
If you had grub installed to sda which is the normal default install, then you would not have a bios_grub.
The bios_grub is required for gpt partitions since gpt has no space after protective MBR like MBR(msdos) partitioning has.
But MBR partitioned drives do not have a need for bios_grub partition as core.img is installed to the sectors immediately after the MBR.

Do not put bios_grub before 2048. Shrink any existing partition on sdc by the 1 or 2MB and create a new unformatted partition with gparted and give it the bios_grub flag. Then use Boot-Repair to reinstall grub to sdc. Do not use auto fix.

It is only the suggestion of keeping boot loader on same drive as install that we need to install grub to sdc. 
And since sdc is gpt it has to have bios_grub partition.
If you reinstall grub to sda, it will boot, but then you can only boot Windows from grub menu not from BIOS. And when Windows needs repairs you almost always have to directly boot it, not from grub, to be able to use f8. Or you have to boot your Windows repair flash drive.
Grub only really boots working Windows.
So better to have two boot loaders, Windows on sda & Ubuntu/grub on sdc and BIOS default boot from sdc. But if required you can still directly boot Windows from sda.

---

### Post by z61p2 on 2016-06-04
> **oldfred said:**
> If you had grub installed to sda which is the normal default install, then you would not have a bios_grub.
The bios_grub is required for gpt partitions since gpt has no space after protective MBR like MBR(msdos) partitioning has.
But MBR partitioned drives do not have a need for bios_grub partition as core.img is installed to the sectors immediately after the MBR.

Do not put bios_grub before 2048. Shrink any existing partition on sdc by the 1 or 2MB and create a new unformatted partition with gparted and give it the bios_grub flag. Then use Boot-Repair to reinstall grub to sdc. Do not use auto fix.

It is only the suggestion of keeping boot loader on same drive as install that we need to install grub to sdc. 
And since sdc is gpt it has to have bios_grub partition.
If you reinstall grub to sda, it will boot, but then you can only boot Windows from grub menu not from BIOS. And when Windows needs repairs you almost always have to directly boot it, not from grub, to be able to use f8. Or you have to boot your Windows repair flash drive.
Grub only really boots working Windows.
So better to have two boot loaders, Windows on sda & Ubuntu/grub on sdc and BIOS default boot from sdc. But if required you can still directly boot Windows from sda.

The more I think on it, I must have installed Ubuntu with grub on sda (wish I still had that recipe!). At any rate, your recommendations for adding bios_grub to sdc make sense to me, and I shall follow your recommendation moving forward this evening. 

If I'm following you correctly, what's amazing to me is that any Windows-Ubuntu dual-boot recipe would do it any other way! It would seem to me the only rational way to set up a dual boot system using separate HDDs is to allow booting from either Windows *or* Ubuntu. To cripple one of these options by not placing bios_grub on sdc just seems ill-considered, and asking for trouble!  Why do you suppose "they" do this?

---

### Post by z61p2 on 2016-06-04
> **oldfred said:**
> Do not put bios_grub before 2048. Shrink any existing partition on sdc by the 1 or 2MB and create a new unformatted partition with gparted and give it the bios_grub flag. Then use Boot-Repair to reinstall grub to sdc. Do not use auto fix.


I've created a new partition with gparted, and added the "bios_grub" flag to it.

I've installed boot-repair, and I'm using the "advanced" menu, but these options are not clear! 

Main Options Tab: Use defaults? 
Grub Location Tab: Use defaults everywhere except the "Place grub in all disks" option? I've selected the alternative to place grub into sdc only
Grub Options Tab: None selected (default)
Other Options Tab: All selected (default)  NOTE: One option is to "Repair Windows boot file"???

---

### Post by oldfred on 2016-06-04
Because you have Windows, one of the few Windows fixes that Boot-Repair can do is install a Windows type boot loader to a Windows drive.

Do not use default or install grub to MBR of all drives. You want Windows boot loader on sda, grub boot loader on sdc and then want to set BIOS to boot sdc.

---

### Post by z61p2 on 2016-06-04
After running boot-repair configured as above (all defaults except "Place grub in all disks"), and setting the Ubuntu disk above the Windows disk the system still refuses to boot from the Ubuntu disk. In fact, it will not boot into Windows either! Once I restore the original boot order (Windows HDD above Ubuntu HDD), Windows will boot... no idea what's going on here! 

My pastebin output is at 17015908  (paste.ubuntu.com/17015908/)

Any advice will be appreciated.

---

### Post by oldfred on 2016-06-04
[http://paste.ubuntu.com/17015908/](http://paste.ubuntu.com/17015908/)

I did not notice you had /boot partition. Generally not required with most desktops. May be required with server or server type installs or LVM, RAID or full drive encryption.

Did you tick /boot partition in Boot-Repair.

Both grub & Windows look like they should boot from BIOS or one time BIOS boot key like f10 or f12.

Because you have nVidia have you installed the nVidia drivers? Or are you using nomodeset to boot open source driver?
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by z61p2 on 2016-06-05
> **oldfred said:**
> [http://paste.ubuntu.com/17015908/](http://paste.ubuntu.com/17015908/)

I did not notice you had /boot partition. Generally not required with most desktops. May be required with server or server type installs or LVM, RAID or full drive encryption.

Did you tick /boot partition in Boot-Repair.

Both grub & Windows look like they should boot from BIOS or one time BIOS boot key like f10 or f12.

Because you have nVidia have you installed the nVidia drivers? Or are you using nomodeset to boot open source driver?
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

The *only* default setting I changed in boot-repair's Advanced menu was the option to install on all drives. 

Re nvidia: Hmmm... the video setup is the same as it was when my Ubuntu system was working. However: When the system was broken following the Windows upgrade, I did move the video card to another PCI slot. This was necessary (or so it seemed) to get anything to display on the monitor. 

I can't follow your suggestion for NOMODESET... the system simply will not boot from sdc. The BIOS just cycles endlessly. There is no black screen; the BIOS menus just cycle over and over and over and ...

---

### Post by oldfred on 2016-06-05
What brand/model system?
Does BIOS show sdc correctly in drive listing?

---

### Post by z61p2 on 2016-06-05
> **oldfred said:**
> What brand/model system?
Does BIOS show sdc correctly in drive listing?

The mobo is an Asus Z9 PE-D8 WS 

The BIOS is American Megatrends core ver 4.6.5.3, ver 5503 x64, Build date 5/6/2014, Compliant with UEFI 2.3; PI 1.2 
The BIOS shows 3 SATA drives that it identifies as P1, P2 & P3. These correspond to drives sda, sdb and sdc in the following order: 
P1: WDC WD1000DHTZ-04N21 (sda, I believe)
P2: WDC WD4003FZEX-00Z4S  (sdb, I believe)
P3: WDC WD1002FBYS-02A6B  (sdc, I believe)

The Boot Order is currently set to P1, P3, P2 (sda, sdc, sdb), and Windows boots without a GRUB selection screen. When I set the Boot Order to P3, P1, P2 (sdc, sda, sdb), the BIOS cycles endlessly; i.e. nothing boots.

Please let me know if any other info is needed, and thanks again for your help.

---

### Post by oldfred on 2016-06-05
If you hold down shift key when booting sdc, can you get to grub menu?

set root='hd2,gpt1'

Above is in grub.cfg and says Ubuntu is on hd2. That would only be correct if booting from sda.
But you are booting from sdc, and boot drive in BIOS/grub is always hd0.
If you can get to grub menu change entry to hd0 and boot.
Then run this to change/correct all entries.
sudo update-grub

---

### Post by z61p2 on 2016-06-05
> **oldfred said:**
> If you hold down shift key when booting sdc, can you get to grub menu?

set root='hd2,gpt1'

Above is in grub.cfg and says Ubuntu is on hd2. That would only be correct if booting from sda.
But you are booting from sdc, and boot drive in BIOS/grub is always hd0.
If you can get to grub menu change entry to hd0 and boot.
Then run this to change/correct all entries.
sudo update-grub

I'm sorry, but holding down the shift key has no effect at all; the BIOS just keeps on cycling through, ad infinitum. I've tried everything that seems to be available, but nothing seems to get me to the GRUB menu; in fact, not even Windows will boot when sdc is at the top of the priority for booting. 

It seems the only access I have to sdc would be through the Ubuntu live cd. Is there any way to make the changes you suggest from there?

---

### Post by oldfred on 2016-06-05
Do you have something in UEFI turned on that prevents it from booting from sdc.
Some systems have per drive settings. Drive should be AHCI, not IDE nor RAID. Nor any Intel settings.

If UEFI will not start boot, not sure editing from live installer will help, but it can be done.

              
 #Normally we do not directly edit grub.cfg. Edit from live-CD/DVD/USB.
mount /dev/sdc1 /mnt
gksudo gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

---

### Post by z61p2 on 2016-06-05
> **oldfred said:**
> Do you have something in UEFI turned on that prevents it from booting from sdc.
Some systems have per drive settings. Drive should be AHCI, not IDE nor RAID. Nor any Intel settings.

If UEFI will not start boot, not sure editing from live installer will help, but it can be done.

 #Normally we do not directly edit grub.cfg. Edit from live-CD/DVD/USB.
mount /dev/sdc1 /mnt
gksudo gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

BIOS on this machine requires all drives be set the same, and they are AHCI mode. 

I've not been able to find anything in BIOS to turn any UEFI options on or off. There is an item "Launch EFI Shell from filesystem device, but when I try it, I get a "not available" message. 

This is a major bummer. I'm sorry you've put all of this effort into it without a solution. I'm giving up on Ubuntu though... this kind of thing happened once before, and I've just got better things to do with my time than nurse some "not ready for prime time" software. Yes - I'm disgusted - I spent far too many hours configuring my OpenWRT build system and my coding projects to just start over. So, I'll chalk this one up to experience, and move on.

---

### Post by z61p2 on 2016-06-06
Seems I'm thwarted at every turn... I read that Ubuntu had a "repair existing installation" feature in its installer. Unfortunately, that's not an option when I actually run the installer from the live cd. It recognizes the drive with all its partitions, but it's only "offer" is to install a new system on that drive?! 

Just for grins, I got another HDD identical to the one storing my existing dysfunctional installation, and installed a fresh copy of Ubuntu on it. It boots right up with no issue at all. Consequently, I'm concluding that the issues with my existing install have nothing to do with hardware or the BIOS - it seems they must be grub-related issues that are causing this grief. Any thoughts on that theory??

---

### Post by oldfred on 2016-06-06
With new drive are you booting with grub from sda or sdc?

Is it also connected when you have the old sdc connected. 
If so post link to Summary report from Boot-Repair.

---

### Post by z61p2 on 2016-06-06
> **oldfred said:**
> With new drive are you booting with grub from sda or sdc?

Is it also connected when you have the old sdc connected. 
If so post link to Summary report from Boot-Repair.

I'm booting from the new drive - the one on which I performed a fresh install of Ubuntu. The old Ubuntu drive, and the 2 windows/NTFS drives, are all disconnected to avoid all possible ambiguity. 

The last boot-repair report is at 17056379; it's on the original Ubuntu install - the one I've been trying to resurrect.

---

### Post by oldfred on 2016-06-06
Have you then tried booting with just the old sdc install a only drive?

---

### Post by z61p2 on 2016-06-06
> **oldfred said:**
> Have you then tried booting with just the old sdc install a only drive?

Yes, I did. The BIOS cycles endlessly; it won't boot from that drive under any scenario I've tried.

---

### Post by oldfred on 2016-06-06
Not sure what issue is/was on that drive.

---

