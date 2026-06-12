---
title: "Upgrading to Ubuntu 24 on my dual-boot laptop broke my filesystem table. Help!"
date: 2024-11-11
forum: General Help
---

### Post by machinus on 2024-11-11
Hello,

I have a dual-boot laptop that has 1 Ubuntu installation and 1 Windows installation in GRUB. Here is partition configuration:

[IMG]https://i.imgur.com/t1rbWKO.png[/IMG]

I tried to upgrade from 22 to 24 yesterday, and the upgrade worked without any errors. But, when I went to restart, I saw that this upgrade broke my fstab file (I think), and I can no longer load the OS. It looks like the fstab was improperly altered without it being restored during the installation.

I get many errors, depending on how I configure fstab, and I don't know how to fix them. I can boot from a Live USB and view the fstab file. Here is the output from blkid:

[HTML]/dev/sda1: LABEL="windows" BLOCK_SIZE="512" UUID="7A7405AA70AE9E28" TYPE="ntfs" PARTUUID="dfed2d2c-01"
/dev/sda3: LABEL="swap" UUID="152a0490-bd72-45e1-bf6c-f50be9711359" TYPE="swap" PARTUUID="dfed2d2c-03"
/dev/sda5: UUID="9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1" BLOCK_SIZE="4096" TYPE="ext4" PTTYPE="dos" PARTUUID="dfed2d2c-05"
/dev/sdc1: LABEL="UBUNTU 24_0" UUID="1A88-8002" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="059287c5-01"
/dev/loop1: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop2: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop0: BLOCK_SIZE="131072" TYPE="squashfs"
[/HTML]

And the table:
[HTML]
UUID=7A7405AA70AE9E28 / ntfs defaults 0 1
UUID=152a0490-bd72-45e1-bf6c-f50be9711359 none swap defaults 0 0
UUID=9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1 /home ext4 defaults 0 1
[/HTML]

How do I fix my installation?

---

### Post by yancek on 2024-11-12
How did you do the update/upgrade?  Terminal commands, GUI software manager?  Not sure how you expect anyone to tell you if there is a problem with your fstab file since you did not post it.  Also, you did not post which version of windows you are using which would be useful.  You also don't indicate what happens when you try to boot Ubuntu or Windows, warning/error messages?

> UUID=7A7405AA70AE9E28 / ntfs defaults 0 1
UUID=152a0490-bd72-45e1-bf6c-f50be9711359 none swap defaults 0 0
UUID=9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1 /home ext4 defaults 0 1 

If the above is the contents of your fstab file, you don't have a / filesystem partition there but only a /home partition which I would certainly not expect to happen without user input.

---

### Post by dragonfly41 on 2024-11-12
I don't recognise that GParted dump. I have dual boot and my first partition is for Boot.

Looking at my dual boot in GParted I have
**/dev/sda1 EFI system partition 100MB flags boot, esp**
/dev/sda2  Microsoft reserved partition 60 MB
/dev/sda3  etc.
/dev/sda4  etc.


and I have installed reFind.

I think you need a first boot  FAT partition 500 MB or so.

---

### Post by oldfred on 2024-11-12
Because you only have one NTFS with boot flag and MBR(msdos) partitioning since you have extended partition, your Windows is installed in old BIOS/MBR configuration. New systems since 2012 are UEFI with gpt partitioning as Microsoft required vendors to install in UEFI/gpt mode.

Often very old systems that are BIOS/MBR need a lightweight flavor to work well. Ubuntu works best on systems that also can run Windows 11.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)
I use Kubuntu which is more mid-weight, but has worked on my very old 2006 laptop and is used on my newer systems.

---

### Post by machinus on 2024-11-12
> **oldfred said:**
> Because you only have one NTFS with boot flag and MBR(msdos) partitioning since you have extended partition, your Windows is installed in old BIOS/MBR configuration. New systems since 2012 are UEFI with gpt partitioning as Microsoft required vendors to install in UEFI/gpt mode.

Yes, I think you are correct. I need to fix this OS before I can make any changes to my setup, though. I was able to boot with 22, but not now with 24. Do you know how I can fix my fstab to make that work?

---

### Post by dragonfly41 on 2024-11-12
Try installing 15 days free trial EasyUEFI in Windows to inspect your setup.

---

### Post by yancek on 2024-11-12
It's hard to make suggestions with the limited information you provide.  First off, do you actually have some version of windows installed and if so, what is it?  As indicated in an earlier post, you have the older style dos/Legacy/CSM install which is shown by the existence of an Extended partition (/dev/sda4) which would not exist on a GPT drive.  You don't have an EFI partition which was also pointed out which also confirms a Legacy install.  

What you refer to in your initial post as 'the table' looks like part of an fstab file and shows  /home, swap and ntfs partitions.  If the line below is from your fstab file, it shows the / filesystem mounted with the UUID and a windows ntfs filesystem.  Not sure how that would happen without some user intervention.  Usually you will see this line just above the / partition:  # / was on /dev/sda1 during installation so if that was your / partition, you've apparently formatted it ntfs and basically overwritten the / filesystem.

> UUID=7A7405AA70AE9E28 / ntfs defaults 0 1 

---

### Post by machinus on 2024-11-12
> **yancek said:**
> It's hard to make suggestions with the limited information you provide.  First off, do you actually have some version of windows installed and if so, what is it?  As indicated in an earlier post, you have the older style dos/Legacy/CSM install which is shown by the existence of an Extended partition (/dev/sda4) which would not exist on a GPT drive.  You don't have an EFI partition which was also pointed out which also confirms a Legacy install.  

What you refer to in your initial post as 'the table' looks like part of an fstab file and shows  /home, swap and ntfs partitions.  If the line below is from your fstab file, it shows the / filesystem mounted with the UUID and a windows ntfs filesystem.  Not sure how that would happen without some user intervention.  Usually you will see this line just above the / partition:  # / was on /dev/sda1 during installation so if that was your / partition, you've apparently formatted it ntfs and basically overwritten the / filesystem.


This laptop has Windows 7 as the other installed OS. I can boot into that at the GRUB screen.


The fstab file I showed above is my attempt to write one. It's all "user intervention." The old one was erased when I upgraded. I do not have a working fstab or any reference file. I need to know how to construct one that will allow me to boot into Ubuntu with the type of setup I have, which as you mentioned is the DOS/Legacy/CSM type.

I included the blkid output to help figure out how to write a working fs table.

---

### Post by yancek on 2024-11-12
Did you have a separate /home partition prior to the upgrade?  
Did you have only a / filesystem partitions?
Do you know which partition was the / filesystem partition?  Was it sda5?
There is no reason for the old fstab file to be erased during an update/upgrade.  Take a look at the link below which is an Ubuntu site explaining creating an fstab file, what you need and also some example files.  I would first try editing the crrent fstab file below, replace /home with /.

```
UUID=9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1 /home ext4 defaults 0 1
```

   [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by machinus on 2024-11-12
> **yancek said:**
> Did you have a separate /home partition prior to the upgrade?  
Did you have only a / filesystem partitions?
Do you know which partition was the / filesystem partition?  Was it sda5?
There is no reason for the old fstab file to be erased during an update/upgrade.  Take a look at the link below which is an Ubuntu site explaining creating an fstab file, what you need and also some example files.  I would first try editing the crrent fstab file below, replace /home with /.

> UUID=9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1 /home ext4 defaults 0 1

   [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I spent a lot of time trying different fstab configurations through a Live USB and then restarting. I have not been able to identify the correct lines yet.

I tried the one you suggested. That gives this error,

[HTML][ TIME ] Timed out waiting for device /dev/disk/by-uuid/9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1[/HTML]

And then gives the Emergency Mode console. I was not able to accomplish much there.

The partitions shown in the gparted console are unchanged from what they were before. So, there was no home partition and only the ones shown there existed before.

So, I tried this instead

[HTML]UUID=9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1    /    ext4    defaults    0    0[/HTML]

This gives "Dependency for SSSD Failed" errors.

Does this give any clues for what to do next?

---

### Post by dragonfly41 on 2024-11-13
I can write what I would do. Cut your losses, lick your wounds and start again.
Buy a brand new SSD in an external powered container (not touching your current failed setup).
Create LiveUSB to install Ubuntu into your external container (best to use USB 3.0 port if you have one since USB 2.0 port is slow to run Ubuntu in an external SSD caddy).
Partition your external caddy for modern day EFI usage (not legacy).
Optionally install rEFInd (my favourite) so that in a GUI you see the various options.
Set your BIOS to boot into rEFInd (if you agree to install this grub manager).
Boot up your fresh Ubuntu. Remember no Windows at this stage just pure Ubuntu.
If you need Windows create a VM. Or buy modern Microsoft Windows. Or use your old system.
Start scavenging the files and applications from the old carcass. Your fresh Ubuntu can be setup to hunt for assets from old internal drive and pull into your reincarnated external Ubuntu in SSD/caddy. A long process and I recommend Recoll to index internal/external assets.
You can still retain the old internal system but your laptop is just the mothership and the real action is now in your new Ubuntu.
Look to Crucial.com to see external USB plugin SSD's working.

---

### Post by ajgreeny on 2024-11-13
We seem to be going round in circles here and getting no clues from the information you've given us so my suggestion, though probably not what you wanted to hear is this:-

Do you have backups of your personal files?
Assuming you do, (and if not why not?), the best way to proceed may be to reinstall your Ubuntu system and then restore your files.

Windows 7 should not be used online any more as it's been out of support now for a long time and is not secure so using a version of the Ubuntu family that requires lower resources may be your best choice in view of what I assume is a fairly old computer.

If you can run a live version of, for example Xubuntu, run terminal command 
**sudo fdisk - l**
and show us the output here using code tags please, which will give us more detail of your disks and current partitions.

---

### Post by yancek on 2024-11-13
Do you have a current fstab file you are trying to use?  If you have the line below you posted earlier in it you need to comment it out as it won't work.  You can't have a / filesystem mount point on an ntfs partition so put a # at the beginning of the line as shown.

> #UUID=7A7405AA70AE9E28 / ntfs defaults 0 1 

In your last post, you indicate there was no separate /home partition which means the only possibility for the / filesystem is sda5.  If you get the error you report in post 10 "Timed out waiting for device /dev/disk/by-uuid/9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1" that is completely illogical unless that UUID changed for some reason and that would likely be bad news.

If you get the error you report "Dependency for SSSD Failed", have you done an online search for it?  Take a look at the link below which has some suggestions.  If you are making changes, keep notes of what you do.

If you want to continue trying to resolve this, post the output of fdisk -l suggested above as well as blkid and the current fstab file.

---

### Post by machinus on 2024-11-13
> **yancek said:**
> Do you have a current fstab file you are trying to use?  If you have the line below you posted earlier in it you need to comment it out as it won't work.  You can't have a / filesystem mount point on an ntfs partition so put a # at the beginning of the line as shown.

In your last post, you indicate there was no separate /home partition which means the only possibility for the / filesystem is sda5.  If you get the error you report in post 10 "Timed out waiting for device /dev/disk/by-uuid/9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1" that is completely illogical unless that UUID changed for some reason and that would likely be bad news.

If you get the error you report "Dependency for SSSD Failed", have you done an online search for it?  Take a look at the link below which has some suggestions.  If you are making changes, keep notes of what you do.

If you want to continue trying to resolve this, post the output of fdisk -l suggested above as well as blkid and the current fstab file.

There was only one line in the fstab file each time I tried to boot. There were no other lines in the file. 

Using this line
```
/dev/sda5    /    ext4    defaults    0    1
```
gives the error "Timed out waiting for device" on boot.

fdisk shows the hard drive, the USB drive, and a bunch of /dev/loops.

Hard disk:
```
Disk /dev/sda: 232.89 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 840
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdfed2d2c


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 146802687 146800640    70G  7 HPFS/NTFS/exFAT
/dev/sda3       146802688 163579903  16777216     8G 82 Linux swap / Solaris
/dev/sda4       163581950 488396799 324814850 154.9G  5 Extended
/dev/sda5       163581952 488396799 324814848 154.9G 83 Linux

```


Live USB:
```
Disk /dev/sdc: 29.3 GiB, 31457280000 bytes, 61440000 sectors
Disk model: UDisk          
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x069140b2


Device     Boot    Start      End  Sectors  Size Id Type
/dev/sdc1  *         128 61439839 61439712 29.3G  c W95 FAT32 (LBA)
/dev/sdc2       61439931 61439993       63 31.5K ea Linux extended boot

```

---

### Post by yancek on 2024-11-13
> /dev/sda5    /    ext4    defaults    0    1

Is that what you have in your fstab file now?

> Timed out waiting for device /dev/disk/by-uuid/9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1

If you change your fstab to use the UUID example above instead of /dev/sda5, do you still get the above error?  Have you run blkid again.  That's the correct UUID from your earlier posts.  Did you look at the /boot/grub/grub.cfg file and check your menuentry for Ubuntu?

---

### Post by machinus on 2024-11-13
> **yancek said:**
> Did you look at the /boot/grub/grub.cfg file and check your menuentry for Ubuntu?

The grub.cfg shows that UUID is the device for all the Ubuntu options.

> **yancek said:**
> If you change your fstab to use the UUID example above instead of /dev/sda5, do you still get the above error? Have you run blkid again.

If I boot with the file
```
UUID=9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1 /home ext4 defaults 0 1
```

I get "Failed to start service for snap application cups" and then dropped a console where I have no network access or access to system utilities.

In the fdisk output I posted earlier, sda1 is indicates as the boot drive by the asterisk. Does that mean anything?

---

### Post by Quarkrad on 2024-11-14
As **ajgreeny** said - have you any backups?  I don't think you have answered that question yet.  I think your first move is to boot via a 'live cd' and drag off all your personal files, if you have no backups.  At least you will have the piece of mind that if things go horribly wrong you have your personal files.

---

### Post by dragonfly41 on 2024-11-14
+1 ... I offered same thoughts in post #11 but it falls on deaf ears (or is it eyes).

---

### Post by oldfred on 2024-11-14
You keep posting a mount of /home, but not / (root).
And you say you do not have a /home as a separate partition which would be the only way fstab would have a line to mount /home.

---

### Post by yancek on 2024-11-14
You need to change the entry you have show and been told to several times from /home as a mount point to / which it likely was originally.

>  [UUID=9ce87bbe-ecfb-4856-96bc-2635c7d4a3b1 / ext4 defaults 0 1

---

### Post by machinus on 2024-11-14
> **yancek said:**
> You need to change the entry you have show and been told to several times from /home as a mount point to / which it likely was originally.

I previously posted that this gives the error "Dependency for SSSD Failed." No mount point is correct. There may be something else wrong besides just the fstab file, but I can't diagnose it.[COLOR=#000000]
[/COLOR]

---

### Post by oldfred on 2024-11-14
Not necessarily an issue.
[https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/2048436](https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/2048436)
> It's not an error though. It's just logging that it didn't start sssd,  which isn't an error for a user who doesn't need the enterprise  integration that sssd provides.

---

### Post by Quarkrad on 2024-11-15
What does your fstab file look like at the moment?  Please show us.

---

