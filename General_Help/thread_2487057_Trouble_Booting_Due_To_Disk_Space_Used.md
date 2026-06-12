---
title: "Trouble Booting Due To Disk Space Used"
date: 2023-05-21
forum: General Help
---

### Post by shane_faulkinbury2 on 2023-05-21
I have a computer with 2 HDD's.  A Seagate 2 TB HDD and a Kingston 500 GB HDD.  The 2 TB HDD has Windows 10 and Ubuntu 20.4.02 loaded on it.  I have it partitioned for 1.5 TB for Ubuntu and 500 GB for Windows.  It was running fine and I was able to boot into both OS's normally.  A couple of days ago I got a Disk Management warning that I was low on disk space when booting into Ubuntu.  I sort of overlooked because I was positive I had enough disk space.

This afternoon I ran Boot Repair on a flash drive.  After trying to repair GRUB to boot into I got the attached error.  I cannot locate the Windows partition or see my other attached HDD.  Do you know where to locate it in Files or can I just load another flash drive and move file to it to make the partition smaller?

The Boot Repair file is at:  [HTML]http//paste.ubuntu.com/p/yw59f6QXZz/[/HTML]

---

### Post by MAFoElffen on 2023-05-22
You transcript the link wrong. Got the 'correct' URL off the attached screenshot.

Boot-repair resinstalled Grub to /dev/sdb2, which is not your primary EFI partition.
```

using the following options:  sdb2/boot/efi

```
Line 64: /dev/sdb3 is 100 % full...
/dev/sdb3 is your /boot/partition.

/dev/sda1 is the primary EFI partiton for both Windows and Ubuntu.

/dev/sdb2 is an EFI directory that just has Ubuntu(?) and seems secondary to Windows.

/dev/sdc is your root partition.

If you mounted the system and chrooted into it, 
```

sudo mount /dev/sdbX /mnt
sudo mount /dev/sdb3 /mnt/boot/
sudo mount /dev/sda1 /mnt/boot/efi/
cd /mnt
sudo chroot /mnt
mount -a

```
If you then did the following, I am fairly sure that you will see that many version of kernel boot files... 
```

ls -l /boot
df -h /boot

```
Which need to be cleaned up, as a first choice method, via 
[code]
apt autoremove, wiht should uninstall all but the last three version of Linux kernel.

If, for some reason, it doesn't make enough room, tell us and I will give you alternative methods.

---

### Post by MAFoElffen on 2023-05-22
<My last post would not let me edit the errors.>

Bottom part of the post should have been:
Which needs to be cleaned up, as a first choice method, via
```

apt autoremove, 

```
which should uninstall all but the last three versions of Linux kernel.

Boot-Repair misinterpreting that, and reinstalling Grub to /dev/sdb2 is not a reflection of the script, which cannot foretell all possibilities that can arise, especially on a dual-boot machine, and where there is mulitple choices for UEFI partitions. 

That is why, on this Forum we recommend that Users run the 'boot-info' report part of that, and post the URL of the uploaded report, before trying to go ahead and make the repair. That way we can confirm that the "plan" is correct for what is there.

---

### Post by shane_faulkinbury2 on 2023-05-22
First I did 'Create a BootInfo summary'.  After completed it said to find upload it to here - [HTML]http://paste.ubuntu.com/p/v5jNDjNG9F/[/HTML]

I then tried to run a one click repair and it of course said it repaired sd3, but that it was full and may not boot and I might get a Disk Manger error.  It of course didn't boot.

How do I get Boot Repair to repair SBD2?

---

### Post by #&amp;thj^% on 2023-05-22
> **shane_faulkinbury2 said:**
> First I did 'Create a BootInfo summary'.  After completed it said to find upload it to here - [HTML]http://paste.ubuntu.com/p/v5jNDjNG9F/[/HTML]

I then tried to run a one click repair and it of course said it repaired sd3, but that it was full and may not boot and I might get a Disk Manger error.  It of course didn't boot.

It would help if the right URL is correct: 
> 
The Paste you are looking for does not currently exist.
Return to the Pastebin


---

### Post by zebra2 on 2023-05-22
It wouldn't hurt to check /var/log on that Ubuntu partition and see if you have a log file running riot. Auth.log is a common culprit.

---

### Post by oldfred on 2023-05-22
Boot-Repair is just that. It typically updates grub menu or reinstalls grub.
It does not houseclean full partitions, and may or may not try to run a fsck.

You show sda3 a NTFS partition only 3% full
But show sdb3 95% & actually then full.

Ubuntu installer defaults to ESP on first drive, usually sda. And you have grub's boot files there.
But you also have an ESP on sdb. That is also ok, but you have to have manually changed that.
Your fstab comments show original install to sda's ESP, but now have mount of ESP on sdb. That is ok if that is what you want.

But issue is really full / (root) partition.

---

### Post by shane_faulkinbury2 on 2023-05-22
Do I have to upload it myself and if so how do I do it?  Also, it is trying to repair sbd3.  How do I have it repair sbd2?  Sorry, but I have never used Boot Repair and the instructions are vague.

Also, as you can see I'm on my second partition, Windows as we speak.  Is there anyway to get to the Ubuntu partition through Windows?

---

### Post by zebra2 on 2023-05-22
My suggestion is to download a copy of puppy linux and install it to a bootable USB using Rufus in Windows.  Puppy linux will  allow you to access the Ubuntu root partition and check your log files.  If you have a oversized log it will be obvious.  Needless to say you will have to fix the offending log if that is the problem.  But you need to get the boot fixed first. 

This link will get you to the focal64 iso download  ([https://distro.ibiblio.org/puppylinux/puppy-fossa/fossapup64-9.5.iso](https://distro.ibiblio.org/puppylinux/puppy-fossa/fossapup64-9.5.iso))

---

### Post by MAFoElffen on 2023-05-22
Here is the URL to the OP's 'boot-info' report:
```

https://pastebin.ubuntu.com/p/GytwcPqw9t/

```

@zebra2 -- I am biting my tongue. True, but you can see a log file from any bootable Distro media, including what is approved "here" in this Forum, from the Ubuntu Installer LiveUSB... But /dev/sdb, which is full, is his /boot partition, which does not contain the /var folder (which /var/log contains log files). That does happen in this realm as a problem for other users, but is not remotely what is going on here.

I am sorry that you are embarrassing yourself here. I am trying to be patient and kind. Think about what you post, and the solutions you recommend. I want you to learn and be an asset here, to be able to help others with your experience. I really, sincerely do. If you want a mentor with that, or if you disagree, feel free to PM me about that.

@oldfred -- A while back, you shared the file location (with me via PM) where Grub2 stores where it keeps track of where it was originally installed within that OS instance. I don't have that info handy (I had to clean out my inbox). If it is installed later via a different source, it doesn't update that file in that OS instance. 

It looks like originally, Ubuntu might have been installed, and the installer originally created another ESP folder at /dev/sdb2, which was updated later... the 'boot-repair' script uses that default 'installed directory' from that file in that OS instance, to reinstall Grub2, right oldfred? I think you were the one who first told me about that, right? (When we were going through the script... It was when we were helping that user from French Polynesia with the locked-down UEFI BIOS on his off-brand Chinese made Mini PC...)

I'm trying to remember where i put that information. That was during the Pandemic...

---

### Post by oldfred on 2023-05-22
UEFI boot entry uses GUID to know the ESP - efi system partition.
Then in the ESP, is a three line grub.cfg that uses UUID of the install to find full grub.cfg. If separate /boot, I believe it would be the UUID of that.
Installs since about 14.04 have locked the ESP with umask=0077, before they used defaults. I believe this was for security reasons as ESP was then writable and not very secure. Boot-Repair still changes it to defaults.

If correct UUID for desired or only ESP is in fstab, you can reinstall grub
sudo grub-install

If system does not boot, most new users will find just using Boot-Repair easier. 
But you can follow GUID/partUUID to ESP, grub.cfg & its UUID in fstab and make sure those entries are correct. That is how I review Boot-Repair's summary report to see if grub installed correctly. Often incorrect UUID or reformatted ESP with wrong GUID/partUUID.

---

### Post by shane_faulkinbury2 on 2023-05-22
Okay, I deleted everything off of the Kingston HDD and booted Boot Repair again.  I deleted the downloads and pictures folder which had a lot in them which should have made a good deal of space.  Booted into Ubuntu again and it still will not boot.  I ran a scan again and this is the pastebin.  -  [HTML]http://paste.ubuntu.com/p/BjZy5sT8M8/[/HTML]

---

### Post by oldfred on 2023-05-22
You still are at 95%. See line 214:
> /dev/sdb3        0  95% /mnt/boot-sav/sdb3

Are you deleting from sdb3 or really is data in your NTFS partitions?
Did you empty trash also?

I like to use ncdu as a bit easier than standard du to see where data really is. You have to install it, but du is part of system.

Can you boot to grub menu? And then recovery mode?

---

### Post by shane_faulkinbury2 on 2023-05-22
Guys, if both OS's are on the same hard drive, surely there is another way on?  I can just write the OS again, but I want to get my Video folder that has about 200 GB in it.  I go into the Video folder on Boot Rescue and there are no files listed.  Can I just copy the folder onto a flash drive?

No, I just deleted the entire D drive on Windows.

---

### Post by MAFoElffen on 2023-05-23
Wow. What a waste of time and information gone, that had nothing to do with your problem and was not related. The Windows NTFS files you deleted, where not causing you to be out of space in your Ubuntu /boot partition, which is formatted as ext4... Which Windows cannot even see, nor mount. Dang.

Please stop and listen, until you fully understand what is going on... "before" you attempt to do anything else... Before you accidentally make a change that causes you to have to do complete reinstall, instead of just a simple (maintenance type) of repair.

(This could have been so simple...)

Let me draw you a picture with a description, so you can visualize the problem , and understand what needs to happen.
```

The / root filesystem = /dev/sdb5 partition...
The /boot partition, which is /dev/sdb3 is mounted into the root filesystem  at directory stub /boot... This partition is out of space (more on that below.)
The ESP / EFI partition is formatted as FAT32 and is mounted into the filesystem at /boot/efi...

```
/dev/sdb3 is out of space. That happens when, during the original install process, it created a boot psrtition of a fixed size, and during subsequent updates of Linux Kernel versions, it kept adding kernel boot images, without removing the old ones that were no longer used... After a while, if you do not run some maintance task kinds of commands, that partition will fill up, and be full. Usually that haapens during another update, and getting an error saying that it was out of space. (like the error you got.)

The maintenance kind of task I describes of doing, is too pay attention to the update prosess, and look for items that say something like "these packages were installed and are no longer needed. please run 'sudo apt autoremove' to remove them. usually that will also remove all but the last three version of the kernel, and the old boot images from your /boot partition. You will see many threads on this forum where this has happened.

Sometimes the user needs to manually uninstall the old kernel packages to make space. Those include
```

apt list linux-* --installed

```
...to identify the Linux Kernel packages that are installed, and to determine, what is old and can be removed. To do that you need to e chrooted into your compromised system to be able to remove those safely. You can't even see the installed packages from that command until you are chrooted into your system.

Please boot from an Ubuntu LiveUSB installer media and do
```

sudo lsblk -o name,mountpoint,fssize,fsused,fsuse%,fstype -e7

```
From that, that will help us, and you to determine, to help explain this and how to correct it.

To get a quick list of the old images in that partition, while booted from the LiveUSB, temporarily  mounnt that partition... In the file manager, right-click on that area  and select open terminal (there), then do
```

ls -lah ./

```
If you can at least do this last part, and post the results within CODE Tags, there is a short-cut type of work-around that I will share with you to open some space up quickly, without you having to chroot into the installed system.

---

### Post by shane_faulkinbury2 on 2023-05-23
Do I do all of this in Boot Repair.   I'm asking because I cannot boot into Ubuntu, only Windows 10.

---

### Post by oldfred on 2023-05-23
Are you using Boot-Repair ISO or adding Boot-Repair to your Ubuntu live installer?
Better to use live installer, but you can use Boot-Repair's ISO.

General rule is Windows tools for Windows & Linux tools for Linux. Windows does not see Linux partitions.
And often best to use same version live installer as your install, unless old obsolete install.

---

### Post by MAFoElffen on 2023-05-23
You can do it booted from the Boot Repair disk... by using the Live Environment there and opening up a Terminal session and a browser, inside of that environment...

That way you can visit the forum from a browser and cut and paste the commands between the browser and the terminal session... Then paste the output into a post, wrapped inside of CODE Tags... Like this:
[noparse]```

Paste your code here

```[/noparse]
Does that make sense now?

Or you could boot from an Ubuntu Desktop Install LiveUSB... Just so you are booted from some type of Linux "Live Image Environment"... That way you can see your system through Linux kind of eyes, as Linux see's your system.

You can repair your system that way, booted from one of those types of disks... 

When I was doing Onsite Service for companies, (and for my own business), an Ubuntu Install LiveUSB (and a Windows Install USB media) was one of my goto tools, even for repairing Windows Systems.

---

### Post by shane_faulkinbury2 on 2023-05-23
Are you talking about the Live Installer from ESET?

---

### Post by MAFoElffen on 2023-05-23
This is how the 'boot-info', and 'boot-repair' scripts work on that disk... They run on top of a Live Image environment... Looks at your system, from a Linux point of view. chroot's into the installed system to make repairs.

What is wrong with your system, why it fails, is outside of the function and capabilities of what those scripts do... But we might have to make changes to the installed system to make repairs... So manually from inside that Live Image Environment.

It is not as scary as that might sound. I will give you instructions on what to do, and lead you through it.

---

### Post by MAFoElffen on 2023-05-23
> **shane_faulkinbury2 said:**
> Are you talking about the Live Installer from ESET?
ESET? What is ESET?

---

### Post by shane_faulkinbury2 on 2023-05-23
All I need to do is to boot into where you all are telling me to make these changes.  Do I put something on a flash drive and boot onto it?  If so, what exactly do I put on it?  I assume I can talk to you from that environment or should I just use my mobile?

---

### Post by MAFoElffen on 2023-05-23
Okay... LOL.

Create an Ubuntu 22.04 (installer) LiveUSB on a flash drive. Boot from it. After it boots, select "Try"... You will be using that to run your computer while you do all this. (You can't make repairs to Linux from Windows.)

Open up Firefox and go to this thread... That way you can use the instructions here, and be able to post back any feedback or questions you have, while still in that "Live Environment". That is just a term that says it is not an installed, persistent kind of environment...

Tell me when you have done that, from Firefox, booted from that media...

---

### Post by shane_faulkinbury2 on 2023-05-23
Okay, on Boot Repair and in Firefox.

```
total 12Kdrwxr-xr-x 1 lubuntu lubuntu  360 May 23 17:56 .
drwxr-xr-x 1 root    root      60 Jun 12  2020 ..
-rw------- 1 lubuntu lubuntu   52 May 23 13:35 .Xauthority
drwxrwxr-x 8 lubuntu lubuntu  160 May 23 17:41 .cache
drwxr-xr-x 1 lubuntu lubuntu  380 May 23 17:54 .config
drwx------ 3 lubuntu lubuntu   60 May 23 13:35 .gnupg
drwxr-xr-x 3 lubuntu lubuntu   60 May 23 13:35 .local
-rw-r--r-- 1 lubuntu lubuntu    0 May 23 17:56 .sudo_as_admin_successful
-rw-r--r-- 1 lubuntu lubuntu   14 Jul 25  2019 .xscreensaver
-rw------- 1 lubuntu lubuntu 2.3K May 23 13:35 .xsession-errors
drwxr-xr-x 2 lubuntu lubuntu   40 May 23 13:35 Desktop
drwxr-xr-x 2 lubuntu lubuntu   40 May 23 13:35 Documents
drwxr-xr-x 2 lubuntu lubuntu   40 May 23 13:35 Downloads
drwxr-xr-x 2 lubuntu lubuntu   40 May 23 13:35 Music
drwxr-xr-x 2 lubuntu lubuntu   40 May 23 13:35 Pictures
drwxr-xr-x 2 lubuntu lubuntu   40 May 23 13:35 Public
drwxr-xr-x 2 lubuntu lubuntu   40 May 23 13:35 Templates
drwxr-xr-x 2 lubuntu lubuntu   40 May 23 13:35 Videos



```

Okay, no time to wait.  I'll create a 32 GB flash drive with Ubuntu installed and boot into "try".  It'll have to be this evening though.

---

### Post by psychohermit on 2023-05-23
From a live session, clean up /var/log.  Fire up gparted and take some disk space from a partition that can afford it and give it to your root partition.  Linux likes to have at least 20% free disk space.  Once you can boot normally apt autoremove old kernels.

--glenn

---

### Post by MAFoElffen on 2023-05-23
@psychohermit -- That would work for most users, when they have a root partition that is full. But, his root partition is not the partition that is full, so that won't work for him. He has a boot partition which is full. It crashed on rebuilding the intramsfs images while reinstalling grub, because there was not enough room left there to do that...

So he must make room in that partition, then rebuild the initramfs image to be able to boot. Once he has enough room to be able to boot, or if he can chroot into the installed, then he can remove old kernels. It's a chicken before the egg affair.

---

### Post by shane_faulkinbury2 on 2023-05-23
On Ubuntu Live.

```
sda                                                        
&#9500;&#9472;sda1                                                     vfat
&#9500;&#9472;sda2                                                     
&#9500;&#9472;sda3 /media/ubuntu/503ACC3A3ACC1F3A   1.8T  68.9G     4% ntfs
&#9492;&#9472;sda4                                                     ntfs
sdb                                                        
&#9500;&#9472;sdb1 /media/ubuntu/D                113.9G  94.2M     0% ntfs
&#9500;&#9472;sdb2                                                     vfat
&#9492;&#9472;sdb3                                                     ext4
sdc                                                        
&#9492;&#9472;sdc1 /cdrom                          28.9G   4.6G    16% vfat
sr0                                                        

```

```
ls -lah ./
total 12K
drwxr-x--- 14 ubuntu ubuntu  360 May 23 18:41 .
drwxr-xr-x  1 root   root     60 May 23 14:38 ..
-rw-r--r--  1 ubuntu ubuntu  220 May 23 14:38 .bash_logout
-rw-r--r--  1 ubuntu ubuntu 3.7K May 23 14:38 .bashrc
drwx------ 12 ubuntu ubuntu  260 May 23 19:15 .cache
drwxr-xr-x 13 ubuntu ubuntu  360 May 23 19:15 .config
drwxr-xr-x  2 ubuntu ubuntu   60 May 23 14:38 Desktop
drwxr-xr-x  2 ubuntu ubuntu   40 May 23 18:41 Documents
drwxr-xr-x  2 ubuntu ubuntu   40 May 23 18:41 Downloads
drwx------  3 ubuntu ubuntu   60 May 23 14:38 .local
drwxr-xr-x  2 ubuntu ubuntu   40 May 23 18:41 Music
drwxr-xr-x  2 ubuntu ubuntu   40 May 23 18:41 Pictures
-rw-r--r--  1 ubuntu ubuntu  807 May 23 14:38 .profile
drwxr-xr-x  2 ubuntu ubuntu   40 May 23 18:41 Public
drwx------  4 ubuntu ubuntu   80 May 23 18:41 snap
-rw-r--r--  1 ubuntu ubuntu    0 May 23 14:38 .sudo_as_admin_successful
drwxr-xr-x  2 ubuntu ubuntu   40 May 23 18:41 Templates
drwxr-xr-x  2 ubuntu ubuntu   40 May 23 18:41 Videos

```

I assume I can remove sbd?  Not that it matters since it's only 92.4M.

---

### Post by MAFoElffen on 2023-05-23
Open the file manager > Other Locations... Look at /dev/sdb3... It should automount and appear as mounted in the left file manager panel...

In the terminal session do:
```

sudo lsblk -o name,size,fssize,fsused,fsuse%,mountpoint | grep -v 'loop'

```
Then post it so I can see where it mounted within /media

Sorry about the delay. I just released an update to the UbuntuForums 'system-info' Script today, so I had to concentrate on getting that out to the repo's. Tomorrow I will update the PPA for it.

---

### Post by shane_faulkinbury2 on 2023-05-23
```
sudo lsblk -o name,size,fssize,fsused,fsuse% | grep -v 'loop'
NAME     SIZE FSSIZE FSUSED FSUSE%
sda      1.8T               
&#9500;&#9472;sda1   100M               
&#9500;&#9472;sda2    16M               
&#9500;&#9472;sda3   1.8T   1.8T  68.9G     4%
&#9492;&#9472;sda4   530M               
sdb    223.6G               
&#9500;&#9472;sdb1 113.9G 113.9G  94.2M     0%
&#9500;&#9472;sdb2   513M               
&#9492;&#9472;sdb3   109G               
sdc     28.9G               
&#9492;&#9472;sdc1  28.9G  28.9G   4.6G    16%
sr0     1024M               

```

---

### Post by MAFoElffen on 2023-05-23
Let's tweak that query a bit to show more info...
```

sudo lsblk -o name,size,fstype,pttype,fsuse%,mountpoint | grep -v 'loop'

```

---

### Post by shane_faulkinbury2 on 2023-05-23
```
sudo lsblk -o name,size,fstype,ptype,fsuse%,mountpoint | grep -v 'loop'
```

---

### Post by MAFoElffen on 2023-05-23
Editted my last post to this:
```

sudo lsblk -o name,size,fstype,pttype,fsuse%,mountpoint | grep -v 'loop'
```
Sorry. Typo (left out a "t")...

Also do
```

sudo fdisk -l | grep '^/dev/' | grep -v 'loop'

```

---

### Post by shane_faulkinbury2 on 2023-05-23
```
sudo fdisk -l | grep '^/dev/\|Device' | grep -v 'loop'
Device          Start        End    Sectors  Size Type
/dev/sda1        2048     206847     204800  100M EFI System
/dev/sda2      206848     239615      32768   16M Microsoft reserved
/dev/sda3      239616 3905940558 3905700943  1.8T Microsoft basic data
/dev/sda4  3905941504 3907026943    1085440  530M Windows recovery environment
Device         Start       End   Sectors   Size Type
/dev/sdb1     239616 239144598 238904983 113.9G Microsoft basic data
/dev/sdb2  239144960 240195583   1050624   513M EFI System
/dev/sdb3  240195584 468860927 228665344   109G Linux filesystem
Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 60620799 60618752 28.9G  c W95 FAT32 (LBA)

```

---

### Post by MAFoElffen on 2023-05-23
Now do 
```

sudo fsck -p /dev/sdb3

```
And then rerun
```

sudo lsblk -o name,size,fstype,pttype,fsuse%,mountpoint /dev/sdb

```

EDIT: Taking a while?

---

### Post by shane_faulkinbury2 on 2023-05-23
```
[NAME     SIZE FSTYPE PTTYPE FSUSE% MOUNTPOINT
sdb    223.6G        gpt           
&#9500;&#9472;sdb1 113.9G ntfs   gpt        0% /media/ubuntu/D
&#9500;&#9472;sdb2   513M vfat   gpt           
&#9492;&#9472;sdb3   109G ext4   gpt      
```

---

### Post by MAFoElffen on 2023-05-23
So you didn't (in the file manager) go to "+ Other Locations" > 109GB Volume (/dev/sdb3)... and double click on it, so that it could automount to the /media folder. Please do that and run the command again so we can see how it mounts under /media...

See where it did that with /dev/sdb1? (as /media/ubuntu/D) That is where I can see that you have selected that NTFS partiton and looked at that already... It is still mounted. You need to mount /dev/sdb3.

---

### Post by shane_faulkinbury2 on 2023-05-23
I don't have a 109  GB volume.  Just a 8.3 GB, a 2.0 TB, 122.3 GB and a 117 GB.

---

### Post by MAFoElffen on 2023-05-23
> **shane_faulkinbury2 said:**
> I don't have a 109  GB volume.  Just a 8.3 GB, a 2.0 TB, 122.3 GB and a 117 GB.

```

NAME SIZE FSTYPE PTTYPE FSUSE% MOUNTPOINT
sdb 223.6G gpt
&#9500;&#9472;sdb1 113.9G ntfs gpt 0% /media/ubuntu/D
&#9500;&#9472;sdb2 513M vfat gpt
[COLOR=#ff0000]&#9492;&#9472;sdb3 **109G** ext4 gpt[/COLOR] 

```
That partition in Red above, will show similar to the attachment, with the instructions I described to you, named as "109GB Volume"...

---

### Post by shane_faulkinbury2 on 2023-05-23
```
sudo fsck -p /dev/sdb3
fsck from util-linux 2.37.2
/dev/sdb3 is mounted.
e2fsck: Cannot continue, aborting.


ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59$ sudo lsblk -o name,size,fstype,pttype,fsuse%,mountpoint /dev/sdb
NAME     SIZE FSTYPE PTTYPE FSUSE% MOUNTPOINT
sdb    223.6G        gpt           
&#9500;&#9472;sdb1 113.9G ntfs   gpt        0% /media/ubuntu/D
&#9500;&#9472;sdb2   513M vfat   gpt           
&#9492;&#9472;sdb3   109G ext4   gpt       95% /media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb8

```

---

### Post by MAFoElffen on 2023-05-23
There you go. Thank you. Now...
```

df -h /media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb8
ls /media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb8

```

---

### Post by shane_faulkinbury2 on 2023-05-23
```
ls /media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb8
ls: cannot access '/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb8': No such file or directory

```

---

### Post by MAFoElffen on 2023-05-23
Can you look at in your file manager and take a screen shot of it to "attach" to a post?

If so, if it has folders such as boot, etc, var... Then take a screenshot of boot. Then go back, open var > open log... Take another screenshot.

---

### Post by shane_faulkinbury2 on 2023-05-23
Here is a screenshot of log -

I forgot to add the screenshot of log and now I can't upload it.  I logged out of the forum and back in  and get the same thing.

Finally!

---

### Post by deadflowr on 2023-05-23
> **MAFoElffen said:**
> There you go. Thank you. Now...
```

df -h /media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb8
ls /media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb8

```

> **shane_faulkinbury2 said:**
> ```
ls /media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb8
ls: cannot access '/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb8': No such file or directory

```

Maybe a moot point, but the output from post #46 shows the working directory is the correct UUID, but the output from the lsblk command is cut off.

---

### Post by MAFoElffen on 2023-05-23
What about the boot folder? Waiting on that...

In the meanwhile-- Remove / Delete files:
apport.log.3.gz
apport.log.4.gz
apport.log.5.gz
apport.log.6.gz
apport.log.7.gz
auth.log.3.gz
auth.log.4.gz
dmesg.log.3.gz
dmesg.log.4.gz
kern.log.3.gz
kern.log.4.gz
syslog.3.gz
syslog.4.gz

---

### Post by oldfred on 2023-05-23
While log files do eventually get removed, I am using system every day, so logs grow. If not using a lot then you may not want to do this:
I regularly run a houseclean script that included this (script does not have sudo as entire script is run with sudo):

> sudo find /var/log/ -name *.gz* -type f -atime +10 -print -exec rm -f {} +
#  /var/backups  Normally 7 backups kept

First time to get I just ran this to make sure of what I was deleting.
> sudo find /var/log/ -name *.gz* -type f -atime +10 -print 

The +10 is ten days, so I do keep some log files, but if no issues, I see no reason for keeping many. 
And if major issues, I would just reinstall & restore from backups, anyway.

---

### Post by shane_faulkinbury2 on 2023-05-23
I tied removing those files and I'll show you the first a couple of them.
```
rm apport.log.3.gz
rm: cannot remove 'apport.log.3.gz': No such file or directory

```
```
rm kerne.log.4.gz
rm: cannot remove 'kerne.log.4.gz': No such file or directory
```

---

### Post by MAFoElffen on 2023-05-24
The terminal session you had open was not navigated to the right folder. That is why it couldn't find it. (And I had a typo. The kerne.log.4.gz should have been kern.log.4.gz)

To make this simpler:
In the file manager-- If you back out to /var on that mount in the file manager, then right click back on the highlighted "log" folder > Select "Open In Terminal"... That will open a terminal session in the correct folder, so that you could remove them with those commands (without adding the full mounted path).

Like this:
```

sudo rm ./apport.log.[3-7].gz
sudo rm ./auth.log.[3-4].gz
sudo rm ./dmesg.log.[3-4].gz
sudo rm ./kern.log.[3-4].gz
sudo rm ./syslog.[3-4].gz

```

---

### Post by MAFoElffen on 2023-05-24
From there, if you then did
```

cd ../../boot
ls -l ./

```
That should move you to the mounted, installed boot directory and show you what is there.

---

### Post by shane_faulkinbury2 on 2023-05-24
```
sudo rm ./apport.log.[3-7].gz
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59/var/log$ sudo rm ./auth.log.[3-4].gz
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59/var/log$ sudo rm ./dmesg.log.[3-4].gz
rm: cannot remove './dmesg.log.[3-4].gz': No such file or directory
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59/var/log$ sudo rm ./kern.log.[3-4].gz
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59/var/log$ sudo rm ./syslog.[3-4].gz
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59/var/log$ cd ../../boot
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59/boot$ ls -l ./
total 180176
-rw-r--r-- 1 root root   270035 Mar 31 15:02 config-5.19.0-40-generic
-rw-r--r-- 1 root root   270012 Apr 18 15:38 config-5.19.0-41-generic
drwxrwxr-x 2 root root     4096 Apr 21 02:41 efi
drwxr-xr-x 5 root root     4096 May 22 15:43 grub
lrwxrwxrwx 1 root root       28 Apr 26 13:04 initrd.img -> initrd.img-5.19.0-41-generic
-rw-r--r-- 1 root root 73096532 May 15 14:47 initrd.img-5.19.0-40-generic
-rw-r--r-- 1 root root 73024556 May 15 14:47 initrd.img-5.19.0-41-generic
lrwxrwxrwx 1 root root       28 Apr 26 13:04 initrd.img.old -> initrd.img-5.19.0-40-generic
-rw-r--r-- 1 root root   182800 Feb  6  2022 memtest86+.bin
-rw-r--r-- 1 root root   184476 Feb  6  2022 memtest86+.elf
-rw-r--r-- 1 root root   184980 Feb  6  2022 memtest86+_multiboot.bin
-rw------- 1 root root  6434470 Mar 31 15:02 System.map-5.19.0-40-generic
-rw------- 1 root root  6434470 Apr 18 15:38 System.map-5.19.0-41-generic
lrwxrwxrwx 1 root root       25 Apr 26 13:04 vmlinuz -> vmlinuz-5.19.0-41-generic
-rw------- 1 root root 12197320 Mar 31 15:03 vmlinuz-5.19.0-40-generic
-rw------- 1 root root 12196552 Apr 18 15:26 vmlinuz-5.19.0-41-generic
lrwxrwxrwx 1 root root       25 Apr 26 13:04 vmlinuz.old -> vmlinuz-5.19.0-40-ge
```

Sorry it took me so long, but sleep and morning stuff.

---

### Post by shane_faulkinbury2 on 2023-05-24
Should I remove these?

```
-rw-r--r-- 1 root root 73096532 May 15 14:47 initrd.img-5.19.0-40-generic
-rw-r--r-- 1 root root 73024556 May 15 14:47 initrd.img-5.19.0-41-generic
-rw------- 1 root root  6434470 Mar 31 15:02 System.map-5.19.0-40-generic
-rw------- 1 root root  6434470 Apr 18 15:38 System.map-5.19.0-41-generic


```

---

### Post by MAFoElffen on 2023-05-24
No! You only have two version of kernel there. You are fine there. 

Now do
```

cd ..
df -h ./

```

---

### Post by shane_faulkinbury2 on 2023-05-24
Okay, after I do that just reboot and I'll be able to log in?  Just wonder if I have to any additional steps to log on?

I don't think I have enough space?

```
$ cd ..
ubuntu@ubuntu:/var$ df -h ./
Filesystem      Size  Used Avail Use% Mounted on
/cow            7.8G  227M  7.6G   3% /

```

---

### Post by MAFoElffen on 2023-05-25
In the file manager, open that 117GB Volume (that /dev/sdb3 partition), when it comes up in the windows of the file manager, right click anywhere in the panel where there is not any file icons > Select Properties. Look to see how much space it says you have free...

---

### Post by oldfred on 2023-05-25
/cow is copy on write or your live installer, not your install.

---

### Post by shane_faulkinbury2 on 2023-05-25
Here you go.

---

### Post by MAFoElffen on 2023-05-25
??? It says it is still completely full?

Lets approach this a little differently. In nautilus, in the left-hand panel, eject all the mounted volumes.

In the terminal:
```

sudo umount /media/*  # <-- Just in case anything is still mounted there
sudo mount /dev/sdb3 /mnt #<-- Added the mountpoint
sudo mount --bind /sys/ /mnt/sys #<-- Corrected the path
sudo mount --bind /proc /mnt/proc
sudo mount --bind /run /mnt/run
sudo chroot /mnt
mount -a
df -h /

```

---

### Post by shane_faulkinbury2 on 2023-05-25
Cool, rebooting!

```
sudo umount /media/*
umount: /media/cdrom: target is busy.
umount: /media/ubuntu: not mounted.
ubuntu@ubuntu:~$ sudo mount /dev/sdb3
mount: /dev/sdb3: can't find in /etc/fstab.
ubuntu@ubuntu:~$ sudo mount -bind /sys/ ./mnt/sys
mount: invalid option -- 'b'
Try 'mount --help' for more information.
ubuntu@ubuntu:~$ sudo mount -bind /proc /mnt/proc
mount: invalid option -- 'b'
Try 'mount --help' for more information.
ubuntu@ubuntu:~$ sudo mount -bind /run /mnt/run
mount: invalid option -- 'b'
Try 'mount --help' for more information.
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: failed to run command ‘/bin/bash’: No such file or directory
ubuntu@ubuntu:~$ mount -a
ubuntu@ubuntu:~$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/cow            7.8G  197M  7.6G   3% /

```

Ubununtu still won't boot.

---

### Post by MAFoElffen on 2023-05-25
Somehow you added a dot, "." in front of /mnt... (my typo, sorry) Do that over without the dot. (I edited that post, #67) The folder /mnt is from the root of the system...

You are doing that from a terminal session, booted from the LiveUSB...

---

### Post by MAFoElffen on 2023-05-25
I have a short window here. I have 2 hours before I have to go to work...

---

### Post by deadflowr on 2023-05-25
mount binds needs a double dash like
```
 mount --bind /sys /mnt/sys
```

---

### Post by MAFoElffen on 2023-05-25
> **deadflowr said:**
> mount binds needs a double dash like
```
 mount --bind /sys /mnt/sys
```
Thank you for being another set of eyes. Have an hour before leaving for work. Was typing in a hurry.

Corrected the code in the post for the chroot...

---

### Post by MAFoElffen on 2023-05-25
Have to leave for work. Will check this again later.

---

### Post by shane_faulkinbury2 on 2023-05-25
mount --bind /sys /mnt/sys
mount: /mnt/sys: mount point does not exist.

```
mount --bind /sys /mnt/sys
mount: /mnt/sys: mount point does not exist.

```

Sorry

---

### Post by deadflowr on 2023-05-25
I think the assumption here is that you re-run the commands MAFoElffen posted in post #67.
I'm also thinking you misread them, which is easy to understand so I'll re-post them without the additional comments:
Run these commands

```
sudo umount /media/*  

sudo mount /dev/sdb3 /mnt  

sudo mount --bind /sys/ /mnt/sys 

sudo mount --bind /proc /mnt/proc

sudo mount --bind /run /mnt/run

sudo chroot /mnt

mount -a

df -h /
```

I double spaced them out so you can see exactly what each individual command he wants are.

---

### Post by shane_faulkinbury2 on 2023-05-25
Okay, rebooting and will give it a go in that order.  Afterwards, do I just reboot and it'll show Ubuntu and Windows and I'll finally be able to boot into Ubuntu?

I think there was a problem with chroot.

```
root@ubuntu:/# mount -a
mount: /boot/efi: can't find UUID=7D2D-39F9.
root@ubuntu:/# mount -a
mount: /boot/efi: can't find UUID=7D2D-39F9.
```

---

### Post by deadflowr on 2023-05-25
Ah, yes.
I see it.
He forgot (And i did too) the mount bind for /dev

Assuming you are still in the chroot, I would exit the chroot and add one more mount like so

run
```
exit
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
```

Then retry the mount -a command again,

---

### Post by shane_faulkinbury2 on 2023-05-25
Heading to bed.  I'll try that in the morning.  Thank you

Ready to get this done.  Oh, darn.  I forgot to try the last thing you said OldFred!

I forgot to try the last thing you said deadflowr!

```
/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59/var/log$ sudo mount --bind /dev /mnt/dev
mount: /mnt/dev: mount point does not exist.
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59/var/log$ sudo chroot /mnt
chroot: failed to run command ‘/bin/bash’: No such file or directory

```

---

### Post by MAFoElffen on 2023-05-26
If it has an error, stop there... No sense in going on to get more errors.

I worked until 2am last night... But had to get up early for a doctors appointment.

If it could not find /mnt/dev, then that means that the root drive was no longer mounted at the /mnt directory. Please try again from the start...

```

sudo umount /media/*  

sudo unmount /mnt/*

sudo mount /dev/sdb3 /mnt  

sudo mount --bind /dev/ /mnt/dev

sudo mount --bind /sys/ /mnt/sys 

sudo mount --bind /proc /mnt/proc

sudo mount --bind /run /mnt/run

sudo chroot /mnt

mount -a

df -h /

```
And no, do not just reboot after that. We need to see the ouput of that command so we can figure out what is still taking up all your space, and how to get you some space to breath. 

You need about 20% free to finish reinstalling grub to be able to boot. That's where it failed, (way back when) right?

Take a breath. Please be patient. We are close though.

---

### Post by shane_faulkinbury2 on 2023-05-26
Cool, let me reboot to Ubuntu from Windows.

```
sudo mount /dev/sdb3 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev/ /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /sys/ /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /run /mnt/run
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# mount -a
root@ubuntu:/# df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb3       107G  102G     0 100% /
```

I imagine I just run a ```
grub-setup -d
```?

---

### Post by deadflowr on 2023-05-26
Not sure how helpful it might be, or what others might think to do at this stage but I think you should  run du to see where space is getting eaten.
try
```
du --exclude=/sys --exclude=/proc --exclude=/dev  --exclude=/snap --max-depth=1 --human-readable / | sort -n
```
Note that I excluded several directories which are actually virtual file systems and won't do anything but clog up the output.
Depending on how good the system is it might take a few seconds or a few minutes to run.

You still have a very full system, so I do not think running something like grub-setup (or whatever)  would be helpful until you can figure out where to clean up some more space,
if possible.
Without setting up some breathing room, you're looking at just doing all this again, eventually.

---

### Post by shane_faulkinbury2 on 2023-05-26
```
du --exclude=/sys --exclude=/proc --exclude=/dev  --exclude=/snap --max-depth=1 --human-readable / | sort -n
2.1M    /run
3.6M    /root
4.0K    /cdrom
4.0K    /mnt
4.0K    /srv
6.2G    /usr
7.5G    /.Trash-0
8.0K    /media
16K    /lost+found
16M    /etc
18G    /var
51M    /opt
60K    /tmp
69G    /home
102G    /
191M    /boot

```

---

### Post by yancek on 2023-05-26
You have 18GB in /var, much of which is probably log files which you can delete.  The location of these files is conveniently in /var/log.  Need to be root (use sudo to delete).

Most of what you have is in your /home directory so you might move some of that to an external device if it is something like, movies, pictures, music or other personal data.  Either that or get a bigger drive for your install.

---

### Post by shane_faulkinbury2 on 2023-05-26
Okay, switching back to Windows.

---

### Post by shane_faulkinbury2 on 2023-05-26
Any more suggestions or is everyone out partying?

I think it has something to do with virtual memory because I have like 2.5 TB total.

---

### Post by MAFoElffen on 2023-05-27
Why go back to "Windows" to try to delete those? Like I said before, Windows cannot read Linux EXT4 filesystems, so you cannot delete those from Windows.

oldfred had posted a command that deleted old log files older than 10 days... Please look back at that post and run that command. Then look back at my post on what to delete there.

Also, by your output, you have 7.5GB of Trash in your trash can that you can delete via
```

rm -rf .Trash-0/*.*
rm -rf /home/username/.local/share/Trash/*

```
...replacing username with your own User Name. You do not need to use sudo for those, as you would be chrooted into the installed filesystem as the root user.

If it where me doing that, i would look for about 22GB of things to delete (or move off there to another. or  external drive) from /.Trash-0/, /var/log/, and you user /home/username/ folders... That would give you about 20% free, to have enough room to reinstall Grub. It's not just room for that, but that process is going to rebuild the initramfs image files, which is where it failed, when it ran out of room.

---

### Post by shane_faulkinbury2 on 2023-05-27
[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547"), I understand the not doing anything from Windows which I have not done since the beginning.  I will try removing the trash.  Would what I showed for installing GRUB work or do you have another way of doing it?

---

### Post by shane_faulkinbury2 on 2023-05-27
```
sudo grub-install /dev/sda3
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
```

---

### Post by shane_faulkinbury2 on 2023-05-27
I'm not to clear on how to create an EFI directory?

---

### Post by oldfred on 2023-05-27
You never install grub to a partition like /dev/sda3.
You always install grub to a drive like /dev/sda.

Post this:
sudo fdisk -lu

And you should see something like this:
```

[FONT=monospace][COLOR=#000000]Number  Start   End     Size    File system  Name       Flags [/COLOR]
 1      1049kB  538MB   537MB   fat32        esp_nvme   boot, esp

[/FONT]
```

---

### Post by shane_faulkinbury2 on 2023-05-27
[**[COLOR=#C61919][B]deadflowr**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1276577") 	 
 						[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]

```
Disk /dev/loop0: 2.54 GiB, 2731876352 bytes, 5335696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 63.28 MiB, 66355200 bytes, 129600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 240.61 MiB, 252301312 bytes, 492776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 346.33 MiB, 363151360 bytes, 709280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 304 KiB, 311296 bytes, 608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 49.84 MiB, 52260864 bytes, 102072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000DM008-2FR1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 76172E7B-1A69-45F8-89E7-7E448878FE5B

Device          Start        End    Sectors  Size Type
/dev/sda1        2048     206847     204800  100M EFI System
/dev/sda2      206848     239615      32768   16M Microsoft reserved
/dev/sda3      239616 3905940558 3905700943  1.8T Microsoft basic data
/dev/sda4  3905941504 3907026943    1085440  530M Windows recovery environment


Disk /dev/sdb: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk model: KINGSTON SA400S3
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 61C453AC-05BE-44C4-A826-B0D2BF81CC50

Device         Start       End   Sectors   Size Type
/dev/sdb1     239616 239144598 238904983 113.9G Microsoft basic data
/dev/sdb2  239144960 240195583   1050624   513M EFI System
/dev/sdb3  240195584 468860927 228665344   109G Linux filesystem


Disk /dev/sdc: 28.91 GiB, 31037849600 bytes, 60620800 sectors
Disk model: USB Flash Drive 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00c46df3

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 60620799 60618752 28.9G  c W95 FAT32 (LBA)


Disk /dev/loop8: 45.93 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb
```

---

### Post by shane_faulkinbury2 on 2023-05-27
```
sudo grub-install /dev/sda
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.

```

---

### Post by MAFoElffen on 2023-05-27
*** Important: ***While chrooted into the "installed system"...***

Try this
```

ls /boot/efi ## If this has an error, then there is no sense in going on to anything else without posting back here first.. Understood?
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy

```

---

### Post by shane_faulkinbury2 on 2023-05-27
```
ls /boot/efi
ls: cannot access '/boot/efi': No such file or directory

```

```
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
grub-install: error: failed to get canonical path of `/boot/efi'.
```

---

### Post by MAFoElffen on 2023-05-27
I said: 
> [COLOR=#ff0000]## If this has an error, then there is no sense in going on to anything else without posting back here first.. Understood?[/COLOR]
The firs command had an error... Why did you go onto the second command, after my warning? Please follow directions carefully.

Chroot into the system again...
```

sudo mount /dev/sdb3 /mnt  
sudo mount --bind /dev/ /mnt/dev
sudo mount --bind /sys/ /mnt/sys 
sudo mount --bind /proc /mnt/proc
sudo mount --bind /run /mnt/run
sudo chroot /mnt
mount -a
if [ "$(stat -c %d:%i /)" != "$(stat -c %d:%i /proc/1/root/.)" ]; then   echo "We are chrooted!"; else   echo "Not chrooted..."; fi

```
Based on the output of that last command, will tell you if you can go on or not. You need to be chrooted into the system, before going on...

If chrooted into the system, then do
```

mount | grep '/boot/efi'

```
To ensure that the EFI partition is mounted correctly. If it is, then do
```

grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy

```
If there is "any error"... then post back here first before going on.

---

### Post by shane_faulkinbury2 on 2023-05-27
Okay.  Eating right now and on my mobile.  Will do when done.

---

### Post by shane_faulkinbury2 on 2023-05-27
```
mount | grep '/boot/efi'
/dev/sdb2 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
root@ubuntu:/# grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
```

I suppose I am ready to install GRUB?

---

### Post by oldfred on 2023-05-27
Did you ever post brand/model system?
Some like HP make it more difficult and others have UEFI settings set prevent UEFI updates beyond UEFI Secure boot.

Check UEFI settings. Probably separate from UEFI Secure boot. May  be similar to any of these:
HP Zbook 15 NVRAM locked, install issues multiple settings
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
Dell 15 Inspiron 3000 RST & bitlocker off
[https://ubuntuforums.org/showthread.php?t=2469456](https://ubuntuforums.org/showthread.php?t=2469456)
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Lenovo Thinkpad T495 Boot Order Lock
[https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots](https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots)

---

### Post by shane_faulkinbury2 on 2023-05-27
Well, it is a Dell desktop, but it's definitely not an Inspirion. A computer shop owner built it for me.  I think the only thing Dell on it is the motherboard.

Intel(R) Core(TM) i5-4590 CPU @ 3.30GHz   3.30 GHz
16.0 GB
499F07EE-3A68-48EB-9A70-D601DDB6455A
00330-80000-00000-AA004
64-bit operating system, x64-based processor

---

### Post by MAFoElffen on 2023-05-28
Chroot into the system again... This time we will tweak it a bit to favor passing on the efivarfs...
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo mount /dev/sdb3 /mnt  
sudo mount --bind /dev/ /mnt/dev
sudo mount -t efivarfs none /sys/firmware/efi/efivars
sudo mount --rbind /sys/ /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo mount --bind /run /mnt/run
sudo chroot /mnt
mount -a
if [ "$(stat -c %d:%i /)" != "$(stat -c %d:%i /proc/1/root/.)" ]; then   echo "We are chrooted!"; else   echo "Not chrooted..."; fi
ls /sys/firmware/efi/efivars
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy

```

---

### Post by shane_faulkinbury2 on 2023-05-29
Sorry, I had church and then a busy day as today will be being Memorial Day.  Here is what I got doing what you just said:
```
[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
UEFI Firmware mode
root@ubuntu:/home/ubuntu# sudo mount /dev/sdb3 /mnt
root@ubuntu:/home/ubuntu# sudo mount --bind /dev/ /mnt/dev
root@ubuntu:/home/ubuntu# sudo mount -t efivarfs none /sys/firmware/efi/efivars
mount: /sys/firmware/efi/efivars: none already mounted or mount point busy.
root@ubuntu:/home/ubuntu# sudo mount --rbind /sys/ /mnt/sys
root@ubuntu:/home/ubuntu# sudo mount --bind /proc /mnt/proc
root@ubuntu:/home/ubuntu# sudo mount --bind /run /mnt/run
root@ubuntu:/home/ubuntu# sudo chroot /mnt
root@ubuntu:/# mount -a
root@ubuntu:/# if [ "$(stat -c %d:%i /)" != "$(stat -c %d:%i /proc/1/root/.)" ]; then   echo "We are chrooted!"; else   echo "Not chrooted..."; fi
We are chrooted!
root@ubuntu:/# ls /sys/firmware/efi/efivars
AcpiGlobalVariable-c020489e-6db2-4ef2-9aa5-ca06fc11d36a
AMITCGPPIVAR-a8a2093b-fefa-43c1-8e62-ce526847265e
AMITSESetup-c811fa38-42c8-4579-a9bb-60e94eddfb34
An00000000-ff2e9fc7-d16f-434a-a24e-c99519b7eb93
Ar00000000-ff2e9fc7-d16f-434a-a24e-c99519b7eb93
AUTOPILOT_MARKER-616e2ea6-af89-7eb3-f2ef-4e47368a657b
Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0006-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0007-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0008-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootFFFA-5990c250-676b-4ff7-8a0d-529319d0b254
BootFFFB-5990c250-676b-4ff7-8a0d-529319d0b254
BootFFFC-5990c250-676b-4ff7-8a0d-529319d0b254
BootFFFD-5990c250-676b-4ff7-8a0d-529319d0b254
BootFFFE-5990c250-676b-4ff7-8a0d-529319d0b254
BootList-65cbd9d9-ab77-4a61-b288-2763405d588a
BootOneDevice-65cbd9d9-ab77-4a61-b288-2763405d588a
BootOptionSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c
BugCheckCode-ba57e015-65b3-4c3c-b274-659192f699e3
BugCheckParameter1-ba57e015-65b3-4c3c-b274-659192f699e3
BugCheckProgress-ba57e015-65b3-4c3c-b274-659192f699e3
ColdReset-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
CPUS3APICID-1456cc6e-22ac-5289-33ba-2e13bbdabaee
CurrentPolicy-77fa9abd-0359-4d32-bd60-28f4e78f784b
db-d719b2cb-3d3a-4596-a3bc-dad00e67656f
dbx-d719b2cb-3d3a-4596-a3bc-dad00e67656f
DIAGEEPROM_VAR-8ebe3d07-3420-4bfa-8c13-3a4e0fae6860
EfiTime-9d0da369-540b-46f8-85a0-2b5f2c301e15
ErrOut-8be4df61-93ca-11d2-aa0d-00e098032b8c
ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
GNVS_PTR-0a602c5b-05a0-40c4-9181-edcd891d0003
GsetLegacyIplDefaultValue-3a21751e-bd32-4825-8754-82a47f01b09b
GsetUefiIplDefaultValue-7f3301c7-2405-4765-aa2e-d9ed28aea950
IccAdvancedSetupDataVar-7b77fb8b-1e0d-4d7e-953f-3980a261e077
KEK-8be4df61-93ca-11d2-aa0d-00e098032b8c
Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c
LangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c
LastModeState-2d2edd10-1661-47e3-bdff-581f2a63ec0d
MemoryOverwriteRequestControl-e20939be-32d4-41be-a150-897f85d49829
M-ff2e9fc7-d16f-434a-a24e-c99519b7eb93
MokListRT-605dab50-e046-4300-abb6-3dd810dd8b23
MokListTrustedRT-605dab50-e046-4300-abb6-3dd810dd8b23
MokListXRT-605dab50-e046-4300-abb6-3dd810dd8b23
MonotonicCounter-8be4df61-93ca-11d2-aa0d-00e098032b8c
NBPlatformData-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
NetworkStackVar-d1405d16-7afc-4695-bb12-41459d3695a2
OfflineUniqueIDRandomSeedCRC-eaec226f-c9a3-477a-a826-ddc716cdc0e3
OfflineUniqueIDRandomSeed-eaec226f-c9a3-477a-a826-ddc716cdc0e3
OsIndications-8be4df61-93ca-11d2-aa0d-00e098032b8c
OsIndicationsSupported-8be4df61-93ca-11d2-aa0d-00e098032b8c
PBRDevicePath-a9b5f8d2-cb6d-42c2-bc01-b5ffaae4335e
PchInit-e6c2f70a-b604-4877-85ba-deec89e117eb
PchInitPei-a31b27a4-cae6-48ff-8c5a-294221e6f389
PchS3Peim-e6c2f70a-b604-4877-85ba-deec89e117eb
P-ff2e9fc7-d16f-434a-a24e-c99519b7eb93
PK-8be4df61-93ca-11d2-aa0d-00e098032b8c
PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c
PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c
PreviousBootServiceDataInfo-4c19049f-4137-4dd3-9c10-8b97a83ffdfa
Rc00000000-ff2e9fc7-d16f-434a-a24e-c99519b7eb93
Rd00000000-ff2e9fc7-d16f-434a-a24e-c99519b7eb93
S3CpuThrottle-8be4df61-93ca-11d2-aa0d-00e098032b8c
SbatLevelRT-605dab50-e046-4300-abb6-3dd810dd8b23
SecureBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c
SetupMode-8be4df61-93ca-11d2-aa0d-00e098032b8c
SignatureSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c
TcgMonotonicCounter-8be4df61-93ca-11d2-aa0d-00e098032b8c
TcgPPIVarAddr-8be4df61-93ca-11d2-aa0d-00e098032b8c
Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c
TPMPERBIOSFLAGS-7d3dceee-cbce-4ea7-8709-6e552f1edbde
TxtOneTouch-3d989471-cfac-46b7-9b1c-08430109402d
UnlockIDCopy-eaec226f-c9a3-477a-a826-ddc716cdc0e3
UserBootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c
UserBootOrderCount-8be4df61-93ca-11d2-aa0d-00e098032b8c
root@ubuntu:/# grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
Installation finished. No error reported.

```

---

### Post by MAFoElffen on 2023-05-29
That's what I like to see as output... :D

Now, do 
```

update-grub

```
Then reboot and Test.

---

### Post by shane_faulkinbury2 on 2023-05-29
Nope -

```
update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
root@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59# grub-mkconfig
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.

```

---

### Post by oldfred on 2023-05-29
Again, /cow is your live installer. 
To update grub you have to have booted or be in the chroot.

---

### Post by shane_faulkinbury2 on 2023-05-29
?

```
sudo chroot update-grub
chroot: cannot change root directory to 'update-grub': No such file or directory

```

---

### Post by MAFoElffen on 2023-05-30
No... LOL

You exited the chroot or somethig else of 100 things happened... But that error told you that you were back o the filesystem of the LiveUSB...

So this time:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo mount /dev/sdb3 /mnt  
sudo mount --bind /dev/ /mnt/dev
sudo mount --rbind /sys/ /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo mount --bind /run /mnt/run
sudo chroot /mnt
mount -a
if [ "$(stat -c %d:%i /)" != "$(stat -c %d:%i /proc/1/root/.)" ]; then   echo "We are chrooted!"; else   echo "Not chrooted..."; fi
update-grub

```

---

### Post by TheFu on 2023-05-30
> **shane_faulkinbury2 said:**
> Okay, switching back to Windows.

Told me you had left Linux, so why would anyone respond?

Plus, last weekend (through Monday) was a holiday in the US. People were at the lake/ocean with their families eating BBQ and drinking "beverages". ;)

---

### Post by wyattwhiteeagle on 2023-05-30
> **TheFu said:**
> Told me you had left Linux, so why would anyone respond?

Plus, last weekend (through Monday) was a holiday in the US. People were at the lake/ocean with their families eating BBQ and drinking "beverages". ;)

It was a holiday...must be one I don't have memorized yet.
I know Memorial Day is this coming weekend.

Oops...maybe it was this past weekend...
Heck, I don't know my days anymore...lol

---

### Post by shane_faulkinbury2 on 2023-05-30
All looks go.  Giving it a go.
```
$ [ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo mount /dev/sdb3 /mnt
UEFI Firmware mode
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59$ sudo mount --bind /dev/ /mnt/dev
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59$ sudo mount --rbind /sys/ /mnt/sys
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59$ sudo mount --bind /run /mnt/run
ubuntu@ubuntu:/media/ubuntu/e58c7598-4351-465a-a2d0-2fc3eb844b59$ sudo chroot /mnt
root@ubuntu:/# mount -a
root@ubuntu:/# if [ "$(stat -c %d:%i /)" != "$(stat -c %d:%i /proc/1/root/.)" ]; then   echo "We are chrooted!"; else   echo "Not chrooted..."; fi
We are chrooted!
root@ubuntu:/# update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-41-generic
Found initrd image: /boot/initrd.img-5.19.0-41-generic
Found linux image: /boot/vmlinuz-5.19.0-40-generic
Found initrd image: /boot/initrd.img-5.19.0-40-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done

```


[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685") 	 
						[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG] I get frustrated sometimes.  If I left Linux I wouldn't be able to use a computer!

---

### Post by shane_faulkinbury2 on 2023-05-30
I don't know what could of happened.  I installed grub on sda3.

---

### Post by oldfred on 2023-05-30
If you press escape right after vendor logo & before grub menu normally should appear, do you get grub menu?
And then can you boot recovery mode, or second line in menu?
If only one install, menu is not shown by default.

---

### Post by wyattwhiteeagle on 2023-05-30
I'm wondering, the advice in this thread...will it work for data recovery on a USB ntfs flashdrive?

---

### Post by shane_faulkinbury2 on 2023-05-30
Should I have installed it on the entire drive or was sda3 alright?  8-[

Let me check [COLOR=#000000][[COLOR=#C61919]oldfred[/COLOR]]("https://ubuntuforums.org/member.php?u=852711") [/COLOR]
[COLOR=#000000][/COLOR][IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]

---

### Post by shane_faulkinbury2 on 2023-05-30
Nope [COLOR=#000000][[COLOR=#C61919]oldfred[/COLOR]]("https://ubuntuforums.org/member.php?u=852711") [/COLOR]
[COLOR=#000000][/COLOR][IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG], , that didn't work.  It says Failed to start GNOME Display Manager.

---

### Post by MAFoElffen on 2023-05-30
Using the same instructions I gave you to chroot into 'your' system... Save these to memory as doing that:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo mount /dev/sdb3 /mnt  
sudo mount --bind /dev/ /mnt/dev
sudo mount --rbind /sys/ /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo mount --bind /run /mnt/run
sudo chroot /mnt
mount -a
if [ "$(stat -c %d:%i /)" != "$(stat -c %d:%i /proc/1/root/.)" ]; then   echo "We are chrooted!"; else   echo "Not chrooted..."; fi

```
Do that...

The do this
```

cp /etc/default/grub /etc/default/grub.old
nano /etc/default/grub

```
Change the item highlighted in red, to these values:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]--[/COLOR] splash"
GRUB_CMDLINE_LINUX=""

```
Do <Cntrl><O>, <Enter> to save. The <Cntrl><X> to exit...

Those options will force the Grub2 menu to show on boot. Then to pickup those edits, do
```

update-grub

```

Then try 
```

dpkg --configure gdm3
ls -lah /home/YourUserName/

``` substituting your user name in that command, so we can see what the hidden files are there, and their permissions.

EDIT: Actually, By that time you would get that screen, the kernel already booted without error until it tried to bring up the graphics layer, so alternately, at that point, you could jst press <Cntrl><Alt><F4>, which would toggle you over to Console vtty4, where you could log in as yourself, then do those later commands (pre-faced with sudo) to do the grub edits and reconfiguring gdm3...

I apologize in advance, if my post is missing any "n's". Was eating chips and one has gotten under that key on my laptop. Is driving me batty.

---

### Post by shane_faulkinbury2 on 2023-05-30
Do that all on my flash drive running 'Test Ubuntu' or when when trying to get to the grub screen or here?

---

### Post by MAFoElffen on 2023-05-30
The first part would be from the LiveUSB installer, mounting and chrooting into the installed system...

But if you booted from the installed system, and jsut failed at GDM, failing to intialize the GUI desktop, then do what my edit said to do as "You"...

Meaning, if you boot straignt from your computer's hard disk, let it go until it fails...

Then press <Ctrl><Alt><F4>... The screen should toggle to a text Console, session vtty-4. Log in with your credentials. These are the instructions, rewritten to use from this perspective:

```

sudo cp /etc/default/grub /etc/default/grub.old
sudo nano /etc/default/grub

```
Change the item highlighted in red, to these values:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]--[/COLOR] splash"
GRUB_CMDLINE_LINUX=""

```
Do <Cntrl><O>, <Enter> to save. The <Cntrl><X> to exit...

Those options will force the Grub2 menu to show on boot. Then to pickup those edits, do
```

sudo update-grub

```
Then try
```

sudo dpkg --configure gdm3
ls -lah ~/

```

---

### Post by shane_faulkinbury2 on 2023-05-31
Thank you.  Here I go.  I'll follow on my mobile to insure I get everything.

---

### Post by shane_faulkinbury2 on 2023-05-31
Darn, forgot my username!

---

### Post by shane_faulkinbury2 on 2023-05-31
Is there anyway to reset it booting in from the Ubuntu install ISO?

---

### Post by MAFoElffen on 2023-05-31
> **shane_faulkinbury2 said:**
> Darn, forgot my username!
I hate when that happens... LOL
> **shane_faulkinbury2 said:**
> Is there anyway to reset it booting in from the Ubuntu install ISO?
You do not need to reset it, if you can be reminded of it, right?

Booted from the LiveUSB... Use the file manager to look at that partition/volume, and the /home folder there will have a subfolder with the name of your "user"... Write that down. Then you just need to remember your password right?

If you then can not remember your password, then chroot into the installed system, and while chrooted into it (you will be the root user):
```

passwd user_name

```
Substituting user_name with the user name you wrote down, to change that User's password.

---

### Post by oldfred on 2023-05-31
This mentions making a image backup 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
There are two different programs for making an image of a damaged device, in preparation for rescuing files.  They are confusingly given the same name: 



[LIST]
[*][GNU ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") (packaged as [gddrescue]("apt:gddrescue"), though once installed the command is "ddrescue") 

[LIST]
[*]This is the one you want.  **This documentation currently only applies to GNU ddrescue.** 
[/LIST]

[*][URL="http://www.garloff.de/kurt/linux/ddrescue/"]
[/URL]
[/LIST]

---

### Post by shane_faulkinbury2 on 2023-06-01
I did all you said and on reboot the system stuck here -

---

### Post by shane_faulkinbury2 on 2023-06-01
Sorry, not that one.  I must have not got a picture of it, but will try again tomorrow.

---

### Post by shane_faulkinbury2 on 2023-06-01
Got a screen shot before hitting the sack.

---

### Post by MAFoElffen on 2023-06-02
From there, If you press <Cntrl><Alt><F4>, does it get to a Console VTTY4 Login screen?

If so, the log in, then do
```

grep . /etc/X11/default-display-manager

```
If it says '/usr/sbin/gdm3', then do this
```

sudo nano /etc/gdm3/custom.conf 

```
Got down to the line that says
```

#WaylandEnable=false

```
Uncomment it like this
```

WaylandEnable=false

```
Save and exit...

Than do
```

sudo systemctl start gdm3.service
sudo dpkg-reconfigure gdm3
systemctl status gdm3.service

```
If, for some reason you can not toggle over to any vtty session, the boot from a LiveUSB and chroot back into the installed system ad do those same changes.

---

### Post by shane_faulkinbury2 on 2023-06-02
I'm stuck at -
It says failed because the control process exited with error code.

---

### Post by MAFoElffen on 2023-06-02
At the prior command:
```

grep . /etc/X11/default-display-manager

```
What does it say?

---

### Post by MAFoElffen on 2023-06-02
Waiting for that feedback, so I can give you instructions... You could just type out what it says.

---

### Post by shane_faulkinbury2 on 2023-06-02
Everything was done in nano and then when performing sudo systemctl start gdm3.service I got an error. In finale I got the screenshot.

---

### Post by MAFoElffen on 2023-06-03
You didn't post the results of
```

grep . /etc/X11/default-display-manager

```
This is the third time I am asking for that. We need to ensure that that "is" the DM you are using, or we are just chasing ghosts on making something work, that really isn't configured...

O the error when enabling gdm3, I am thinking that when using 'enable', if it is already running, it may be getting a false-positive on that. Which it would also be an error if another DM is configured in it's place.

What happens if you use
```

sudo systemctl restart gdm.service

```
*** But then again, that is just trying to restart gdm to pick up the edits you made to /etc/gdm3/custom.conf I suggested without having to reboot... You could just reboot and see if that worked. 

And if not, then go straight to 
```

systemctl status gdm

```
to check if it is running or not.

But, again, that depends on what the default DM is configured as... See why having that information is "required"?

---

### Post by shane_faulkinbury2 on 2023-06-03
When I ran a ```
[COLOR=#000000][FONT=&quot]sudo systemctl restart gdm.service[/FONT][/COLOR]
```  everything went fine.  When running a ```
[COLOR=#000000][FONT=&quot]systemctl status gdm[/FONT][/COLOR]
```  I got this

---

### Post by MAFoElffen on 2023-06-04
> **shane_faulkinbury2 said:**
> When I ran a ```
[COLOR=#000000][FONT=&amp]sudo systemctl restart gdm.service[/FONT][/COLOR]
```  everything went fine.  When running a ```
[COLOR=#000000][FONT=&amp]systemctl status gdm[/FONT][/COLOR]
```  I got this
No, it told you the truth... Look at the attached photo to see what you typed instead of. You had a typo and it couldn't find the command of that. Please try again.

---

### Post by shane_faulkinbury2 on 2023-06-04
Okay, I guess I did have a typo.   I did what you said this morning and here is what I got.

---

### Post by MAFoElffen on 2023-06-04
Okay now. 'gdm3' is installed, and is the default DM, so now lets try to get it working again.

Do
```

sudo apt install --reinstall gdm3

```

---

### Post by shane_faulkinbury2 on 2023-06-04
Here you go.

---

### Post by MAFoElffen on 2023-06-05
Back to "No space left on drive..." (Again...)

You really need to clean up your User $HOME folder to make some room. I think i remember you posting that you had over 80+ GB there. 

Have you thought about adding anther cheap drive to move your home to another drive? That would solve everything, quickly and efficiently.

---

### Post by shane_faulkinbury2 on 2023-06-06
It looks like that is what I'm going to have to do.  I have a bunch of flash drives, but not another external HDD or SSD.  I'll have to research and go buy one.  Should I close this thread or wait until I do that?

---

### Post by MAFoElffen on 2023-06-06
I would keep it open until this is resolved. 

It is not fixed, and you have the same problem. Let's continue when you get some storage to make some room to fix this problem, right?

I'm patient.

---

### Post by shane_faulkinbury2 on 2023-06-06
Cool brother, thanks.

---

### Post by shane_faulkinbury2 on 2023-06-10
I have a pretty large capacity HDD.  What if I just create another Ubuntu partition, put another Ubuntu OS on it and transfer my videos to a flash drive and then rewrite Ubuntu alongside Windows 10?

---

