---
title: "Ubuntu may be installed wrong partion"
date: 2017-02-15
forum: General Help
---

### Post by eddugo on 2017-02-15
I had a problem installing Ubuntu 16.1in UEFI and after many attempts was helped by someone on this forum in this thread: 
[SOLVED] Dual boot problem on new Dell Latitude E5470
The attempts by me to install chopped up my hard drive and I think Ubuntu is installed in the wrong partition as I orig made a 320 gig part and when I select properties in my home folder, I only have 13 gigs of storage with nothing stored anywhere.  I had other problems with  the online accounts app freezing and sometimes very slow performance.  I would like to 1.  fix the hard drive problem - get rid of the small unused partitions  and 2. do a fresh install to get everything working properly.

---

### Post by oldfred on 2017-02-15
Post these:

sudo parted -l
df -h
cat /etc/fstab
mount

If longer output use code tags, you can easily add code tags with forum's advanced editor and the # icon.

---

### Post by eddugo on 2017-02-15
Warning: failed to translate partition name
Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  524MB  523MB   fat32           EFI system partition          boot, esp
 2      524MB   659MB  134MB                   Microsoft reserved partition  msftres
 3      659MB   151GB  150GB   ntfs            Basic data partition          msftdata
 6      151GB   151GB  1049kB                                                bios_grub
 9      151GB   173GB  22.0GB  ext4
 7      173GB   480GB  307GB   ext4
 8      480GB   490GB  10.0GB  linux-swap(v1)
 4      490GB   490GB  472MB   ntfs                                          hidden, diag
 5      490GB   500GB  9922MB  ntfs                                          hidden, diag

---

### Post by oldfred on 2017-02-15
I always label partitions, but did you put a label in using non-ASCII chars?
I use plain text with no spaces. Also length may be limited.

You also show a bios_grub partition. 
That is only used for BIOS boot of Ubuntu. 
But you have ESP - efi system partition, so Windows is installed in UEFI boot mode.

UEFI & BIOS are not compatible, or once you start booting in one mode, you cannot switch. 
Or from grub menu, you can only dual boot systems in same boot mode.
Or with both BIOS & UEFI, you can only dual boot from UEFI boot menu.

---

### Post by eddugo on 2017-02-15
but did you put a label in using non-ASCII chars? -- No,  I didn't label anything. I think  this came from trying to install unrestricted extras from sofware center - it failed.  Tried to install flash player - installed, doesn't always work, installed gmail in online accounts - it froze and removed other accounts.  This strange behavior is why I thought I would reinstall correctly.  The extra GRUB was from when I tried to install before - haven't used it, starts just fine since you (Olfred) helped me with that a couple days ago.  I didn't label anything.  Here is the thread where you helped me with the boot; [https://ubuntuforums.org/showthread.php?t=2352271]("https://ubuntuforums.org/showthread.php?t=2352271")

---

### Post by oldfred on 2017-02-15
Post these
cat /etc/fstab
df -h

Is sda7 supposed to be /home, or did you want to use it for data like a /mnt/data.
New users often find the separate /home easier first step to separate data partitions as it is auto configured including mounting in /home and setting ownership & permissions. If you use a separate data partition you have to manually do those steps.

For new users, you should always install software from Ubuntu repository. 
I have never really used Software Center as it hides the actual program names. I use synaptic which is an old tool, or command line.
For example to install grub2 its program name is grub-pc for BIOS or grub-efi-amd64 for UEFI. I prefer to know exactly what I am installing.

---

### Post by eddugo on 2017-02-15
ed@Dell1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=41fe5333-f457-4119-87cd-1ba6c2a7f1f2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=713bc9fa-b2eb-4eaa-9c44-fab5d29dcd7c none            swap    sw              0       0
UUID=FCA3-F88C	/boot/efi	vfat	defaults	0	1



ed@Dell1:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           787M  9.9M  777M   2% /run
/dev/sda9        21G  6.7G   13G  36% /
tmpfs           3.9G  195M  3.7G   5% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1       495M   35M  461M   7% /boot/efi
tmpfs           787M  100K  787M   1% /run/user/1000
ed@Dell1:~$ 


When I partitioned my drive, I followed an online tutorial - I think it was from OMG UBUNTU as it did not show windows 10 so I selected "something else" and used the tutorial to make the partitions.  I am not sure where the data is stored - thought it was "home" and the part was big enough.  As you can see, I still am kinda green even though I am a 9 year user - never had much of a problem until now.  I have 3 other dul booted machines that are all perfect.

I am glad you use synaptic.  When I started Ubuntu, 7.04, that's all you got for software installs.  I quit using it because it no longer came with the OS.  I have it installed now as the only way I could install flash.  I like synaptic much better

---

### Post by oldfred on 2017-02-15
When you use Something Else and want a separate /home you have to select if existing or add another partition and choose /home.
If a re-install you still have to select (choose) the existing /home, but must NOT check the format or it will erase your data.

If you do not want to reinstall, you can move /home.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I normally have multiple / (root) partitions, to test another or next version of Ubuntu. But I may not want same /home that has all the settings. 
So I use a data partition and mount it inside every new install. Since I do that a lot I have scripted it.
But basically you have to create mount point like /mnt/data, add mount of data partition by UUID into fstab and link your typical /home folders from data partition into /home. Folders have to exist in data partition. And I reset owership & permissions of data partition to be same as a typical /home. I use same user in all installs, so no issues.

Details in these threads:
The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata) 

      [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 
    
If not in fstab yet, but unmount if adding to fstab or run chmod & chown after mount in fstab and copy of folders & files into data partition:
      sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data
 # Note that the -R is recursion and everything is changed, do NOT run on any system partitions.

---

### Post by eddugo on 2017-02-15
I guess what I should do is leave the home folder on a separate partition and learn how to link it.  SSID's are becoming popular and I will need to know this in the future.  I guess I will link and then reinstall to fix all the system problems I am experiencing.

Below is a quote from one of the links you gave me.  Is there still an easy way to link the home folder to a separate particion or do I have to do it in terminal.  

"Re: Splitting home directory
Move all data folders from the ssd to the hdd, and then create links to them in your home folder. Creating links is easy, just right click a folder and select 'Make link'.

Edit: If you find that the default directories are recreated on reboot, edit .config/user-dirs.dirs and comment them out.
Last edited by mikewhatever; July 24th, 2011 at 12:27 PM."


If I must do it in terminal, is this tutorial accurate for linking the drives or point me to a better one if possible?  My head is kind of spinning now. :-) [https://www.maketecheasier.com/move-home-folder-ubuntu/]("https://www.maketecheasier.com/move-home-folder-ubuntu/")

Thank you

Ed

---

### Post by oldfred on 2017-02-15
I have not had to edit .config/user-dirs.dirs, but that may be because I have all the normal folders in my /mnt/data and linked all of them.

But just the procedure I have in several of the links posted before.
But you just about have to use terminal.
Not really difficult to copy & paste. 

It was after I did it line by line with several new test installs, that I realized I could list history, copy history files into a bash file, some edits to clean up all the mistakes & remove sudo as not required. The with every new install I just run script & instantaneously my fstab is edited, & my links added.

---

### Post by eddugo on 2017-02-18
Got it running perfect!  Thank you Olfred,

---

