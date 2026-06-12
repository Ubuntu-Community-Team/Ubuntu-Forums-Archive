---
title: "upgrade failed, grub confused, working my way back"
date: 2024-05-23
forum: General Help
---

### Post by aeronutt on 2024-05-23
23.10 to 24.04 upgrade crashed spectacularly.  I "had" to reinstall an OS to get back to a booting system (back to KDE and Windows at least).

But something weird is going on with Grub.  If I run "boot-repair" in KDE, it gives an error that it "can't create a boot option for the current OS", but then if I run update-grub, it creates it.  Looking at UEFI during boot, shows some weird stuff. Running 'bootinfoscript' doesn't reveal anything to me.

bootinfoscript:
[https://docs.google.com/document/d/1Cy39JCPXKq51Qvq9cY9DbPtYy6owg0DhtW00r0e-Ej0](https://docs.google.com/document/d/1Cy39JCPXKq51Qvq9cY9DbPtYy6owg0DhtW00r0e-Ej0)

Pic of UEFI:
[https://drive.google.com/file/d/1BDGwMU_4JR7S0NkxoWVFWSa8eyjq7F9F](https://drive.google.com/file/d/1BDGwMU_4JR7S0NkxoWVFWSa8eyjq7F9F)

Next step to figure out what's going on?

---

### Post by yancek on 2024-05-23
The output you posted is uninformative and does not show even a fraction of the information we would expect from the boot repair software so boot your system or the live usb and go to the boot repair site at the link below and download and run the script using the 2nd option described on the page.  Select the Create Bootinfo Summary option and post the link here that you get when the script finishes.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by aeronutt on 2024-05-23
Thanks, 
Here we go, this is more like it:

[https://docs.google.com/document/d/1Qq_vR3tKeXZF-DC6assNkJfVY6tWE-tFfOszJVoyb9M](https://docs.google.com/document/d/1Qq_vR3tKeXZF-DC6assNkJfVY6tWE-tFfOszJVoyb9M)

---

### Post by yancek on 2024-05-23
The output from efibootmgr only shows an entry for Neon Boot0004.  When you select that option, does it boot?  If you scroll down the page, you can see 2 identical grub.cfg file on the EFI partition, 1 in the neon directory and one in an ubuntu directory.  They both point to the same partition, partition 10.  Partition 9 looks like the old neon install and you installed again to partition 10 rather than over the previous install?

Your /boot/grub/grub.cfg on partition 9 shows an entry for Ubuntu 24.04 on partition 8 but that partition does no show at the top of the report where there is information on the other partitions.   Are you using encryption?

What are you able to boot now?  Ubuntu, Neon, Windows.  If you can boot Neon or Ubuntu, open a terminal when you do an run the command:  df -h
That should show which parittion is the root / filesystem partition for each.

Your boot repair does not look right as if you use the 2nd option on their page as suggested, the lines in the file would be numbered which makes it a lot easier to point out problems.

---

### Post by aeronutt on 2024-05-23
Messy, huh?

Here are the options  shown on power up.
[https://drive.google.com/file/d/1KD4X8Wqzxn0E4124RMCsjoJw7VJgRx_q](https://drive.google.com/file/d/1KD4X8Wqzxn0E4124RMCsjoJw7VJgRx_q)
I just noticed, I am confused about the references to /dev/dev/nvme1n. None of the OS's are installed on that disk. And nvme1n has only 2 partitions, nvme1np1 and nvme1np2

The first OS, Neon, is installed on partition /dev/nvme0n1p10, and boots.  This is the KDE partition I installed after the 24.04 upgrade failed (it's the USB iso I had handy).
"Windows Boot Manager boots on /dev/nvme1np1" boots fine. 
"KDE 6.0 neon 22.04 (on /dev/nvme1n1p9)" does not boot. It hangs late in the stage of boot but before login page.

None of the OSs partitions are encrypted, BUT, /dev/nvme1np1 IS.

It's like grub is getting nvme1n and nvme0n confused?

---

### Post by aeronutt on 2024-05-24
Ok, something is really messed up.
Can the /dev location of a disk change?
I'm now showing my OS's to be on nvme1n1

---

### Post by aeronutt on 2024-05-24
I may be going crazy and have too much caffeine, lol, but.....

A snippet from bootinfo from yesterday:
**nvme0n1**:512GB:nvme:512:512:gpt:PC801 NVMe **SK hynix** 512GB    

A snippet from fdisk -l today:
Disk /dev/**nvme1n1**: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: PC801 NVMe **SK hynix** 512GB      


The same physical disk getting mounted at /dev/nvme0n1 yesterday and /dev/nvme1n1 today.

Does grub use mount point or UUID or?

---

### Post by yancek on 2024-05-24
> I just noticed, I am confused about the references to /dev/dev/nvme1n.  

Why?  What is on the first partition?  Is that just a Linux encrypted data partition.  The second partition on that drive looks to be just a windows data partition.

 > "Windows Boot Manager boots on /dev/nvme1np1" boots fine.  

No, are you referring to [COLOR=#000000][FONT=Arial]nvme1n1p1, because that shows as "crypto LUKS" which is "[/FONT][/COLOR] [B]a specification for block device encryption" so it should have nothing to do with windows.  I don't know why your EFI boot options show that?  Did you at some point switch ports for the drives?
Your EFI partition which contains both the LInux and windows EFI boot files is   [/B][COLOR=#000000][FONT=Arial]nvme0n1p1: [/FONT][/COLOR]
Windows filesystem partition is [COLOR=#000000][FONT=Arial]nvme0n1p3 which shows in boot repair under OS detected.  That also shows Neon on partition 9 and 10 but does not show any sign of Ubuntu on partition 8.

Disk device names can change so if you have an internal drive showing as sda and you boot up a flash drive, the flash drive OS would show as sda and the internal drive formerly shown as sda would show as sdb/sdc, etc. depending upon the number of drives.  The SSD device names can also change but should not unless a user is removing/replacing or adding drives or changing ports.  If you have been removing and replacing drives, don't do that as it confuses everything.  If you have not been doing that, I don't know why they are changeing.  If you have looked at any grub.cfg file, you will see that it uses UUIDs.

Your boot repair does show a partition 7 with an ext4 filesystem exists.  Is that where you tried to install Ubuntu?  Can you boot into Neon and try to mount that partition to see if the expected Ubuntu files are there?

Boot repair shows partition 7 with no OS and partition 8 does not even show.  It shows an OS installed on partition 3 (windows), 9 and 10 (Neon).
[/FONT][/COLOR]
If I understand, your problem is that your upgraded Ubuntu which is supposed to be on partition 7 of the first %12GB drive does not boot so mount that partition and take a look at it to see if the necessary files are there.  Boot repair detected an ext4 filesystem on that partition but not an OS and it shows that partition as less than 10GB so that is too small for an Ubunt install.

Did you adopt the suggestion at the end of boot repair to mount the encrypted partition so contents could be verified?  Not sure if that would be useful as I don't know what is on that partition.

---

### Post by aeronutt on 2024-05-24
First, thanks for the quick responses and help.

My current problems:
- I can't boot previous install of KDE (partition 9), which was working fine before crashed upgrade of Ubuntu.
- When I run boot-repair, it always says "can't add current OS to grub". Which seems to imply something is fundamentally wrong, and I'm concerned about what will happen when update-grub is run during an update.

I have 2 SSDs.  On one I have all the OS's. The other has 2 partitions, an encrypted partition for data, and an NTFS partition for data.
Oddly, mount points are changing between boots. (It literally just swapped /dev/dev/nvme1n and /dev/nvme0n after a few boots.)
But, maybe that's not the root problem if grub uses UUID's.

"...your EFI partition which contains both the LInux and windows EFI boot files is nvme0n1p1"
To be clear, that sometimes changes between nvme0n1p1 and nvme1n1p1 after a reboot.

"Did you adopt the suggestion at the end of boot repair to mount the encrypted partition so contents could be verified? Not sure if that would be useful as I don't know what is on that partition. "
Yes, I did do that at least once during boot-repair.  My 2 problems stated above didn't change.

"...your problem is that your upgraded Ubuntu which is supposed to be on partition 7"
Sorry, nope.  Partition 7 is just a small data partition with some scripts. Ubuntu was installed on partition 8. What started all this, was an attempt to update that from 23.10 to 24.04 which crashed, and laptop wouldn't boot. After a few failed attempts of using boot-repair from USB, I deleted partition 8/Ubuntu. Eventually, I installed KDE from USB, and at least got a system that boots.

---

### Post by yancek on 2024-05-24
>  I can't boot previous install of KDE (partition 9), which was working fine before crashed upgrade of Ubuntu.

So is that what you now want to do, to be able to boot Neon on partition 9?  When you boot Neon, verify if you have not yet, that you are using Neon on partition 10.  You can do that with the df -h command which should show output similar to the example below:

```
 /dev/nvme0n1p10   47G   20G   25G  45% /

```

You should see the forward slash indicating the root system partition at the end of that line.  If you are booted into Neon on partition 10, go to the /boot/grub/grub.cfg file and check it for any entries for Neon on partition 9.  If there are any entries, check the UUID used in each entry with the UUID you get for partition 9 using sudo blkid.

I'm not sure what your problem is now.  Do you want to be able to access Neon on partition 9 or do you want to install Ubuntu over that partition?

>  Oddly, mount points are changing between boots. (It literally just swapped /dev/dev/nvme1n and /dev/nvme0n after a few boots.)

Those are device names not mount points and should not change if you are booting from the USB shown as sda in boot repair or if you are booting from Neon on the /dev/nvme0n device, the one on partition 10.  I noticed in your boot options from an earlier image that windows was shown as nvme1n1p1?  Boot repair shows it on [COLOR=#000000][FONT=Arial]nvme0n1p3.  This is not expected to change unless the drives are being attached to different ports between boots so I don't know why that happens. [/FONT][/COLOR]

---

### Post by aeronutt on 2024-05-24
Ok, so I decided to try a few things to see if my fears were warranted. 
Let's ignore KDE on P9, I've given up on that.

1) Run update-grub from KDE p10. **YES**, all is ok.
2) Run boot-repair from KDE p10. **NO**. It runs, but ends with a warning "can't add current OS", then when I reboot, it goes to BIOS no matter what.
3) Install Ubuntu 24.04. **YES**, and all OS's work as expected (except KDE p9).
4) Run boot-repair from Ubuntu 24.04. **NO**. Same problem as with KDE p10. Ends with the notice below, and reboot goes to BIOS no matter what.

Here's what boot-repair showed after running it in Ubuntu 24.04 (and forcing BIOS only boots)
[https://drive.google.com/file/d/1bPXOdVA4Js9h9kp6BZiggTjZAKxHqHG4](https://drive.google.com/file/d/1bPXOdVA4Js9h9kp6BZiggTjZAKxHqHG4)

So, maybe the problem is boot-repair.

I will say, I still don't understand the nvme0n vs nvme1n thing. During one boot, grub showed the OS's selections all on nvme0n, then when I actually selected one and booted, fdisk showed the OS disk as /dev/nvme1n  .

---

### Post by aeronutt on 2024-05-24
Follow up, I have read from several sources that yes, disk lables assigned at boot are random (even if nothing else changes). I guess I'd never noticed it before, but also knew when I'm writing scripts to not use those labels. lol.

So I think we're down to a boot-repair bug.  And it all started because ubuntu upgrade screwed my system.

---

### Post by oldfred on 2024-05-25
Back when only booting with HDDs we would sometimes see drive order change. Part of reason UUIDs became way to mount partitions. BIOS would order drives in order they came up and HDDs did not always come up at same speed.
Have not seen that with SSD, nor NVMe drives. But not a lot of systems with multiple NVMe drives.

What brand/model system? Is UEFI firmware & NVMe firmware the most current version?
sudo dmidecode -s bios-version
udisksctl status
or install nvme-cli:
sudo nvme list

What is the partition mybootfiles? You are not sharing boot files from multiple installs are you?

---

### Post by aeronutt on 2024-05-25
> **oldfred said:**
> Back when only booting with HDDs we would sometimes see drive order change. Part of reason UUIDs became way to mount partitions. BIOS would order drives in order they came up and HDDs did not always come up at same speed.
Have not seen that with SSD, nor NVMe drives. But not a lot of systems with multiple NVMe drives.

What brand/model system? Is UEFI firmware & NVMe firmware the most current version?
sudo dmidecode -s bios-version
udisksctl status
or install nvme-cli:
sudo nvme list

What is the partition mybootfiles? You are not sharing boot files from multiple installs are you?

**"Have not seen that with SSD, nor NVMe drives."**
The /dev/nvme naming switch happens often and as far as I can tell, randomly. 

**"What brand/model system? Is UEFI firmware & NVMe firmware the most current version?"**
Dell XPS 15 9530, everything's up to date according to lvfs.

**"sudo dmidecode -s bios-version"**
```
1.12.0
```

**"udisksctl status"**
```
MODEL                     REVISION  SERIAL               DEVICE
--------------------------------------------------------------------------
Samsung SSD 970 EVO Plus 1TB 2B2QEXM7  S59ANM0RA15223N      nvme0n1 
PC801 NVMe SK hynix 512GB 51003141     SYC1N00711050161L nvme1n1 
```

**"sudo nvme list"**
```
Node                  SN                   Model                                    Namespace Usage                      Format           FW Rev  
--------------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1          S59ANM0RA15223N      Samsung SSD 970 EVO Plus 1TB             1         802.65  GB /   1.00  TB    512   B +  0 B   2B2QEXM7
/dev/nvme1n1             SYC1N00711050161L PC801 NVMe SK hynix 512GB                1         512.11  GB / 512.11  GB    512   B +  0 B   51003141
```

**" What is the partition mybootfiles? You are not sharing boot files from multiple installs are you?"**
Correct, no boot files shared. It's a handful of scripts and icons I share at login (used in .profile or .bashrc).
Basically, my laptop is setup like this:
512GB NVM:
- efi partition
- Windows, and associated partitions.
- 2 or 3 Linus OS's, always Ubuntu and another 1 or 2 to experiment with.
1TB NVM:
- various "data" directories I access only during or after a login. One of the partitions is encrypted.

---

### Post by oldfred on 2024-05-25
You are showing the Locked NVRAM issue which I am not sure is a real issue or just a bug in modprobe, grub or Boot-Repair.
But as fatal error seems to stop grub or Boot-Repair from finishing.
Error seems to be where modprobe does not see efivars. From my system.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo modprobe efivars [/COLOR]
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.8.0-31-generic
[/FONT]
```

But efivars is really here not as module, but many files:
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /sys/firmware/efi/efivars/ [/COLOR]
cat: /sys/firmware/efi/efivars/: Is a directory
[/FONT]
```

Note sure if they moved efivars, but error has been around for a while.

---

### Post by aeronutt on 2024-05-25
Is there a way to hide a partition or device(disk) from boot-repair while it's doing its thing?

---

### Post by oldfred on 2024-05-25
Not that I know about.

You can always use the manual methods to repair, update or totally reinstall grub.  You only have to have essential system partition(s) mounted, ESP, / (root) and if separate partition /home. A few, mostly with servers, may have other system folders as partitions that normally have to be mounted.

If you can boot, you can do those from within your install.
If you have to use live installer, you can chroot into your install.

Some combination of these is an example of chroot, depending on your configuration compared to examples:
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)

---

### Post by aeronutt on 2024-05-26
I guess I'll learn how to install manually, not a bad thing to know.
I've put in a bug report to boot-repair.

I'm writing a script to record /dev nvme assignments after login, just for the fun of it.

Thanks again for the great responses and help.

---

