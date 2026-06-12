---
title: "[SOLVED] File system check failed"
date: 2008-02-06
forum: General Help
---

### Post by jeffsa12 on 2008-02-06
Hello Ubuntu Community, This is my first post so please be gentle!!!

I'll get this out of the way first...., I'm a Newbie Linux and Ubuntu user. I've been distro hopping and  selected Ubuntu as "my favorite linux"  after trying several other distros. I've played around with Windows for several years and thought I actually knew something until I started playing around with Linux. So far, I've shunned learning command line code.  I realize now that if I knew some basics, I could probably bail myself out with this problem!!! So far, I've gotten away with just copy and pasting code from the forums without actually learning much of it.  

Everything has been great until tonight, I switched to pulse audio packages using synaptic from the repositories. I removed the ESD package same time as adding the pulse packages. I got an error pop up box...something about network....before synaptic finished with the install. After the files were loaded and synaptic updated, things were not right with my main menu, missing apps, etc, so I rebooted....or tried.......Also ktorrent was uploading files in the background when this happened and I don't know if this was possibly a problem. I also have several deb packages installed that were not in the Ubuntu repositories, but as I said, everything has been running smooth until this last change. 

Upon rebooting, I now get:   *File system check failed. A log is being saved in /var/log/fsck/checkfs if ...........ets, etc...............    *A maintenance shell will now............etc,etc........

My Ubuntu 7.10 is installed on the second hard drive. My two hard drives have 10 partitions on hda, 9 on hdb. I have one win xp on each, along with 3 different linux os's. Ubuntu root is hdb7, Ubuntu home is hdb8, hdb9 and 10 are used for media, uncompressed torrent files, deb packages, etc.

I can boot windows and Mint....have not tried the others. I have used different installed Linux distros in the past to get into and change things in a broken one....instead of using the “dreaded shell.” I'm just not sure what or how to fix it this time.

I am usually successful finding what I need for info with Ubuntu...but this one has some conflicting info out there such as running fsck when mounted on the partition being checked. 

Thanks in advance for any help with this problem!!!

Jeff

---

### Post by kpkeerthi on 2008-02-06
OK... Did you check what is in /var/log/fsck/checkfs? Boot with recovery mode (from GRUB) if need be.

---

### Post by jeffsa12 on 2008-02-06
This is theUbuntu  /var/log/fsck/checkfs file, accessed from within PCLinux OS. 



Log of fsck -C -R -A -a 
Tue Feb  5 23:05:47 2008

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda2: 2309 files, 697004/785638 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb5: 8183 files, 585214/1066271 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda5: 15168 files, 1184077/1966036 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda2: 2309 files, 697004/785638 clusters
Mint home: clean, 6098/932064 files, 651637/1861524 blocks
Ubuntu home: clean, 7183/932064 files, 1646787/1861524 blocks (check in 2 mounts)
Replaying journal..
Replaying journal..
Reiserfs journal '/dev/hda7' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..Reiserfs journal '/dev/hdb10' in blocks [18..8211]: 0 transactions replayed
finished
PClinOS_root: Reiserfs super block in block 16 on 0x307 of format 3.6 with standard journal
Blocks (total/free): 1861520/1319240 by 4096 bytes
Filesystem is clean
Replaying journal..
Checking internal tree..finished
OSues home: Reiserfs super block in block 16 on 0x34a of format 3.6 with standard journal
Blocks (total/free): 1861520/1490400 by 4096 bytes
Filesystem is clean
Reiserfs journal '/dev/hda8' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
PClinOS_home: Reiserfs super block in block 16 on 0x308 of format 3.6 with standard journal
Blocks (total/free): 1861520/1847488 by 4096 bytes
Filesystem is clean
Replaying journal..
Reiserfs journal '/dev/hda9' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Mint root: Reiserfs super block in block 16 on 0x309 of format 3.6 with standard journal
Blocks (total/free): 1861520/1322151 by 4096 bytes
Filesystem is clean
Failed to open the device 'UUID=e4297032-2dd4-6a12-1689-4f4d2da27bd8': No such file or directory


PClinOS_root: Reiserfs super block in block 16 on 0x307 of format 3.6 with standard journal
Blocks (total/free): 1861520/1319240 by 4096 bytes
Filesystem is clean
OSues home: Reiserfs super block in block 16 on 0x34a of format 3.6 with standard journal
Blocks (total/free): 1861520/1490400 by 4096 bytes
Filesystem is clean
fsck died with exit status 8

Tue Feb  5 23:06:01 2008
----------------

---

### Post by jeffsa12 on 2008-02-07
Any one able to help me out here.  
 
I just had Ubuntu set up to do everything XP would do plus a LOT MORE before I broke it!!!.....I miss my UBUNTU!!! 

Any tips on how to troubleshoot or where to go for info on this problem would be greatly appreciated.....

Thanks.....
Jeff

---

### Post by kpkeerthi on 2008-02-07
> My two hard drives have 10 partitions on hda, 9 on hdb.
What does your ubuntu's /etc/fstab look like? Do you have all these 19 partitions mounted in ubuntu? Can you post the output of ```
cat /etc/fstab
``` ?

---

### Post by jeffsa12 on 2008-02-07
Thank you kpkeerthi for your help. Here is my /etc/fstab file.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb7
UUID=0ae53440-032d-4ef9-8da5-fd16ba7e5b75 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb8
UUID=56cd59e5-df83-4215-9495-1181314a8a57 /home           ext3    defaults        0       2
# /dev/hda1
UUID=0CBC286ABC28510E /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda10
UUID=696b0a2a-a9ec-4dae-99d0-165cb70c18b2 /media/hda10    ext3    defaults        0       2
# /dev/hda2
UUID=1759-73DC  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=9BC4-852A  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=425897de-16c0-4518-b91c-1ac901b28b47 /media/hda7     reiserfs defaults        0       2
# /dev/hda8
UUID=843b84d1-55ee-44bb-a3ca-4b3431f06f37 /media/hda8     reiserfs defaults        0       2
# /dev/hda9
UUID=96ec1acb-8934-4422-a66f-322ae0c60037 /media/hda9     reiserfs defaults        0       2
# /dev/hdb1
UUID=14ACC584ACC5613A /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb10
UUID=c0059448-fb19-87ee-df6f-5de78f890346 /media/hdb10    reiserfs defaults        0       2
# /dev/hdb2
UUID=1759-73DC  /media/hdb2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=140F-A8DB  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb9
UUID=e4297032-2dd4-6a12-1689-4f4d2da27bd8 /media/hdb9     reiserfs defaults        0       2
# /dev/hda6
UUID=4640b5ac-0f7f-4488-9bec-a65daa8f3d79 none            swap    sw              0       0
# /dev/hdb6
UUID=5d07c577-1b2a-4508-9e2f-42f0f3529f30 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by jeffsa12 on 2008-02-07
Well actually, I see now I incorrectly posted the details regarding my partitions. I have 2 HD's. 

hda or 1  has the following partitions:
1
2
( skips.....no # 3,4)
5
6
7
8
9
10

hdb or 2  has the following partitions:
1
2
( skips.....no # 3,4)
5
6
7
8
9
10

So i actually have 16 total partitions and 22GB unallocated space on hda.
I have 2 swap partitions and know this is unnessary, but all the Linux seem ok with it.....Is this a potential problem? My thoughts on having 2 swaps were if I remove 1 HD, i still have a Linux swap.

I am new to linux, and currently am more comfortable using Acronis in WinXP to manipulate or create new partitions. Old habits hard to break!! I have used gparted? during the install of a few dostros to creare partitions, but started creating the partitions prior to install to ease my worries of screwing my HD up during the installs.

You asked about all partitions mounted in Ububtu.....I believe it by default auto mounts all available linux partitions. Please correct me if im wrong on this. Before I set up my desktop, it was quite full of partition shortcut icons.

Now that I pretty much have my Os's narrowed down to one WinXP, and  Ubuntu on two different computers, I could consolidate several partitions into larger ones. I would however like to have two Linux os's per computer just for the convenience of fixing problems.

---

### Post by jeffsa12 on 2008-02-07
more info:

When I loaded Ubuntu on this computer, I had to use the all_generic_ide-- workaround  to get the live CD to run, and to the OS after I installed to the HD.

When I boot now, if I Ctrl-D after the error message, it goes to the log in screen, If I log in,  I get  to a blank tan screen. The mouse cursor moves, but that's the only function working.

Anyone with ideas or input?

---

### Post by jeffsa12 on 2008-02-07
Would it make sense to just reload Ubuntu and start over? I will do that if this problem has no easy fix or if there is no practical  trouble shooting process to try.

I would like to learn a better way of dealing with problems with Linux than just reloading.....although I have resorted to that several times. 

Any input would be greatly appreciated!!!

---

### Post by Herman on 2008-02-07
:) Hello jeffsa12,
I would suggest that you try booting a Ubuntu Live CD and get a list of your hard drive's file system UUID numbers with the following command,
```
ls /dev/disk/by-uuid/ -alh
```Use the following link for an example of how to gain access to your hard disk installed Ubuntu's /etc/fstab file, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD.

Then, referring to the following link, make sure the file system UUID numbers your computer currently has, match the UUID numbers for the file systems in your /etc/fstab file. [About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with").

If you need any more help or there is something you're not sure about  just ask.

Regards, Herman :)

---

### Post by jeffsa12 on 2008-02-07
Thanks Herman. I used the instructions to get a list of the HD UUID numbers.  The list was quite long, and was  longer than what was viewable on my monitor. I was however,  able to get the numbers for:

/dev/hdb7:Label =" Ubuntu root" UUID = "0ae53440-032d-4ef9-8da5-fd16ba7e5b75" SEC_YPE "ext2" TYPE = "ext3"

/bev/hdb8: LABEL = "Ubuntu home" UUID = 56cd59e5-df83-4215-9495-1181314a8a57" SEC_YPE"ext2" TYPE"ext3"

I had to right this down as I don't know how to print or copy and paste to something accessible from a graphical environment. 

I then looked at the /etc/fstab file and the numbers all match.

The line below from the ** /etc/fstab** file draw my attention.

# /dev/hdb7
UUID=0ae53440-032d-4ef9-8da5-fd16ba7e5b75 / ext3 defaults,errors=remount-ro 0 1

and the below from the** /var/log/fsck/checkfs** file

Failed to open the device 'UUID=e4297032-2dd4-6a12-1689-4f4d2da27bd8': No such file or directory

---

### Post by Herman on 2008-02-07
:)
```
 Failed to open the device 'UUID=e4297032-2dd4-6a12-1689-4f4d2da27bd8': No such file or directory
``` If you take another look in your /etc/fstab file you should see
  ```
# /dev/hdb9
UUID=e4297032-2dd4-6a12-1689-4f4d2da27bd8 /media/hdb9     reiserfs defaults        0       2
```Check to see which UUID number your /media/hdb9 has with the  'ls /dev/disk/by-uuid/ -alh' command output and replace the out of date number 'e4297032-2dd4-6a12-1689-4f4d2da27bd8' with the current number for whatever file system you have in /dev/hdb9 now, if it's another reiserfs file system.
>  I then looked at the /etc/fstab file and the numbers all match.If you have deleted your /media/hdb9 partition then you won't see it in your list of UUID numbers.
If that's the case then just hash it out or delete the entry for it from your /etc/fstab file so that Ubuntu won't look for it at boot-up time.
Or maybe you made some other file system in /dev/hdb9? If that's what happened then it's up to you if you want an entry for it in /etc/fstab. If you then it will be automatically mounted on each boot-up. 

The other thing you can do is to run a better file system check to fix your file systems. 
You can run a better file system check in each partition with GParted. Just boot your Ubuntu Live CD and open GParted Partition Editor. 'System'-->'Administration'-->'Partition Editor'.
Simply right-click on the partition you want a file system check run in and click  'Apply' on the toolbar and 'Apply' in the  confirmation box, and wait a few minutes.
Click on the triangular button to expand the information box to show you what has been done.

If it's for a reiserfs file system you might still need to use some more commands from the commmand line, try having a look in this link,  [         Running a filesystem check on a reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_on_a_reiserfs").

Regards, Herman :)

---

### Post by Herman on 2008-02-07
>  I had to right this down as I don't know how to print or copy and paste to something accessible from a graphical environment. Well you don't have to write anything down, I'll let you in on a few simple tips and tricks.
First, look down in the bottom left-hand corner of your monitor, and see on the bottom panel, (Windows users call that a taskbar I think), there are two small rectangles there? You can click on those to open another workspace. It's called a 'workspace switcher'.   Right-click on it and click 'preferences' and set the number of workspaces up to eight or twelve or something like that. Some people only use four, I like twelve.

Now you can have a terminal open in one Desktop (workspace) and click on another workspace to switch to that one.
Open another terminal in the other workspace and open another terminal in that Desktop.
Now you can open your /etc/fstab file in one Desktop and use your other terminal in your other Desktop for your list of partitions and file system UUID numbers.

Simply copy any of your  UUID numbers (if you need to), and click on the other Desktop to go to it. 
Then highlight the UUID number that's wrong, and paste the new number over it.

---

### Post by jeffsa12 on 2008-02-08
Thanks again Herman and kpkeerthi....you walked me the through troubleshooting and fixing of the boot hang up problem. Getting into this problem, and the fix makes me realize what caused the problem and it wasn't changing packages. It was most likely caused by me formatting an old OS partition from reiserfs to ext3 using acronis in windows. Next time, I'll use a linux partitioning tool from Ubuntu. Possibly the problem didn't surface immediately, because of a scheduled partition check by Ubuntu, that just happened to run after I rebooted for the problem related to changing the sound packages.





Now I don't know if I should start a new thread for this unrelated problem. This one may have been caused by changing the sound packages. I'll explain in detail whats going on in steps.

Start up computer
Boots into acronis OS detector
Select Linux OS....Ubuntu 7.10 in this case
Loads grub boot loader
Select Ubuntu kernal2.6---etc--etc
Loads Ubuntu log in screen
Log in
Loads to a blank tan screen. 

Tan is not my desktop wallpaper colour. It's not the default wavy dark brown wallpaper either. The mouse cursor moves around, but no other mouse or keyboard input has any effect except the ctrl+alt+backspace kills X normally, returning to the log in screen.

I have on board ATI 200 express graphics in this one and use the fglrx ATI driver. It seems as though the problem may not be X related....I have always had a dark, blank screen or a visible screen with 600x800 resolution setting when X settings or the driver has had problems. 

I'll copy and paste a bit of details from my earlier post as to what I was doing when this problem developed in case this post gets moved to a new thread.

I switched to pulse audio packages using synaptic from the repositories. I removed the ESD package same time as adding the pulse packages. I got an error pop up box...something about network....before synaptic finished with the install. After the files were loaded and synaptic updated, things were not right with my main menu, missing apps, etc, so I rebooted....or tried.......Also ktorrent was uploading files in the background when this happened and I don't know if this was possibly a problem. I also have several deb packages installed that were not in the Ubuntu repositories, but as I said, everything has been running smooth until this last change.

The non repository deb packages I have loaded are, a stand alone version of Krita, Nero linux, Acetone ISO, flash 9.0.115, grub editor, xorg-edit, Ubuntu tweak.

---

### Post by Herman on 2008-02-09
[**Log into a blank tan desktop**]("http://ubuntuforums.org/showthread.php?t=691570")
I'm happy to see that you did start a new thread already, that's outside my area of expertise, and hopefully you'll attract someone who knows about that with your new thread.
Good luck with it,
Regards, Herman :)

---

