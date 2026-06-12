---
title: "Newbie question - what partition is my Home folder installed on?"
date: 2022-02-06
forum: General Help
---

### Post by uacnt83982803 on 2022-02-06
I set up a 2nd laptop using Ubuntu 20.04LTS.  I have a 537MB FAT partition mounted at /boot/efi, device name /dev/sda1.

I also have an Extended Partition 2 of 320GB and a Filesystem Partition 5 of 320GB.

The extended partition 2 is device /dev/sda2 and the filesystem partition 5 is device /dev/sda5

Is my /home folder, and every file I've place there, in the 537MB FAT partition, or in the Extended Partition 2?  I can't tell.

For this install, unfortunately I didn't select Advanced disk options and wipe everything out during the install.

I'd like /home and everything under it to be on the extended partition 2.

---

### Post by GhX6GZMB on 2022-02-06
Open a terminal and run lsblk. That should tell you where things are.

---

### Post by uacnt83982803 on 2022-02-06
Hmm.  Unfortunately that doesn't give me any more information.  In other words, it echos what I wrote in my original post.

---

### Post by uacnt83982803 on 2022-02-06
sda1 reports 536MB free, out of the 537MB space, so only 1MB used, mounted at /boot/efi.

sda2 reports it is 320GB in size, not mounted.

sda5 is mounted at Filesystem Root with 304 of 320GB free.  

My /Home folder reports it is using 160.2MB, and 287.9GB free.

---

### Post by GhX6GZMB on 2022-02-06
Which means your installation has failed totally. Redo from start. This is the output from my simple laptop:
```
macro@macro-pc:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223,6G  0 disk 
&#9500;&#9472;sda1   8:1    0  29,3G  0 part /
&#9500;&#9472;sda2   8:2    0 188,3G  0 part /home
&#9492;&#9472;sda3   8:3    0     6G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  
macro@macro-pc:~$ 

```
This might also help, it tells you which file system is used (ext4 for Ubuntu is best):
```
macro@macro-pc:~$ blkid
/dev/sda1: UUID="1638bc2d-d547-4994-868e-72ea81c42f9e" TYPE="ext4" PARTUUID="7e408a68-01"
/dev/sda2: UUID="8a04a816-20f0-4685-a0b4-d4d25e77be98" TYPE="ext4" PARTUUID="7e408a68-02"
/dev/sda3: UUID="f6c1f1e8-4923-49d6-b0a6-760b4545424e" TYPE="swap" PARTUUID="7e408a68-03"
macro@macro-pc:~$ 



```

---

### Post by oldfred on 2022-02-06
This should show you more info:
lsblk -e7  -o FSTYPE,NAME,LABEL,PARTLABEL,SIZE,FSUSED,MOUNTPOINT

And some have posted that an ESP - efi system partition (FAT32) is created even with BIOS installs on MBR drives.
If not booting Windows in BIOS mode, you should not really use MBR(msdos) but use gpt.
And if system is UEFI, then better to install in UEFI boot mode.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Note that converting from MBR to gpt normally erases all partitions on drive. So have good backups.
Or this which may not erase everything.
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by uacnt83982803 on 2022-02-06
It shows:

sda
  sda1 512M 4K /boot/efi
  sda2 1K
  sda5 297.6G 8.9G /
  sr0 1024M

Home isn't listed, but obviously it's there.

To  				 				 					 						 	[**[COLOR=#000000]ml9104[/COLOR]**]("https://ubuntuforums.org/member.php?u=2127041")'s point, I can redo from scratch easily.  Very little stuff installed.  I guess I need to select Advance when the install gets to disk setup.  Should I just wipe out and have one big partition for everything?  Or what's the best way?

---

### Post by uacnt83982803 on 2022-02-06
blkid shows:
/dev/sda5:  UUID="........." TYPE="ext4" PARTUUID="...."

---

### Post by GhX6GZMB on 2022-02-06
You did not enter@oldfred's command correctly in a _terminal_. Your output is from something else.

---

### Post by GhX6GZMB on 2022-02-06
> **uacnt83982803 said:**
> blkid shows:
/dev/sda5:  UUID="........." TYPE="ext4" PARTUUID="...."

You're apparently of the opinion that the UUIDs are part of an NSA scheme to track you. They're not. They're 100% internal to your machine and randomly assigned.
Second: when you post the output of a terminal command, enclose the output with [CODE] brackets in your post. Highlight the text and click the "#" button on the top menu (you may need to click "Go Advanced" first).
Thanks.

---

### Post by uacnt83982803 on 2022-02-06
Actually, I did.  Typed it in a terminal directly.  lsblk......

Results:
sda (edit: I forgot to type this: 298.1G)
  sda1 512M 4K /boot/efi
  sda2 1K
  sda5 297.6G 8.9G /
  sr0 1024M

---

### Post by uacnt83982803 on 2022-02-06
Sorry.  It's running across VNC and I just typed the pertinent parts (or so I thought), skipping the long strings.  Having a problem copying from the VNC instance and pasting here on the host.

---

### Post by Impavidus on 2022-02-06
You have your entire installation in one big partition.

/dev/sda1 is an efi partition. It contains the bootloader on UEFI installs, but it looks like you've got a legacy install. On old computers, like my 11 year old laptop, that may be better, but nowadays its generally recommended to use UEFI installs. On a legacy install there's nothing in the efi partition. There's no reason for the existence of that partition, but the installer created one anyway.

/dev/sda2 is an extended partition. It's a container for additional partitions, invented because your harddrive uses a partitioning method (MBR) that only supports 4 partitions directly. There are no files directly in /dev/sda2.

/dev/sda5 is the only partition containing actual files. Your entire system is there, including your home directory. /dev/sda5 is inside /dev/sda2.

So it looks like everything went OK, except that maybe it was better to use UEFI and GPT partitioning than legacy and MBR partitioning.

---

### Post by grahammechanical on 2022-02-06
Unless we create a partition to specifically be a Home partition and tell the installer to mount that partition as /home, the installer will install Ubuntu in a partition called the root partition. In this case Home will be a folder under the root ( or / ) directory.

If you open the file manager (Files) and click on Other Locations you will see Computer as a location. Click on Computer and you will have opened your root ( / ) directory. Inside the root directory you will see several system folders including a home folder. Click on the home folder and you will see a folder with your username. That is your home folder. Every user we create will have their own username folder.

If we have installed Ubuntu with a partition mounted as /home, then clicking on Other Locations>Computer>home>username folder will bring us to our home folder in the specially created home partition.

So, the answer to your question is: your home folder is in your Ubuntu (root) partition. 

Regards

---

