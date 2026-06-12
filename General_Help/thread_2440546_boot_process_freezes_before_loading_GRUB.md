---
title: "boot process freezes before loading GRUB"
date: 2020-04-12
forum: General Help
---

### Post by thinkbrick on 2020-04-12
[FONT=Arial]Hi! I would greatly appreciate any kind of help with this boot issue i am experiencing currently as I have already searched the web and this forum and can't seem to find anything on this particular issue. I have an Asus PA90 mini-PC running in dual boot Ubuntu / Windows 10. Each OS is running on a separate ssd and there is an additional SATA data drive which both OSs access. The dual boot setup has been running fine for the past couple of months up until yesterday. I booted up into Ubuntu then later rebooted the machine to change into Windows but before even getting into GRUB the machine freezes on the ASUS press DEL to enter BIOS screen. At this point i can't enter BIOS and the only option left is to power down the machine unplug the ssd running ubuntu and power the machine back up. Now the machine boots straight into Windows. If i reinstall the ssd now and go into BIOS to change the boot order back so it boots from the ssd running Ubuntu at first it seems like all is well. GRUB loads i can boot into Ubuntu as usual. But then if i reboot the machine again i'm back at the frozen ASUS press DEL to enter BIOS screen. To try and resolve the issue I have installed the latest BIOS update from ASUS and I tried my luck with the standard repair setting in boot-repair but so far without success. The BIOS boot order does not seem to be the problem as the machine boots fine once after reinstalling the ssd and setting the correct boot order in BIOS. Also while I am in ubuntu i can check the boot order with efibootmgr which also shows me the correct boot order. I tried fsck in recovery mode to check for possible corruptions in the root filesystem but receive an error message saying the check can't be performed on a mounted drive.[/FONT][FONT=Arial]
[/FONT]
[FONT=Arial]To see boot-repair log:  [/FONT]
[FONT=Arial][https://paste.ubuntu.com/p/BmwVxfBK5N/](https://paste.ubuntu.com/p/BmwVxfBK5N/)  [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Any kind of advice would be greatly appreciated as I am currently at a loss for any further possible solutions.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Thanks![/FONT]

---

### Post by CelticWarrior on 2020-04-12
Mounted file system cannot be checked indeed. That why we do it in a live session, not from a running OS. Try that because the symptoms really suggest corruption.

---

### Post by oldfred on 2020-04-12
Windows turns fast startup back on with updates. You need to turn it off.
Also UEFI update resets some settings back to defaults. You have to redo those you change. I have 7 or so, some optional that I have to redo every update.

Line #13 of report:
> Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by thinkbrick on 2020-04-12
Thank you! Will try doing the check from live session tomorrow.

---

### Post by CelticWarrior on 2020-04-12
> **thinkbrick said:**
> Thank you! Will try doing the check from live session tomorrow.

Actually what oldfred said makes a lot more sense and he took the time to read the report, I didn't. And regardless of that detail, whenever I say something and oldfred says differently, always go with oldfred.

---

### Post by thinkbrick on 2020-04-12
Thank you for your suggestions oldfred. I am kind of confused about the report section about windows being in hibernation because I have in fact checked the fast startup and hibernation options multiple times and the radios for both options are definitely set to off in windows system settings. Is there perhaps another setting in windows 10 that overrides these radios? As for UEFI BIOS settings I have disabled secure boot as this has always caused problems with this machine. I checked for settings to enable or disable fastboot in BIOS but couldn't find anything of the sort. Any other suggestions what I should watch out for in BIOS? Thank you guys again for your efforts! I will try CelticWarrior's suggestion about the filesystem check tomorrow and keep this thread updated with the results.

---

### Post by thinkbrick on 2020-04-13
So I havent resolved my issue yet but i think i am making progress. I did some digging in the Windows registry as that line in the boot-repair log was very suspicious. Turns out hibernation was active even though it was set to off in the system settings. So i turned hibernation off using the windows command line and the registry entry shows hibernation as turned off now. So far so good. 

Unfortunately this has not resolved my issue. 

So next up i booted up a live session from which i am typing now to perform fsck on /dev/nvme0n1 (which is the ubuntu ssd). Unfortunately i am not quite sure what to make of the terminal output but i will attach it below and maybe you guys can help me with that. So i guess my question is... Is there a filesystem repair option or is my ubuntu install beyond repair and i have to do a clean install? 

Thanks again for your time. As always, your help is greatly appreciated!

```
ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1
fsck from util-linux 2.33.1
e2fsck 1.44.6 (5-Mar-2019)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/nvme0n1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a gpt partition table in /dev/nvme0n1
```

I also performed fsck on all individual partitions on the drive but terminal output reported all partitions to be clean...

---

### Post by oldfred on 2020-04-13
You cannot run fsck on a drive, so that would give errors.
You can only run fsck on ext family (ext2, ext3, ext4) of partition formats. Although there is fsck.dos for vfat/FAT32.

---

### Post by thinkbrick on 2020-04-15
So after I unsuccessfully spent half of today trying to figure out what was going on I finally decided to just format the entire ubuntu drive and clean install. Much to my surprise after doing so the issue remains exactly the same. So I am guessing the problem must be in BIOS?
Really at this point any and all advice is very welcome!

---

### Post by oldfred on 2020-04-15
Have you updated UEFI and SSD firmware?
Is drive set for AHCI?
Do you finally have Windows fast start up off?

---

### Post by thinkbrick on 2020-04-17
UEFI BIOS and SSD firmware is latest available.
Both os drives are NVMe M2 SSDs. SATA mode in BIOS is set to AHCI.
All registry keys listed in the links you provided show Windows fast start up to be off. After running [COLOR=#3E3E3E][FONT=Consolas]powercfg -h off[/FONT][/COLOR] settings for fast start up and hibernate disappeared from control panel all together. Is there another way to be sure it's actually off?

[COLOR=#3E3E3E][FONT=Consolas][/FONT][/COLOR]Should i perhaps be looking at ERP or TPM settings in BIOS?

---

### Post by oldfred on 2020-04-17
From Linux you cannot mount a NTFS partition read/write, just read only manually. 
So default mount will not work and give a generic error. 
The Linux NTFS driver will not mount hibernated nor partitions needing chkdsk to prevent further damage.

Settings I change in UEFI are AHCI, fast boot off, allow USB boot, full USB support, turn off network boot as will never use that, maybe a couple others. But every vendor implements the UEFI standard somewhat differently.
Since system did work for a couple of months not sure what issue then is.

Some Asus models need pci=nomsi boot parameter. 
ASUS X540U pci=noaer instead of pci=nomsi and it also worked
[https://ubuntuforums.org/showthread.php?t=2391201](https://ubuntuforums.org/showthread.php?t=2391201)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)

---

### Post by thinkbrick on 2020-04-17
I finally got it running again. Seems the issue was the Asus boot splash. ](*,)I disabled the Asus boot logo and now everything seems to be running perfectly. I have no idea why this didn't create any issues in the past but what ever... I'm just happy it runs again. Thank you for your help!

---

### Post by CelticWarrior on 2020-04-17
I think a firmware update is in order.

---

