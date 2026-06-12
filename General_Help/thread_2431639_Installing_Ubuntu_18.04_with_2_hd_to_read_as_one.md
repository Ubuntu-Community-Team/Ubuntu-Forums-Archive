---
title: "Installing Ubuntu 18.04 with 2 hd to read as one"
date: 2019-11-19
forum: General Help
---

### Post by dohm11 on 2019-11-19
Hi Newbie here, 
                         I have started to use Ubuntu to get on my own server and play around. I have just received a brand new 2T Hd and ready to clean install Ubuntu. My original HD is a 2T. This will be making my server a 4T in total. I have read up some info online but seem complicated and I can't seem to get my head around this. 

So /dev/sda (ext4) and dev/sdb (Free space) (Both 2T)

How would I go about to have my sda and sdb as one? 

Making the full drive one big 4t instead of 2 separate 2t... I am at the installation type now. I am doing a clean wipe of everything as I have a back up (external hd which I can re-upload everything after)

Thank you so much for tech geeks which hopefully I will become too one day lol.

Dohm

---

### Post by SeijiSensei on 2019-11-19
Depends on what you mean by "as one." Combining devices usually involves "RAID" technologies. In RAID 0, the two drives are connected in series, so your two, 2 TB drives will appear as one 4TB drive.  In RAID 1, the drives are managed in parallel with all data written to and read from both drives simultaneously.  This provides redundancy should a drive fail, but it's important to remember the adage "RAID is not a substitute for backups."

However I suggest you consider a different approach, one that's likely easier to manage if you don't have much Linux experience.

During installation, choose the "manual" or "something else" option when you reach the drive partitioning stage. Tell the installer to place the system on /dev/sda with ext4 format. Then tell it to mount /dev/sdb (also ext4) as /home.  Then all the home directories will occupy the second drive, while everything else will be on the first drive.  

Rather than referencing drives as C:, D:, etc., like Windows, Linux puts everything under the root ("/") filesystem. So /home need not be on the same drive partition as the rest of the filesystem.

This will leave you with a lot of unused space on /dev/sda.  A better method might be to tell the installer to allocate, say, 50 GB to the root filesystem, and create another partition that spans the remainder of the drive and mount it somewhere else, say as /data.  

Now if you're really hardy and willing to get your hands dirty at the command prompt, you could install mdadm and try to set up a RAID0.  (If you're using the Server edition of Ubuntu, mdadm will already be there. On a desktop machine, you'll need to run "sudo apt install mdadm" first.)  Now tell the installer to create a 50 GB partition for the root filesystem, we'll call it /dev/sda1, and a second filesystem on the first drive called /dev/sda2.  Create another partition on the second drive, /dev/sdb1, and have it span the entire drive. Don't bother to format either of these filesystems; we'll do that momentarily. 

Now you can use mdadm to concatenate /dev/sda2 and /dev/sdb1 into a single RAID0 device like this:

```
sudo mdadm --create /dev/md0 --raid-devices=2 --level=0 /dev/sda2 /dev/sdb1
```

When that finishes you'll have a big RAID0 device that will be 2 X 2 TB - 50 GB in size that will be referenced as /dev/md0.  Now we'll format that device as ext4:

```
sudo mkfs -t ext4 /dev/md0
```

Finally decide where you want to mount the device in the filesystem. Again I'll recommend /home.  To do this, we'll edit the file /etc/fstab. You need to do this with sudo. You can use the command "sudo nano /etc/fstab" to use the nano editor.  The commands for the editor consist of control-key sequences which are represented as ^S, ^X, etc.  The various commands appear at the bottom of the editor window. ^S means hold down the Ctrl key and type the appropriate letter, e.g., Ctrl + S to save the file.  Add this line to the bottom of the file

```

/dev/md0    /home     ext4    defaults     0 0

```

Save the file and reboot. Then type the command "df" at a terminal prompt to see the layout of your filesystems.  For instance, on my server you'd see

```

Filesystem      1K-blocks       Used Available Use% Mounted on
/dev/sda3        50264772   23269956  24434816  49% /
tmpfs             1893412         80   1893332   1% /dev/shm
/dev/sda2          511720        280    511440   1% /boot/efi
/dev/md0        909757100  378657224 484880204  44% /home
/dev/sde1      3845577736 3109730936 540495968  86% /media/external
/dev/md127     2884023328 2148643696 588872944  79% /media/raid

```

I have two RAID devices on this machine named /dev/md0, which is mounted as /home, and /dev/md127, which is mounted as /media/raid.  (Both of these are RAID1 devices where the two devices operate in parallel.) The operating system is installed to /dev/sda3. /dev/sde1 is a 4 TB USB external drive that I use for backups. I export both /home and /media/raid from this machine using a protocol called NFS which is the native file-sharing method in *nix.  I also export them both using a program called Samba which allows them to be mounted from Windows using the standard method of attaching them to a drive letter as a "network drive."

---

### Post by dohm11 on 2019-11-19
Yes... As one meaning... The desktop computer now holds two 2T (Previously only had one 2T HD installed (sata)), problem is I don't know how to couple/merge them together to make one section... IE: 4T overall (+/- the required space for merging) 

Same as window would do when you want to re-allocate the extra space, making a partition(s), to the C: going in Disk Management. 

I know about GParted, but it did mentioned I could lose all data which I don't really care as I am doing a clean install... but did not have the proper explanation, or was just way out of my league, on how to merge two hard drive together.

Cool I will try and work with what you have mentioned. 

Thank you so much [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195").

---

### Post by TheFu on 2019-11-19
Or use LVM.  It would be smart to follow the partitioning best practices. Unix isn't Windows. You really don't want 4TB for / or the OS.  That is NOT a best practice.

Warning - any of these "merging" techniques means tremendous data loss if either disk fails, so really having storage spread across 2 disks that isn't RAID1 or RAID10 is a poor idea.

Or you could use normal Unix built-in capabilities to gracefully make access to the 2nd disk available in a convenient way using **symbolic links**.  This would be a loose coupling and would limit data loss from a drive failure to just the 1 disk impacted.  Lots of people use symbolic links to media areas on different disks.  [https://en.wikipedia.org/wiki/Symbolic_link](https://en.wikipedia.org/wiki/Symbolic_link) These have been around 40 yrs for Unix systems and work with 99.999999% of programs.  They are part of the file system, unlink what Windows attempted to accomplish with "libraries" that were not file system objects and don't work with all programs.

If you choose to setup LVM during the install, then you could add the 2nd disk to a new PV and add that PV into an existing VG, then create LVs as needed.  You'd never need to know which physical disk where the data was actually stored. 
A tutorial on LVM: [https://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](https://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

LVM provides flexibilities that RAID1 doesn't.  You can even setup RAID1 with LVM using only LVM commands.  Breaking the RAID or recreating the mirror is possible too.  Some people will do that to make a clone of their system to move to another physical machine.

I truly hope you have excellent backups if merging storage is the plan.

---

### Post by CatKiller on 2019-11-19
> **dohm11 said:**
> How would I go about to have my sda and sdb as one? 

So, to step back a bit here, since you describe yourself as a newbie. 

Linux doesn't care about drives in the way that Windows does. It uses a single unified filesystem tree that starts at / and has other locations branching from there. Those branches could be directories on the same partition as /, or they could be other partitions, or they could be on a different computer entirely. The process of assigning a particular device to a particular location in the filesystem tree is called **mounting**.

The others have already covered ways to do what you specifically asked for, and highlighted some of the downsides of doing so. RAID is the older method, and LVM is more flexible, and they're both relatively complicated but great for specific needs.

Instead, what I'd recommend is that you create a smallish partition for / (around 50 GB would give you *plenty* of room for anything you're likely to use) and have the rest of that drive as one big partition that you mount as /home. All your settings, media, Steam games, and so on, are generally going to live in your Home directory. If you need to reinstall the OS at any point you can just do so over the / partition and leave your /home partition untouched. 

The other drive I would use as flat storage, mounted out of the way somewhere like /mnt. You can use symbolic links to locations in your Home folder or wherever for ease of access, and if you ever need just that data you can just pull the drive and plug it into another computer: it's not reliant on anything because it's just flat data.

---

### Post by TheFu on 2019-11-19
+1 to what CatKiller suggests.  For someone knew to Unix/Linux, LVM and RAID are not beginner-level skills.

I'd probably go with 25G for / and the rest for /home/ unless there is a specific need somewhere else.
If this is for a server, then the type of server being planned could matter.  Lots of people here run all sorts of servers and storage design is an important aspect of total server design.   

Many media servers have no problem with handling multiple partitions for the same or different sorts of media.  I run a Plex server that is connected to 3x4TB primary disks and 3x4TB backup disks.  The server has music, photos, movies and tv recordings.  There are directories for each of those different types of media on each disk as my library expanded.
These are on partition 1 of disk 1:
```
/D/T1
/D/M1
/D/P1
/D/Music1
```
Partition 1 of disk 2 has:
```
/D2/T2
/D2/M2
/D2/P2
/D2/Music2
```
I bet you can guess what partition 1 of disk 3 has.
Inside the Plex settings, there adding multiple directories for all Movies, TV, Photos, and Music is easy.  Plex integrates the view from 3 disks into 1 for Music.  Kodi does the same thing.

Symbolic links can do the same thing on the file system so you forget where stuff is because you don't need to know.

---

### Post by dohm11 on 2019-11-20
> I'd probably go with 25G for / and the rest for /home/ unless there is a specific need somewhere else.

So what should I choose for my sdb free space? 

I can do a partition for sda to make it 50g at / and the rest of the space for /home 

I got option for
/boot
/tmp
/var and so on but I cannot add two to /home

Should I make my second HD (sdb) to Logical? 

Sorry for all the questions I am trying to really understand this part. I may need to add more server space = to more HD, I like to keep my stuff tidy and nice for all information to be at one specific place. 

My previous built was on the same location ( accessing the ftp going to one single folder with with all my sub folder, when there was a problem I knew exactly where to retrieve or fix that file) 
User/ftp/folders... within this folders all sub folder with files in them.

---

### Post by TheFu on 2019-11-20
Don't confuse the entire disk (sdb) with partitions (sdb1, sdb2, sdb100) on the disk.  Windows says "disk" almost always when it really means "partition".  C: is a partition on a drive.  D: is a partition on a drive.  It might be the only partition and it might take up almost all of the drive, but it is still a partition.

You shouldn't be using MBR/MSDOS partitioning. You should have GPT partitioning.  In MSDOS partitioning, we are limited to 4 primary partitions.  With GPT, there aren't any practical limits to the number of primary partitions.  For HDDs over 2TB in size, GPT must be used or only 2TB will be available. The rest is inaccessible.   Choose GPT whenever possible. There are many reasons.

Plain FTP shouldn't be used. It should have died out around 2002.  sftp should be used instead since around 1997.  Every client OS with networking has excellent sftp programs.  On Linux systems, sftp:// in a file manager URL is supported for drag-n-drop stuff between systems, as needed.  sftp is considered secure enough for use over the internet.

BTW, you keep asking questions without providing data.    Run this command and post both the command and output back here inside 'code tags'. 
```
lsblk -o name,size,type,fstype,mountpoint
```
If it doesn't look the same here as it does in your terminal, then you didn't get the code-tags correct. Please try again.

---

### Post by dohm11 on 2019-11-20
Sorry about that will use 'code tags from now on" and yes ftp old which sftp was used. 

I am still at the installation screen which I really want to do properly.

Here is what the window screen looks like: 

```

Device                  Type           Mount point           Format?          Size           Used            System
/dev/sda                                                                              
Free Space                                                     [ ]          2000398 MB                                                                                                                                                                            
/dev/sbd                                                                                                                                                                           
Free Space                                                     [ ]          2000398 MB    


```

Using ubuntu-18.04.3-desktop-amd64 (Which I like to access once in awhile) Rest is using putty to access Terminal.

Other info: Reading online and it's letting others know to create a 25gb to 50gb at mount point "/" on the sda and include the rest as mount point "/home". 
I am looking to know what to, do and how to, set the sdb to. Do I leave it to "Free Space / create new partition and to set it to what?

Also this way I will know what to do in the future when I need to add more HD for more space. This computer and hold 4 external hard drive and my data is quickly ramping up space therefore more hd will be installed.

---

### Post by oldfred on 2019-11-20
I use data partition(s).
I have / in 25GB or so on SSD and large data partition on sdb. I then link folders from data partition back into /home, so Documents, Music, etc are really on sdbX but  in system look like they are in /home. I like to have an install on every drive, just for emergency boot.
I started using gpt in 2010 with BIOS systems, but now have UEFI.

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

I still have error on ESP. I made it GB when it should be 500MB. I plan on another / partition or two for test installs and will use that space for those.
```
fred@Bionic-Z170N:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda4      ext4   25G   11G   14G  43% /
/dev/sda1      vfat   50G   79M   50G   1% /boot/efi
/dev/sdb6      ext4  298G   88G  196G  31% /mnt/data
/dev/sdb4      ext4  146G   64G   75G  47% /mnt/backup
```

---

### Post by TheFu on 2019-11-20
There are 50 different ways to accomplish what you seem to be asking.  Adding storage later has very little to do with how things are setup during installation, except that big choices like to use or not use LVM is best handled at install time.

Above, 3 options have been provided.
[LIST=1]
[*]Use mdadm and RAID0 (if either drive fails, expect 100% data loss)
[*]Use LVM with or without RAID0  (if either drive fails, expect 100% data loss)
[*]Use symbolic links from 1 directory into multiple partitions on the same or different disks. (data loss would be limited to only the drive that died)
[/LIST]

If you have excellent backups, then I'd go with using LVM because it has flexibility that the other methods do not.  It is also more complicated.  LVM has been around and used in enterprises for well over 20 yrs. It is solid. But if 1 disk fails, expect total data loss across the other disks too.

mdadm for RAID0 is probably the easiest, but there are RAID problems that happen "just because" where the only answer is to wipe the RAID set, recreate it from nothing and restore from backups.   mdadm has been around and used in enterprises for well over 20 yrs. It is solid.  But if 1 disk fails, expect total data loss across the other disks too. You've been warned.

Symbolic links isn't as fancy, but it can easily get the job done.  If your plan is to have 1 directory with 500+ files inside it, that is a bad plan.  File systems get slow with that many objects inside them.  But with a few sub-directories, it is easy to have symbolic links point to storage locations on different disks.

There are a number of overlay file systems which sit on top of existing storage and make them all appear as one. These are popular with people who aren't used to enterprise setups like LVM.  You can look up unionFS and overlayfs and aufs and mergerfs.  I consider these to be hobbyist solutions.  Not once have I seen them deployed inside any company.

So ... please pick one of these solutions.  If you go with mdadm and RAID0,  SeijiSensei's answer is excellent.

Regardless of the answer, you want 
* GPT partition tables
* At least 1 partition on each HDD.  
* / should be 25G, IMHO.  If you use LVM, this will be an LV.
* If you use UEFI to boot, then there will need to be at least 2 other partitions - the EFI partition and the /boot partition.
* I would have a swap partition - that's a personal preference. If you use LVM, then a swap LV would be inside the 1 huge partition that the PV and VG are inside.

It is your choice.

To see how lsblk can look with LVM, [https://ubuntuforums.org/showthread.php?t=2430449](https://ubuntuforums.org/showthread.php?t=2430449)  is a fairly short thread where the OP needed to expand a full 4GB LV but that 1.7TB available. That was a very simple issue due to LVM and having plenty of storage available in the VG, volume group.  If you have multiple disks, with LVM you can add each partition (which we'd allocate as a separate PV) into the same VG which spans partitions and/or disks as much as you like. Then create or expand LVs, Logical Volumes, without know exactly where the VG storage is located.  This 3-pivot point solution effectively means having infinite possibilities for storage management. There is a price for this amazing flexibility. That is complexity.

---

### Post by dohm11 on 2019-11-20
> **TheFu said:**
> 
```
lsblk -o name,size,type,fstype,mountpoint
```
If it doesn't look the same here as it does in your terminal, then you didn't get the code-tags correct. Please try again.

Here is what I came back with, just to answer your request: 

```

NAME     SIZE TYPE FSTYPE   MOUNTPOINT
fd0        4K disk
loop0   88.5M loop squashfs /snap/core/7270
loop1   14.8M loop squashfs /snap/gnome-characters/296
loop2      4M loop squashfs /snap/gnome-calculator/406
loop3   54.4M loop squashfs /snap/core18/1066
loop4    3.7M loop squashfs /snap/gnome-system-monitor/100
loop5   42.8M loop squashfs /snap/gtk-common-themes/1313
loop6  149.9M loop squashfs /snap/gnome-3-28-1804/67
loop7   1008K loop squashfs /snap/gnome-logs/61
sda      1.8T disk
&#9500;&#9472;sda1  46.6G part ext4     /media/dohm/37a1074d-a847-46c6-95ef-6ac41618ef68
&#9500;&#9472;sda2     1K part
&#9492;&#9472;sda5   1.8T part ext4     /
sdb      1.8T disk
&#9492;&#9472;sdb1   1.8T part ext4     /home
sr0     1024M rom

```

---

### Post by TheFu on 2019-11-20
I would shrink sda5 down to 25G ASAP.  Then make another partition for data and perhaps 1 for swap.  Swap on a desktop should be 4.1GB in size unless you hibernate. Hibernation has security repercussions.

I guess you decided against LVM and RAID/mdadm.  Excellent.  

Some light reading on symbolic links. [https://en.wikipedia.org/wiki/Symbolic_links](https://en.wikipedia.org/wiki/Symbolic_links)
And don't forget that every command on a Unix system has a manpage which explains options in detail.
**man ln**

---

### Post by dohm11 on 2019-11-20
Thank you all... > I guess you decided against LVM and RAID/mdadm.  Excellent. 

Just trying to understand as I go and learn :) 

Starting from scratch is easy, just have to reboot ubuntu again and do it right this time. 

I am reading most/all links provided in this thread, just got to remember to get back in the "coding" side of things lol only been using linux for about a year now with some cheat sheets to add as I go.

On my off to read, thank you so much for everything :)

---

