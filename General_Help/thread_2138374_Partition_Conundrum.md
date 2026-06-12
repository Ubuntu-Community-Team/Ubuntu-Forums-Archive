---
title: "Partition Conundrum"
date: 2013-04-23
forum: General Help
---

### Post by gagsays on 2013-04-23
Hi,
I have spent last few day setting up my computer (xubuntu 12.10) to the very last detail, like configuring sickbeard, sabnzbd, plex, bumblebee, various hacks to correct minor annoyances, themes, docks, various softwares etc.
And now I just realized, I have made one fatal mistake - My partition are are messed up!

Current configuration of partitions is as follows -

[IMG]http://i.imgur.com/y5RN6zo.png?1[/IMG]

And I want to achieve - 
1. Split current swap partition into two parts
[LIST]
[*]/boot partition (must align with beginning of HDD) : about 100-200 mb
[*]/swap partition with remaining memory (BTW i have 4gb RAM)
[/LIST]
2. Move my home partition (either of following two scenarios)
[LIST]
[*]Shrink /(root) partition and move /home to unallocated space, of course along with files currently present in home.
[/LIST]
                                             OR
[LIST]
[*]Simply mount /dev/sda3(ntfs) as my new home. Will there be any issues because of "non ext" partition?
[/LIST]


I wish to keep ntfs partition intact because that is where I keep my data files like music, movies, downloads etc. If I ever want to install windows in future I can simply delete other partitions and I am good to go. I do not plan on dual booting.

And the reason I want to make separate home partition is - If i ever have to reinstall ubuntu then my basic data and settings will be preserved, right?

I have already read few guides online from here and official wiki.ubuntu but still I am not confident enough to pull this off. Furthermore, I already have 3 primary partitions because of that I am not sure how to handle this situation. 

Plausible solutions-
[LIST=1]
[*]May be if I can make the first partition itself as extended and then split it into /boot and swap. I don't know if it's a good idea to make boot partition as extended
[*]Don't make separate swap partition but instead use file on harddisk for swap memory.
[/LIST]

Thanks for your time and any help will be appreciated.
Note: I am new to linux please provide complete instructions.

---

### Post by oldfred on 2013-04-24
I do not like moving partitions left, prefer to have a couple of primary partitions at the beginning of a drive and then make the rest of the drive extended with many logicals.

Why a separate /boot. Most desktops do not need that. You can just shrink sda2 to 25GB and make a new /home. 
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

You actually do not have a lot of room in your NTFS partition. I know when it is a Windows system partition it needs 30% free to work well, and at 10% free is very slow and you just about cannot defrag as there is no working room.

You cannot make /home NTFS. But you can have all data in NTFS and then /home is tiny, easily backed up. My /home is 2GB with 1.5GB of that .wine for Windows version of Picasa. So /home is only about 500MB for its mostly hidden settings. I do agressively move data folders and some hidden folders like the Firefox profile to data partitions. I have two one NTFS from when dual booting XP and the other Linux formatted for all new data as I stopped using XP.

---

### Post by gagsays on 2013-04-24
> **oldfred said:**
> I do not like moving partitions left, prefer to have a couple of primary partitions at the beginning of a drive and then make the rest of the drive extended with many logicals.

Why a separate /boot. Most desktops do not need that. You can just shrink sda2 to 25GB and make a new /home. 
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

You actually do not have a lot of room in your NTFS partition. I know when it is a Windows system partition it needs 30% free to work well, and at 10% free is very slow and you just about cannot defrag as there is no working room.

You cannot make /home NTFS. But you can have all data in NTFS and then /home is tiny, easily backed up. My /home is 2GB with 1.5GB of that .wine for Windows version of Picasa. So /home is only about 500MB for its mostly hidden settings. I do agressively move data folders and some hidden folders like the Firefox profile to data partitions. I have two one NTFS from when dual booting XP and the other Linux formatted for all new data as I stopped using XP.

Thanks for replying.

While I was waiting for answers, i tried using [this guide]("https://help.ubuntu.com/community/BootPartition") but it didn't go well.
Basically, I split the original swap into 100or200 mb boot and and the rest as swap partition.

Then I again deleted those two partition and merged them again into one partition using gparted and used boot-repair utility. Now ubuntu wont boot and gets stuck at grub prompt.

Here is the logfile generated by boot-repair utiliy [http://paste.ubuntu.com/5597451/](http://paste.ubuntu.com/5597451/)

Now that I have read your response, I feel, I should only shrink the main partition and create new home partiton . But before that how can I fix the above grub problem.

---

### Post by oldfred on 2013-04-24
I do not see a /boot partition?

You also installed grub to a PBR or partition boot sector. Grub does not like that but it can be done. And you have grub in the MBR that says it is looking for the rest of grub in partition 1 msdos2. Not sure if script did not parse MBR correctly?

A boot flag is not a boot partition. Windows uses boot flags, grub does not. You should always have a boot flag on the primary NTFS partition with Windows boot files. Its boot loader uses boot flag to find the Windows install. Grub does not need the flag to find Windows, but even if repairing Windows it need the flag to know what partition to repair. Use gparted to put boot flag on sda3, but it looks like it does not have boot files, so it really then does not matter.

It looks like Boot-Repair also is trying to fix sdb, which I assume is you flash drive?
Because you deleted & recreated swap the UUID in fstab is wrong. You need to fix that. But it should boot, just with errors. So you can fix from inside your install.

Try Boot-Repair again. Is it the same version as your install or are you running from your installer with Boot-Repair added?
IF not try manual repair.

       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda2 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda2 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

