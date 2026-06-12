---
title: "Sharing a hard disk partition bewteen Ubuntu and windows XP pro"
date: 2005-11-01
forum: General Help
---

### Post by Inder on 2005-11-01
On my computer, I have an 80Go hard drive that I divided in 3 partitions (20Go NTFS, 20Go, 40Go) using the partitioning tool windows XP offers me during the installation.
I then installed windows on the first 20Go NTFS partition.
Next, I installed Ubuntu on the second 20Go partition using not NTFS but another file system, I dont remember what it was.

Now, I want to format my third partition (40Go) with a file system that can be used by both operating systems. I chose FAT32. But Windows doesnt let me format my partition in fat32. It only allows NTFS. I really dont know why. So my question is this: How can I format my third partition in fat32?
And once I get this done, will I be able to use this partition with both operating systems?
Ultimatly, I want to ditch windows completely, but Im not brave enough to do that just yet.

Taking it one step at a time,
Shawn

Thanks for any help.

---

### Post by Inder on 2005-11-02
Sorry, this is an error.

---

### Post by Inder on 2005-11-03
Apparently, noboy knows. Does anyone know where I could get an answer?

---

### Post by Nomad64 on 2005-11-03
I am not sure why Windows XP will not allow you to format in FAT32. Are you using the Disk Management tool (Right click on My Computer -> Manage -> Disk Management)?

Otherwise you can try using the "format" command in the command prompt for Windows...pretty sure there is a simular command for the Linux shell, but I don't know it off of the top of my head.

The above two are the easiest, but you should try to use a third-party formatting/partitioning tool if you have it. Ya know, something like Parition Magic.

---

### Post by aysiu on 2005-11-04
Can't you just use QTParted or GParted to make the FAT32 partition?

---

### Post by Qrk on 2005-11-04
Yeah, you can format the partition just fine in Ubuntu. Just 
 
sudo apt-get install gparted 

Or if you have a breezy live CD handy, you can load that up and do it there.

---

### Post by peanut butter on 2005-11-04
hmm im on xp now and i dontseem to have that problem

---

### Post by rajsarkar on 2005-11-04
Since you have installed Ubuntu already, I presume you have Ubuntu installation CD. Use the CD and enter into installation program. Format your 40 GB partition in FAT32. Once the formatting is done abort the installation using escape key. 

Then boot into Ubuntu and follow the guidelines provided in ubuntuguide.org to make the FAT32 partition to be usable both in Ubuntu and XP.

PS: always take backup before doing something new. You never know.......
Raj

---

### Post by corefile on 2005-11-04
actually the problem is that Windows XP has a limit for 32 gigs for fat32, the partition is 40 gigs which is why windows will only allow you to format it with NTFS, if it were 32 gig partition you would see the choice of fat32 when you try to format it in windows.

You can format it with Ubuntu, but not sure windows would see all 40 gigs.

---

### Post by StarFire on 2005-11-04
_Tip1:_ Use Qparted in Ubuntu
[INDENT]Program can resize / move / format partitions in several formats,including FAT32. 
However, in my opinion FAT32 is too unstable and maintenance unfriendly. You can add it to your [FONT=Verdana][COLOR=Green]Applications > System[/COLOR][/FONT] menu by simply choosing "Add Application" in your menu bar.
[/INDENT] [U]
Tip 2:[/U] Share NTSF partition with Ubuntu
[INDENT]There are a lot of forum threads about mounting NTSF partitions in Ubuntu (or Linux in general), none of which are *really* simple. But 5 minutes ago I found out something *really wonderfull.* :cool:
Open [COLOR=Green]System > Administration > Disks[/COLOR]. Select your NTSF partition. Select the Tab "Partition". Create [COLOR=SeaGreen]access path[/COLOR], e.g. /home/ntsf. Select <[COLOR=Navy]Enable[/COLOR]>. Now you will be able to open your partition from your home folder.
[/INDENT] 
Greetings,
 
[COLOR=Blue][COLOR=Red][COLOR=Orange]-=[/COLOR]S[/COLOR]tar[COLOR=Red]F[/COLOR]ire[COLOR=Orange]=-[/COLOR]

[SIZE=1][COLOR=DarkRed]Registered Linux User 401411[/COLOR][/SIZE]

[/COLOR]

---

### Post by shinygerbil on 2005-11-04
The trouble with NTFS partitions is that Linux can't write to them... :/

Steve

---

### Post by ofek on 2005-11-04
[QUOTE=corefile]actually the problem is that Windows XP has a limit for 32 gigs for fat32, the partition is 40 gigs which is why windows will only allow you to format it with NTFS, if it were 32 gig partition you would see the choice of fat32 when you try to format it in windows.

You can format it with Ubuntu, but not sure windows would see all 40 gigs.[/QUOTE]
Well u can always use partition magic on windows xp i just converted a 80gb hard disk from ntfs to fat32 so its possible and it works on xp and ubuntu and my gentoo system without any hassle.

---

### Post by mwolfe on 2005-11-04
i'm pretty sure that i formatted one of my drives fat32 to like 60 gb ( i think it was with partition magic).  I am not on my home computer right now to check, but i'll see later.. I thought i had heard about a 32gb limit though, maybe there is a way around it though somehow.. Also, i havent had any problems using fat32 with ubuntu and sharing files between ubuntu and windows. Previously i used to use an ntfs shared drive but i found it was very annoying to have to make copies of everything before i could change them.. and then i'd end up losing data if my linux installation crashed ( usually because i did something stupid).  

But anyways. you could try removing two of your partitions in the partition manager, then recreate them so that the one drive is less than 32 gb so you can have a fat32 drive.. I believe that will work in windows. (make sure you dont format them though if you have data on them obviously).

---

### Post by Inder on 2005-11-05
Thanks for all your replies. I got it formatted in "windows vfat" using linux. Now windows sees it as fat32 and can use it just fine. Problem is, I don't know how to get it with Linux.. Is it the access path or something like that? I put a .txt file in that part using windows, but I can't find it using Linux.

---

### Post by Inder on 2005-11-11
Maybe I didnt explain my problem very well.
My partition is formatted now. 40Go formatted in fat32. It works perfectly with windows: I open my explorer, go to my computer and there it is. When I click on it, it opens. But I dont know where to find this partition using Ubuntu. I go in Places. Then I click Computer. then File System There are a whole bunsh of folders there. Where is my 80Go partition..

Thanks for any help.

---

### Post by Irony on 2005-11-11
First make a folder (directory). I've called my folder *2nd* and put it in *mnt* folder. Then mount it. You can if you want then unmount it. When its mounted you can access it;

[I]sudo mkdir /mnt/2nd
sudo mount /dev/hdb1 /media/2nd/ -t vfat -o iocharset=utf8,umask=000
sudo umount /mnt/2nd[/I]

You can make this mount up on booting. I've already created the folder *2nd* so first back up your *fstab* file;

[I]sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab[/I]

Then edit your *fstab* file by adding this to it;

*/dev/hdb1       /media/2nd  vfat    iocharset=utf8,umask=000   0       0*

For your partition list type;

*sudo fdisk -l*

For more information see;

[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by Inder on 2005-11-11
Alright, perhaps I should have told you. I don't know anything about command lines and the such. I don't even know where to type what you said... Is there any way to do that using a graphic interface?

Thanks for your help though.

---

### Post by Irony on 2005-11-12
Has to be done in terminal. No graphical way.

The example is a nice way to start as its safe.

First find the terminal icon, I think its in Applications somewhere (I'm in another operating system at the moment). It looks like a little black TV.

Click on it.

Type;

*sudo fdisk -l*

Or copy and paste it from here. sudo means you become a superuser with root privileges.

*sudo gedit /etc/fstab*

Gedit is a text editor. By opening the fstab file in this manner you will be able to edit it. You can navigate to it graphically go to the etc folder then find fstab - when you click on it you will open it but won't be able to alter and save it... which is why you use the sudo command line interface.

Follow the previous instructions and watch as you magically create folders.

---

### Post by Inder on 2005-12-11
Alright, Im too much of a noob.
Ive tried doing what you said, but ran into a few problems.
1. Im able to make a new folder but Im not able to move it to /mnt
2. I dont know how to mount something.
3. When I write sudo gedit/etc/fstab it says:
command not found

Also, after trying a few things, I had this folder on my desk top which I am not able to get rid of.  It says: Cannot move "/home/shaw...ktop/part5" to the trash because you do not have permissions to change it or its parent folder.

Thanks for any further help.

---

### Post by Teedyo on 2005-12-11
OK now, don't get too frustrated....

Here's a step by step of how I would do it.  Everything in quotes is explicite: don't include the quotes.

1.  Applications > Accesories > Terminal
     to get a command prompt.

2.  At the prompt; enter: "sudo su"
     you'll get a password prompt.

3.  Enter *your* password at the prompt to get root access

4.  Enter "fdisk -l /dev/hda"  (I'm assuming that your partitions are on drive0)
     to list all of your partitions something like:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         257     2064321   83  HPFS/NTFS
/dev/hda2   *         258         322      522112+  83  Linux
/dev/hda3             323        2594    18249840   83  W95/FAT32

My list is different than yours will be obviously.  Whichever part lists the FAT32
is the one we're interested in.  Remember it or write it down.

5.  "cd /etc"
     moves you to the /etc directory

6.  "cp fstab fstab_bak"
     create a backup of your File System Table

7.  "mkdir /mnt/win32_share
     create a mount point for the partition

8.   "vim fstab"
      open your fstab for editing

9.  Move down to the last line of the file using the cursor keys.

10. Enter "o"   (that is a small o; not a zero)
     opens a new line in insert mode

11.  Enter "/dev/hda3    /mnt/win32_share   vfat   iocharset=utf8,umask=000   0   0"

12.  Enter ":wq"   (colonlittlewlittleq)
      writes the new line to the file and quits vim

13.  Enter "mount /dev/hda3"
     mounts the 3 third partition of the first hard drive according to the fstab
     which in this case is a fat32 partition mounted under /mnt/win32_share.

14.  Enter "exit" to leave root
14.  Enter "exit" again to close the terminal window.

The next time you reboot, this partition will be mounted automatically.
If the partition you have for sharing isn't /dev/hda3; substitute yours instead.

If the mount command returns an error of any sort; post it here and me or somebody, can fix our mistake(s).

You can work on removing that desktop link later after you make sure that 'part5'
doesn't contain anything important.

I know there was something else I was going to add but, that durn phone made
me lose my train of thought.

G'luck

---

### Post by aysiu on 2005-12-11
[QUOTE=Inder]
3. When I write sudo gedit/etc/fstab it says:
command not found[/QUOTE] I don't know if you realize it, but you have written ```
sudo gedit/etc/fstab
``` You should have written ```
sudo gedit /etc/fstab
``` See the difference?

---

### Post by Teedyo on 2005-12-11
[QUOTE=Inder]Alright, Im too much of a noob.
Ive tried doing what you said, but ran into a few problems.
1. Im able to make a new folder but Im not able to move it to /mnt[/QUOTE]

You need to have root privileges to write to /mnt.  Much better to create it under /mnt as root to begin with.

> 
2. I dont know how to mount something.

lol...  General options for mounting a partition from the command line:
mount -t fstype -o options /hwpartition /mountpoint
in the above example:
mount -t vfat -o iocharset=utf8,umask=000 /dev/hda3 /mnt/win32_share

See man mount for more information.

> 
3. When I write sudo gedit/etc/fstab it says:
command not found

That's because you apparently didn't leave a space between gedit and /etc/fstab.

> 
Also, after trying a few things, I had this folder on my desk top which I am not able to get rid of.  It says: Cannot move "/home/shaw...ktop/part5" to the trash because you do not have permissions to change it or its parent folder.

Thanks for any further help.

---

### Post by Robocoastie on 2005-12-12
[QUOTE=corefile]actually the problem is that Windows XP has a limit for 32 gigs for fat32, the partition is 40 gigs which is why windows will only allow you to format it with NTFS, if it were 32 gig partition you would see the choice of fat32 when you try to format it in windows.

You can format it with Ubuntu, but not sure windows would see all 40 gigs.[/QUOTE]

I don't think that's true. I have a Fat32 drive that's 80GB I've used for over a year. Course that's the whole drive though, I don't have it partitioned up any differently. Once I finally get a network - samba friendly printer though the drive will turn into a Reiser4 partition once and for all server style and be done with it.

---

### Post by Inder on 2005-12-13
[QUOTE=Teedyo]
4.  Enter "fdisk -l /dev/hda"  (I'm assuming that your partitions are on drive0)
     to list all of your partitions $%^%^UJL::{{something like:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         257     2064321   83  HPFS/NTFS
/dev/hda2   *         258         322      522112+  83  Linux
/dev/hda3             323        2594    18249840   83  W95/FAT32

My list is different than yours will be obviously.  Whichever part lists the FAT32
is the one we're interested in.  Remember it or write it down.
[/QUOTE]

I entered "fdisk -| /dev/hda".
It says:

Unable to open -
bash: /dev/hda: Permission denied


What am I doing wrong. Maybe my partitions are not on drive0... How would I know that.

---

### Post by sudokubuntu on 2005-12-14
[QUOTE=Inder]I entered "fdisk -| /dev/hda".
It says:

Unable to open -
bash: /dev/hda: Permission denied
[/QUOTE]

Hmm... maybe "sudo fdisk - /dev/hda"?

or you can just write "sudo fdisk -l" to view the partition table
(I think it's called that. I'm a nOOb too  :D   )

sudo is what you must write in front of commands to get the right rights (sometimes)

---

### Post by everard on 2005-12-14
NTFS is the newest windows harddisk format. Windows always recommends the latest that's why windows xp cannot format one of the partition to FAT32. You can use a windows 98 startup disk to format it to FAT32. There is no problem for windows xp to use a FAT32 format partition but in Ubuntu... I don't know.

---

### Post by Inder on 2005-12-14
When I type fdisk - /dev/hda, I get this:
> 
Usage: fdisk  [-b SSZ] [-u] DISK       Change partition table
            fdisk -l [-b SSZ] [/-u] DISK    List partition table(s)
            fdisk -s PARTITION                 Give partition size(s) in blocks
            fdick -v                                  Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


when I write fdisk -s /dev/hda it says
"78150744"
when I write cd/etc it says
"bash: cd/etc: No such file or directory"

What do I do now.

Maybe it would be simpler if someone could sit down with me on MSN and walk me through it.... just a thought.
Anyhow, thanks for the help, Ill get there one day or another :)

---

### Post by aysiu on 2005-12-14
```
sudo fdisk -l
``` is the command you want.

---

### Post by ember on 2005-12-14
I throw in another idea:

Format the partition with ext2 - there is a Windows driver for Ext2 called Ext2-IFS, available at [http://www.fs-driver.org]("http://www.fs-driver.org") - it has some known flaws (no utf-8 support, no way to work out linux-permissions correctly (new files just inherit the permissions of their parent folder), but it works much faster on linux and windows than fat32.

---

### Post by RAOF on 2005-12-14
[QUOTE=ember]I throw in another idea:

Format the partition with ext2 - there is a Windows driver for Ext2 called Ext2-IFS, available at [http://www.fs-driver.org]("http://www.fs-driver.org") - it has some known flaws (no utf-8 support, no way to work out linux-permissions correctly (new files just inherit the permissions of their parent folder), but it works much faster on linux and windows than fat32.[/QUOTE]
In fact, I'd suggest formatting it ext3 instead.  It has the same on-disc format, so the windows ext2 driver will be able to read/write it just fine, and under linux you'll get the crash-stability of the ext3 journalling.

---

### Post by ember on 2005-12-14
Hmm ... maybe that breaks journalling?

---

### Post by RAOF on 2005-12-14
I don't think so, no.  The windows writes will obviously not get journalled, but I think the journal on a properly unmounted partition should be empty, anyway.

---

### Post by neymac on 2005-12-15
[QUOTE=StarFire]_Tip1:_ Use Qparted in Ubuntu
[INDENT]Program can resize / move / format partitions in several formats,including FAT32. 
However, in my opinion FAT32 is too unstable and maintenance unfriendly. You can add it to your [FONT=Verdana][COLOR=Green]Applications > System[/COLOR][/FONT] menu by simply choosing "Add Application" in your menu bar.
[/INDENT] [U]
Tip 2:[/U] Share NTSF partition with Ubuntu
[INDENT]There are a lot of forum threads about mounting NTSF partitions in Ubuntu (or Linux in general), none of which are *really* simple. But 5 minutes ago I found out something *really wonderfull.* :cool:
Open [COLOR=Green]System > Administration > Disks[/COLOR]. Select your NTSF partition. Select the Tab "Partition". Create [COLOR=SeaGreen]access path[/COLOR], e.g. /home/ntsf. Select <[COLOR=Navy]Enable[/COLOR]>. Now you will be able to open your partition from your home folder.
[/INDENT] 
Greetings,
 
[COLOR=Blue][COLOR=Red][COLOR=Orange]-=[/COLOR]S[/COLOR]tar[COLOR=Red]F[/COLOR]ire[COLOR=Orange]=-[/COLOR]

[SIZE=1][COLOR=DarkRed]Registered Linux User 401411[/COLOR][/SIZE]

[/COLOR][/QUOTE]

And can you write to this NTFS partition as well from Ubuntu?

---

### Post by psusi on 2005-12-15
WinXP can format and use fat32 partitions just fine.  So can Ubuntu.  Because of this it makes a good choice for sharing files between the two.  

Ubuntu can read NTFS partitions, but not write to them.  


Ubuntu can read and write to a UDF filesystem.  Windows at least can read UDF because it is used on DVDs.  I wonder if windows can read/write a UDF filesystem on a hard disk?  Might be worth checking out.  The nice thing about UDF is that it stores proper unix file permissions.  

The easiest thing though is just to stick with fat32 for the shared partition.

---

### Post by Inder on 2005-12-15
I tried fdisk -| but it doesnt give me what you said it would.
And then cd /etc  and  cd/etc dont work. So basically Im stuck again.

---

### Post by RAOF on 2005-12-15
The command is not
```
fdisk -|
```
it is
```
fdisk -l
```
That's a letter "l" as in "letter", rather than (what gets called) a pipe '|' character, which you'll find above the backslash.

---

### Post by Inder on 2005-12-18
oh my god, what a stupid mistake !
Thanks, I'll try it again later tonight :)

---

### Post by earobinson on 2005-12-18
Just checking we (as a community) still dont know how/cant do it on ext3?

---

### Post by Inder on 2005-12-27
Hello, I did what you said, but at one point, it stopped reacting, I would press enter and it would simply go to the next line...
Here is a screenshot...
[http://www.angelfire.com/blog/shawninder/images/Screenshot.png](http://www.angelfire.com/blog/shawninder/images/Screenshot.png)

As you see I replaced hda3 by hda5, because this is the one where I saw W95 FAT16(LBA)
Here is the full thing:
/dev/hda5      4463   9728   42299113+   e   W95 FAT16 (LBA)


Care to help me some more, I ask.
Thanks you.

---

### Post by State on 2005-12-28
There is a Windowsdriver for accessing ext2 Partitions:
[http://fs-driver.org/](http://fs-driver.org/)

Just make your homepartition or sharingpartition ext2 and you can write and read it under windows.

Never had problems with this driver

---

### Post by RAOF on 2005-12-28
Format it ext3 instead.  You'll get a better filesystem in linux, and from the fs-driver page above:
> 

Does the Ext2 driver access Ext3 volumes, too?

The Ext3 file system is the Ext2 file system which has been extended by journaling. Ext3 is backward-compatible to Ext2 - an Ext3 volume can be mounted and used as an Ext2 volume. Just as older Linux Kernels which do not know the Ext3 file system can mount Ext3 volumes (as Ext2 volumes), the Ext2 file system driver ext2fs.sys for Windows incorporated in this software package can do it without any problems, too. Of course you do not take advantage of the journaling of the Ext3 file system if you mount it as an Ext2 file system. 


---

