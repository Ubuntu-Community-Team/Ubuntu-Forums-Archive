---
title: "Moving Ubuntu partition to new disk destroyed Windows?"
date: 2023-04-13
forum: General Help
---

### Post by urubu66 on 2023-04-13
Hey all,
I used to run a dual boot Ubuntu 20.04 and Windows10 off a single SSD, but over time both were running out of space constantly and I decided to get a second ssd.
I found some manual online, got a live USB, moved the ubuntu partition to the new ssd with gparted, changed the UUID of the old ubuntu partition, moved the boot flag, tested and both ubuntu and windows worked. 
Now I wanted to expand the Windows partition, so I deleted the ubuntu partition from the old ssd, gparted gave me a warning that I shouldn't expand Windows so I decided to not do so and try to do that using Windows.
Problem is, when I rebooted and tried to go into windows I got a BSOD, stop code INACCESSIBLE BOOT DEVICE
I searched around for a bit, I can still boot into Ubuntu just fine, so I installed the boot repair utility, tried to repair the windows boot but every time I try to do so it gives me the message
> An error occurred during the repair.
--no-nvram exit code: 1 Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

The weird thing is that on the first reboot after this, when I select Windows I get into the windows Start-up repair, which then turns out to be useless.

Any help is appreciated.

I hope this is in the correct section of the forum, if not feel free to move it

---

### Post by tea for one on 2023-04-13
Windows 10 on one disk and Ubuntu 20.04 on another disk is ideal.
Are both systems installed in UEFI mode with GPT?
Do both disks have an [COLOR="#0000FF"]E[/COLOR]fi [COLOR="#0000FF"]S[/COLOR]ystem [COLOR="#0000FF"]P[/COLOR]artition?

---

### Post by urubu66 on 2023-04-13
My old drive (that currently has Windows) had a GUID partition table, the manual I found said I had to use the same one on the new drive so I made that GUID as well, not sure if that was the question. 

There is a Filesytem partition on the old drive (511MB FAT, EFI system partition type), none on the new one.

---

### Post by tea for one on 2023-04-13
Can you boot into Ubuntu 20.04, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
What is the output?

---

### Post by urubu66 on 2023-04-13
UEFI mode

---

### Post by tea for one on 2023-04-13
Isolate, de-activate or remove your Ubuntu disk.
Repair Windows Boot Manager using Windows utilities.
Double-check 2/3 times that Windows 10 boots as normal.

Remove Windows 10 disk.
Attach Ubuntu disk.
Boot into a live session with 20.04 i.e. Try Ubuntu.
Use Gparted to create an ESP with boot and esp flags on this drive.
Then re-install Grub.

You should end up with each disk being independent.
Each using its native boot manager.

If you are unsure how to re-install Grub via a live session, please ask.
It may be quicker to back up and reinstall Ubuntu.

I would back up and re-install Ubuntu because it breeds confidence in using the installer and also confirms that your backup strategy is sound.

---

### Post by urubu66 on 2023-04-13
> [COLOR=#000000]Isolate, de-activate or remove your Ubuntu disk.[/COLOR]
[COLOR=#000000]Repair Windows Boot Manager using Windows utilities.[/COLOR]

Tried that, gave me a white letter black background

> GNU GRUB version 2.06
Minimal BASH-like editing is supported. (...)

grub>



So I couldn't even get into the windows automatic repair (which didn't work for launching windows anyway)

I'm thinking, I can clone the ubuntu partition back to the old drive, maybe that will somehow repair the windows?

I have no idea how to reinstall grub, but reinstalling ubuntu would take a whole day to reconfigure so I really want to avoid that.

---

### Post by urubu66 on 2023-04-13
I tried some things in the windows console that I get in the automatic repair, nothing works so far but I have a log

> 
Startup Repair diagnosis and repair log
---------------------------
Number of repair attempts: 1

Session details
---------------------------
System Disk = 
Windows directory = D:\Windows
AutoChk Run = 0
Number of root causes = 1

Test Performed: 
---------------------------
Name: Check for updates
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: System disk test
Result: Completed successfully. Error code =  0x0
Time taken = 78 ms

Root cause found: 
---------------------------
[B]A hard disk could not be found. If a hard disk is installed, it is not responding.
[/B]
---------------------------
---------------------------
#

So, my guess is uninstalling ubuntu would be pointless, and removing a partition on the harddrive has windows confused?

---

### Post by oldfred on 2023-04-13
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by urubu66 on 2023-04-14
[https://paste.ubuntu.com/p/S22PVFG3Sm/](https://paste.ubuntu.com/p/S22PVFG3Sm/)

between the last post and the report I've tried some things which may have made things worse. 
I made a Macrium Rescue Media live usb and tried to fix Windows, which failed, and when I then tried to do a bootrepair in Ubuntu it deleted the windows boot option altogether.

---

### Post by tea for one on 2023-04-14
You have booted into Ubuntu on sda1, which is good news.
However, the boot process reads the ESP on sdc1 which is your Windows disk.
Windows 10 is unbootable on sdc4.

Boot-repair reports that your sda1 partition is also an ESP - this is very unusual as it should be Fat32 rather than ext4.
[COLOR="#0000FF"]Line 106[/COLOR] > sda1	: is---ESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
Possibly, a result of a failed repair?

At the moment, as you can boot into Ubuntu, back-up both your Windows and Ubuntu data.
Please confirm when you have done this.

Boot-repair will not repair Windows Boot Manager.
It will only add a Working Windows to Grub.

I'm sure that a Windows re-installation on disk sdc will overwrite the ESP and then Ubuntu will not boot, hence the importance of restorable backups.

---

### Post by urubu66 on 2023-04-14
I have backed up the data, but a reinstall of Ubuntu and setting up the software again would take me a whole day so I'd even prefer buying a 3rd ssd to add windows if I could avoid a ubuntu reinstall.

Would a windows reinstall where I leave the sdc1 partition be and give the rest of that drive to windows solve things?

> [COLOR=#000000]Possibly, a result of a failed repair?[/COLOR][COLOR=#000000]
I have no idea, I just followed this manual 
[https://yulistic.gitlab.io/2018/03/replace-hdd-or-ssd-without-the-re-installation-of-ubuntu/](https://yulistic.gitlab.io/2018/03/replace-hdd-or-ssd-without-the-re-installation-of-ubuntu/)
[/COLOR]and things worked, and then I tried a couple times with boot repair and Macrium and got things the way they are now.

---

### Post by tea for one on 2023-04-14
> **urubu66 said:**
> I have no idea, I just followed this manual 
[https://yulistic.gitlab.io/2018/03/replace-hdd-or-ssd-without-the-re-installation-of-ubuntu/](https://yulistic.gitlab.io/2018/03/replace-hdd-or-ssd-without-the-re-installation-of-ubuntu/)
The instructions on that site refer to Legacy rather than UEFI installations.
> I have backed up the data
Including Windows data (because unbootable Windows is the current problem)?
> if I could avoid a ubuntu reinstall
Certainly possible, if you add a functioning ESP to sda (as I mentioned in post 6)
As you have a data backup, do you want to try?
> Would a windows reinstall where I leave the sdc1 partition be and give the rest of that drive to windows solve things?
Does the Widows installer allow you to avoid the existing ESP?
I thought that Windows will probably take complete control of ESP during re-installation.
If you have restorable backups, then it is worth consideration.

---

### Post by urubu66 on 2023-04-14
> [COLOR=#000000]Certainly possible, if you add a functioning ESP to sda (as I mentioned in post 6)[/COLOR]
[COLOR=#000000]As you have a data backup, do you want to try?[/COLOR]

I have backed up both Windows and Ubuntu, I'd like to try

>  [COLOR=#000000]Does the Widows installer allow you to avoid the existing ESP?[/COLOR]
[COLOR=#000000]I thought that Windows will probably take complete control of ESP during re-installation.
I'm not sure. But I can use gparted, copy the sdc1 partition to the new ssd, try to reinstall windows on sdc and if the partition gets overwritten just delete the whole thing again and put the partition back to its original place?
[/COLOR]

---

### Post by tea for one on 2023-04-14
OK, let's try and make the Ubuntu disk independent with an ESP.

Remove/disconnect all disks except the Ubuntu disk (sda)
Remove/disconnect all peripheral devices
Boot into a "Try Ubuntu" session (preferably using the same Ubuntu version as your installation)
Open gparted
Unmount disk (if mounted)
Make space for a new partition of 512MB (preferably at the beginning of the drive)
File system FAT32 with boot and esp flags

Open terminal and run
```
sudo parted -l
```

Please reply with the output when you have completed this and then we'll point Grub at the new partition.

---

### Post by tea for one on 2023-04-14
> **tea for one said:**
> 
Make space for a new partition of 512MB (preferably at the beginning of the drive)
That may be an onerous task if you have to shift lots of data.
Put the ESP at the end of the drive, it should not matter.

---

### Post by urubu66 on 2023-04-15
done

```
Model: ATA CT250MX500SSD1 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  50,0GB  50,0GB  ext4               boot, esp
 2      250GB   250GB   537MB   fat32              boot, esp



```

---

### Post by dragonfly41 on 2023-04-15
Optionally, you might add rEFInd into that partition alongside usual grub installation. Offers nice GUI.

---

### Post by oldfred on 2023-04-15
You can only have one ESP per drive with most UEFI systems.
And it must be FAT32.

Remove with gparted the boot,esp flags from sda1.

---

### Post by urubu66 on 2023-04-15
> **oldfred said:**
> 
Remove with gparted the boot,esp flags from sda1.
Done.

---

### Post by tea for one on 2023-04-15
Splendid, only one partition with esp and boot flags.
Now, we'll try and install grub via a live session.
Only the target device should be attached.
Boot into a live session, open a terminal and enter these commands one at a time.
```
sudo mount /dev/sda1 /mnt  [COLOR="#0000FF"]# mount root partition[/COLOR]
```
```
sudo mount /dev/sda2 /mnt/boot/efi [COLOR="#0000FF"]# mount efi partition[/COLOR]
```
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done [COLOR="#0000FF"]# mount other directories needed by grub[/COLOR]
```
```
sudo chroot /mnt [COLOR="#0000FF"]# chroot into new environment[/COLOR]
```
```
grub-install /dev/sda [COLOR="#0000FF"]# install grub[/COLOR]
```
```
grub-install --recheck /dev/sda [COLOR="#0000FF"]# doublecheck[/COLOR]
```
```
update-grub [COLOR="#0000FF"]# find available kernels[/COLOR]
```
```
exit
```
Power off PC and remove USB stick
Power on

Any error messages, please post command and message within code tags.
Fingers crossed.

---

### Post by urubu66 on 2023-04-15
Just did all that and it works! 
I booted with only the new ssd attached, thanks guys!

Is there anything I should pay special attention to when installing windows on the other disk?

---

### Post by tea for one on 2023-04-15
> **urubu66 said:**
> Is there anything I should pay special attention to when installing windows on the other disk?
Good news that Ubuntu boots independently.
When you re-install Windows 10/11, just make sure that you only have one target disk visible to the installer.
The Windows installer will automatically create an Efi Partition together with GPT.
Therefore, with an ESP on each bootable disk, Ubuntu and Widows can be booted via the dedicated key to access the PC boot menu (F2, F10 or similar)

You can add Windows Boot Manager to grub later if you wish.

---

### Post by tea for one on 2023-04-15
In post 18, dragonfly41 mentioned rEFInd.
It's a handy boot manager for UEFI systems.
You do not have to install it, you can run it from a USB stick (ideal for emergencies).
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)  [COLOR="#0000FF"]> A USB flash drive image file[/COLOR]

---

### Post by urubu66 on 2023-04-16
I've installed windows on the old drive and added it to the grub menu.
problem is that with both drives connected, it boots straight into windows unless I dash F11 and get to select between windows boot manager or ubuntu, with the choice for ubuntu leading to the grub screen that lets me pick between ubuntu and windows.
I've tried editing the boot order in my motherboard bios, but it doesn't see the ubuntu ssd. It sees a bunch of usb keys, uefi cd, floppy, and the hard drive with the windows boot manager on it (sata4), but not the new one

---

### Post by tea for one on 2023-04-16
Lots of progress made so far.
Two disks and two independent operating systems.

Your UEFI settings (i.e.motherboard) must see your Ubuntu ssd because you said it boots independently.
I suspect that this is a problem identifying the correct description of your ssd.

Remove the Windows disk and all other disks/peripheral devices.
Boot into Ubuntu and then power off.
Power on and access your UEFI settings.
Can you recognise your Ubuntu ssd?

---

### Post by urubu66 on 2023-04-16
Solved it.

In the motherboard bios there is only 1 entry for sata, but there's a submenu for changing drive priority. Putting the Ubuntu disk on top makes it boot to grub.

---

### Post by tea for one on 2023-04-16
Therefore, it's important to know how to manipulate the UEFI firmware of each PC.
There is little consistency in each vendor's treatment of UEFI firmware and it is necessary for each PC owner/user to understand the various options.

Anyway, this successful outcome would benefit from marking the thread as solved because other users/searchers may find the info. helpful.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

