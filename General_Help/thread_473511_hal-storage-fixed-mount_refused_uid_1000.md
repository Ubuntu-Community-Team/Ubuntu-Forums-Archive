---
title: "hal-storage-fixed-mount refused uid 1000"
date: 2007-06-14
forum: General Help
---

### Post by pardesi on 2007-06-14
i have ubuntu 7.04 and can acess al my drives in it .i loaded kde-core yesterday and there when i click on the storage media except my root directory /sda 8 i am unable to view any and it gives the following reply
```
hal-storage-fixed-mount refused uid 1000
```
i posted thsi before but no reply (i didn't post it this neatly)

---

### Post by HotShotDJ on 2007-06-14
Well... lets start simple and work our way up.  Open Konqueror, click "Home Folder" -- if the navigation panel isn't there, press F9 while konqueror is the active window.  In the navigation panel, click the little blue flag to open up the services tree :shock:

Oh... SCREW ALL THAT!  Konqueror is a LAME file manager. ](*,)  Open a terminal and apt-get install dolphin (another backport from KDE 4!).  Once installed, it will be in Kmenu --> System.  Open Dolphin, click Storage Media.  What is in there?

---

### Post by pardesi on 2007-06-14
so just wait a minute before i install dolphin

---

### Post by pardesi on 2007-06-14
same result no change:(

---

### Post by HotShotDJ on 2007-06-14
Ok.  What partitions (/dev/sda?) are we trying to look at?  Also, post your /etc/fstab -- that might come in handy.

---

### Post by pardesi on 2007-06-14
/sda 1,/sda 5,/sda 6,/sda 7
```
/etc/fstab
``` gives permission denied
```
sudo /etc/fstab
``` 
gives
```
sudo: /etc/fstab: command not found
```

---

### Post by HotShotDJ on 2007-06-14
Oh... sorry... I figured you knew what I meant when I asked for your /etc/fstab. :)  Its a text file. At a terminal, type ```
kdesu kate /etc/fstab
``` Paste the contents of the file and post.

While your at it... tell me what each of those partitions are (example, sda1 = Windows, sda2 = Music)

---

### Post by pardesi on 2007-06-14
nothing i don't remember division like that everything is there in everything i don't see any sda 1... in ubuntu it is disk,disk 1.....equiv to C,D,E,F drives in windows thats all

```
pardesi@pardesi-desktop:~$ kdesu kate /etc/fstab
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
DCOP Cleaning up dead connections.
QFile::open: No file name specified

```

---

### Post by HotShotDJ on 2007-06-14
Argh... oh well -- we'll worry about that some other time.  Open dolphin.  In the tool bar just below "File Edit View" etc, etc ... hit the up arrow icon until you can't anymore.  Then find "etc" and click it to open, then find "fstab" and click it to open.  Post the contents.

---

### Post by pardesi on 2007-06-14
when i open fstab thsi comes i want my default session to be GNOME what to do....

---

### Post by HotShotDJ on 2007-06-14
:shock:

Now I just don't have ANY clue whats going on.  I'm wondering if these problems are an artifact of having KDE installed on top of Ubuntu rather than with Kubuntu.  I've never seen such ill manners from KDE on any of my installs.  At this point, close any open applications and restart X (Ctrl+Alt+Backspace) and then start Gnome.  At least that should get you to a stable desktop.  Then, go to Synaptic and see if kubuntu-desktop is installed.  Don't do anything with it yet... just check and see.

WAIT!! STOP!!! I KNOW WHAT THAT WAS!!!  Let me know if I edited in time!

---

### Post by pardesi on 2007-06-14
hey wait i never installed kubuntu-desktop i just installed kde-core ....:p

---

### Post by HotShotDJ on 2007-06-14
> **pardesi said:**
> hey wait i never installed kubuntu-desktop i just installed kde-core ....:p](*,) (NOW he tells me)  LOL!  We'll get back to THAT too! :)

---

### Post by pardesi on 2007-06-14
well anyways here is the output of ifstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=3c47f43b-c71f-4744-a755-84af4bb1b9ea /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=4442ecec-3931-4c9c-8585-5ffa86c722a2 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by pardesi on 2007-06-14
> **HotShotDJ said:**
> ](*,) (NOW he tells me)  LOL!  We'll get back to THAT too! :)
:mrgreen:

---

### Post by HotShotDJ on 2007-06-14
Yep.. that explains why you only see /dev/sda8  -- Now I just need to figure out what to do about those other partitions.    I KNOW... in a terminal, type ```
sudo cfdisk /dev/sda
``` and post the output.  Make sure to select QUIT in cfdisk after you get the output!  Be careful, we don't want to mess up anything!

---

### Post by pardesi on 2007-06-14
```
                 cfdisk 2.12r

                              Disk Drive: /dev/sda
                       Size: 160041885696 bytes, 160.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 19457

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        Boot        Primary   W95 FAT32 (LBA)                  20971.57*
                            Pri/Log   Free Space                           0.04*
    sda5        NC          Logical   NTFS             []              24200.01*
                            Logical   Free Space                           1.65*
    sda8        Boot        Logical   Linux ext3                       21977.95
    sda9                    Logical   Linux swap / Solaris              1003.49
    sda6        NC          Logical   NTFS             []              24201.00*
                            Logical   Free Space                       22979.21*
    sda7        NC          Logical   NTFS             []              22864.88*
                            Pri/Log   Free Space                       21839.53*


     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition


```

---

### Post by HotShotDJ on 2007-06-14
Good GOD, pardesi, that is the most BIZARRE partitioning scheme I've ever seen.  Oh well... no matter.... let me digest all this information and see if I can fix things up.  It should be fine.... stand by.

---

### Post by pardesi on 2007-06-14
i am really satisfied with GNOME and think it's more like 'me' than KDE do  u think this is worth taking the risk:(

---

### Post by HotShotDJ on 2007-06-14
Ok... FIRST  run the following commands -- one line at a time... be careful... we don't want any typos
```
sudo mkdir /mnt/win_c
sudo mkdir /mnt/win_d
sudo mkdir /mnt/win_e
sudo mkdir /mnt/win_f
```
Stand by for next instructions...

---

### Post by HotShotDJ on 2007-06-14
> **pardesi said:**
>  do  u think this is worth taking the risk:( I assure you, I have no intention of taking any risks with your system. :)

---

### Post by pardesi on 2007-06-14
done and thanks

---

### Post by HotShotDJ on 2007-06-14
Here is the fun part. :)   FIRST, and most importantly, run the following command:
```
sudo cp /etc/fstab /etc/fstab.orig
```
This is so we can restore if things don't go as planned!

Now, save the attached file in your home directory.
After it is saved, fun the following (make proper change for your home directory!)
```
sudo cp /home/pardesi/fstab.pardesi /etc/fstab
```
Let me know when this is done... hopefully error free.

Hmmm... where did the attachment go????????

---

### Post by pardesi on 2007-06-14
u there can u be a bit fast i have other assignments......

---

### Post by HotShotDJ on 2007-06-14
DAMN.... ok... I'll do it this way instead...  untar and proceed as described above.

---

### Post by HotShotDJ on 2007-06-14
> **pardesi said:**
> u there can u be a bit fast i have other assignments......You can have it right, or you can have it fast. ;)   Seriously, we should be done now.  If all goes with no errors, reboot, start up KDE and see if you can see the drives.  If there is a problem, we'll restore the original fstab and try again some other day.

---

### Post by pardesi on 2007-06-14
well thanks for your valuable time which i suppose i wasted even mine but due to serious fear of losing out my computer which i use for my studies without whch i can't study seriously i neede to remove the eye candy kde-core:(:(:(:(:(
just that i don't like eye candies except when they are in the form of.......as i had said before also GNOME had everything good in it that i wanted also i have no time to set things right if something goes wrong..

again i thank u for your valuable time and expertise i seriously didn't deserve that though...:(:(

---

### Post by HotShotDJ on 2007-06-14
Well... the work is done and the proper fstab file is there if you want to access those drives.

---

### Post by KhaaL on 2007-09-13
Hey guys

I also had this problem (with ntfs3g), but it was solved by unchecking "mount as a user" in the device properties in dolphin (should prolly work in konq too).

---

### Post by leon_mcnichols on 2007-10-10
leonardo@Hal:~$ kdesu kate /ect/fstab
Error: "/var/tmp/kdecache-leonardo" is owned by uid 1000 instead of uid 0. And this is becuase I installed a 4.3 gig as a slave and refuses to mount.

Anyone got a fix for this ?

---

### Post by gtrman79 on 2007-10-11
I have this same exact error when I try to access or mount my partitions.  I just installed Kubuntu.  It's weird because one of my partitions has a USB icon next to it in my explorer window.  I am really just trying to access my windows partition (NTFS) to move some music and pics around.  I know with Ubuntu I had no problems.  I was just trying Kubuntu out.  I am new to all of this.  Any ideas?

---

### Post by leon_mcnichols on 2007-10-11
Yea its definitely odd.  I'm running KU 7.10 and only thing broke is the Kmail otherwise the whole thing works great save for mounting that stoooopid 4.3 hdd ...

---

### Post by johnbuck on 2007-10-20
> **KhaaL said:**
> Hey guys

I also had this problem (with ntfs3g), but it was solved by unchecking "mount as a user" in the device properties in dolphin (should prolly work in konq too).

Thanks Khaal, you method works. My is a USB harddisk, I right click on the USB hardisk icon in dophin, select property, Mounting tab, unselect mount as user.

---

### Post by GrantShoe on 2007-10-20
> **HotShotDJ said:**
> Well... the work is done and the proper fstab file is there if you want to access those drives.

AHhhh you just saved me about 100 hours of frustration!

---

### Post by krak on 2007-10-22
@HotShotDJ grate job ! nice howto!
:-({|=

---

### Post by fsanders on 2007-10-22
> **KhaaL said:**
> Hey guys

I also had this problem (with ntfs3g), but it was solved by unchecking "mount as a user" in the device properties in dolphin (should prolly work in konq too).

Thanks Khaal!  Your fix worked perfectly for me in Gutsy!

---

### Post by rmeu on 2007-10-22
I think you are quite lucky.
I've done exactly the same (checking/unckecking "mount as user"). 
But ... to no avail.

I dropped a look inside the KSystemLog but found nothing of interrest.
A fault in the "hald" configuration? The new nt3gfs driver?:confused:

Somebody have good idea?
Well, maybe I should go to define those partitions inside fstab.

Rmeu.

PS: For info, this a fresh  7.10 installation. Not an upgrade from 7.04.

---

### Post by Buelldozer on 2007-10-22
This seems to be a fairly common problem. I'm seeing reports of it all over the net.I'm so disappointed, I never had this problem with Feisty.

Mounting a removable drive I can almost understand but refusing to mount a fixed-disk partition is almost inexcusable.

Yet, here it is happening to me. I have a vfat partition on my laptops hard drive and it refuses to automount for me. No problem mounting my NTFS Vista partition though! 

Soooo weird.

---

### Post by jmikeh on 2007-10-27
> **johnbuck said:**
> Thanks Khaal, you method works. My is a USB harddisk, I right click on the USB hardisk icon in dophin, select property, Mounting tab, unselect mount as user.

You guys rock.  Disabling mount as user worked on my external hdd as well.

---

### Post by guidryp on 2007-10-27
Argh. I am in the club now too, with the same error message when I try to mount sda5 (Kubuntu 7.10) I am about to give up on Linux forever. This is the third time I tried it (first was slackware in the 90's) It was looking good for a while but I had to reinstall after messing up my video really bad trying to get dual monitors working...

Before reinstall I could see my media disk, but after I can't.  I can see my bootable NTFS partition no problem, but the big one now won't mount. Dolphin, unchecking "mount as user" doesn't help. I see no real difference between the two NTFS partitions in fstab.

```
 
                          cfdisk (util-linux-ng 2.13)

                              Disk Drive: /dev/sda
                       Size: 500107862016 bytes, 500.1 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 60801

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        Boot        Primary   NTFS             []              32719.17*
                            Pri/Log   Free Space                           1.00*
    sda5                    Logical   NTFS             [3]            441212.25
    sda6                    Logical   Linux ext3                       24026.05
    sda7                    Logical   Linux swap / Solaris              2146.80




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a5075a9c-779c-4334-84ad-11fd6582d4e5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2CD44F71D44F3C78 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=5BEEC9A67A5535DB /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=73e576a9-8b02-4399-ac32-24b79497f680 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



```

EDIT:    "sudo mount /dev/sda5 /media/sda5" works but an auto solution would be nice...

---

### Post by database_dan on 2007-10-28
FINALLY! HERE IS THE FIX!!!

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Enjoy your partitions peoples!
~Dan:guitar:

---

### Post by guidryp on 2007-10-28
That doesn't appear to be a solution, it seems to be pre 7.10 info about how to setup what is automatically already present in 7.10.

7.10 does auto-mount partitions AFAIK. It all worked on my first install and stopped working on a reinstall.

The info is already in fstab. The problem is one NTFS partion is fine, The other not when I can't see any difference between them in the config files. To add to my info on the previous page, I just tried pmount and mount -a on sda5:

```

guidryp@guidryp-desktop:~$ sudo fdisk -l
[sudo] password for guidryp:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7e61057

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3978    31952278+   7  HPFS/NTFS
/dev/sda2            3979       60801   456430747+   5  Extended
/dev/sda5            3979       57619   430871301    7  HPFS/NTFS
/dev/sda6           57620       60540    23462901   83  Linux
/dev/sda7           60541       60801     2096451   82  Linux swap / Solaris
guidryp@guidryp-desktop:~$ pmount /dev/sda5
**Error: device /dev/sda5 is not removable**
guidryp@guidryp-desktop:~$ sudo mount -a
**Failed to access '/dev/disk/by-uuid/5BEEC9A67A5535DB': No such file or directory**



```

---

### Post by guidryp on 2007-10-28
**I think I found the problem.** Posting before I reboot:

fstab entry:

# /dev/sda5
UUID=5BEEC9A67A5535DB /media/sda5     ntfs    defaults,umask=007,gid=46 0       1


The Unique ID reported by vol_id:

sudo vol_id -u /dev/sda5
ACC41132C410FFEE


My theory is somehow after reinstall,upgrades, the old UID is getting into fstab. Obvious change is to put the correct uid in fstab.

Time to reboot...

edit:
**Success. Fixed.**

There may be more than one issue at work. Hopefully this will help others. Just check that your vol_id matches what is in fstab and you may be golden. 

Next hurdle. Realtek s/pdif output...

---

### Post by database_dan on 2007-10-28
> **guidryp said:**
> That doesn't appear to be a solution, it seems to be pre 7.10 info about how to setup what is automatically already present in 7.10.

7.10 does auto-mount partitions AFAIK. It all worked on my first install and stopped working on a reinstall...


sounds like its different for everyone. i am on kubuntu 7.10 and that solution worked for me...even though its an older script.

---

### Post by guidryp on 2007-10-28
> **database_dan said:**
> sounds like its different for everyone. i am on kubuntu 7.10 and that solution worked for me...even though its an older script.

It is possible it would have worked for me, but I didn't try it, because it said to use it if you didn't have entries in fstab. Which I did. 

The script must re-write fstab, which then corrected the problem for you and probably would have worked for me as well. But hey, I learned something figuring out what was wrong.

Good news is we now have two solutions. Using that script to re-write fstab, or fixing the one broken UUID like I did.

Cheers. I just got s/pdif out working (sort of). Yipee... I think Linux might finally be good enough for me. 

:guitar:

---

### Post by curVV on 2007-12-06
Hi, I'm having the same problem with a SATA internal drive /dev/sda1. It is not listed in fstab, so I cannot correct the ID. How do i fix this please anyone?

---

### Post by database_dan on 2007-12-06
> **curVV said:**
> Hi, I'm having the same problem with a SATA internal drive /dev/sda1. It is not listed in fstab, so I cannot correct the ID. How do i fix this please anyone?

[https://help.ubuntu.com/community/Au...ountPartitions](https://help.ubuntu.com/community/Au...ountPartitions)

---

### Post by curVV on 2007-12-07
Ah thanks, man :)

---

### Post by outferno on 2008-01-30
> **guidryp said:**
> **I think I found the problem.** Posting before I reboot:

fstab entry:

# /dev/sda5
UUID=5BEEC9A67A5535DB /media/sda5     ntfs    defaults,umask=007,gid=46 0       1


The Unique ID reported by vol_id:

sudo vol_id -u /dev/sda5
ACC41132C410FFEE


My theory is somehow after reinstall,upgrades, the old UID is getting into fstab. Obvious change is to put the correct uid in fstab.

Time to reboot...

edit:
**Success. Fixed.**

There may be more than one issue at work. Hopefully this will help others. Just check that your vol_id matches what is in fstab and you may be golden. 

Next hurdle. Realtek s/pdif output...

This worked for me - I had to find out the volume id since I made the partition after I installed Ubuntu parallel to Windows XP.  Then I created an NTFS partition and it would not auto mount.

I then edited the file systems table, as suggested, with the correct UUID.

Then I saved and typed "sudo mount -a" and it worked.  Then I got the error that I couldn't save bookmarks, but you can use this link to resolve that:

[http://www.linuxforums.org/forum/ubuntu-help/108515-unable-save-bookmarks-dolphin.html](http://www.linuxforums.org/forum/ubuntu-help/108515-unable-save-bookmarks-dolphin.html)

---

### Post by lakedude on 2008-02-22
> **database_dan said:**
> [https://help.ubuntu.com/community/Au...ountPartitions](https://help.ubuntu.com/community/Au...ountPartitions)
Hi this is my first post on this board.

I'm trying to use Kubuntu 7.10 as a live CD and I get the error "hal storage fixed mount refused uid 999".  I tried to go to the link in the quote but it comes up

> Au...ountPartitions
 
 
This page does not exist yet. You can create a new empty page, or use one of the page templates. Before creating the page, please check if a similar page already exists. I've got Sata and Pata drives from 74GB to 500GB and all have the same error message in Konqueror and Dolphin.

Please help!

---

### Post by database_dan on 2008-02-22
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by knic on 2008-03-11
> **johnbuck said:**
> Thanks Khaal, you method works. My is a USB harddisk, I right click on the USB hardisk icon in dophin, select property, Mounting tab, unselect mount as user.

thanks a lot, this also helped me to solve my ntfs datas usb drive access. cheers

---

### Post by HotCocoa on 2008-03-27
OK, ](*,) I am very annoyed now.  I am getting the same error with ext3, so that wiki guide does not apply.  What the heck is up with my drives?!!?!?!?

---

### Post by jakerman999 on 2008-04-19
hello all, i recently stared using Kubuntu, and i was trying to transfer some files from my old windows machine onto this one.  my computers teacher said I could set my old hard drive as a slave and copy the files in through the directories( he is also a linux user, but I'm not sure how well he knows it).  i got it hooked up, and i have tried using both dolphin and Konqueror to read it.  I have tried putting it on 3 different IDE possibility's, and it keeps giving me the same result.

 hal-storage-fixed-mount refused uid 1000

I googled this error and came to this page.  deselecting mount as user doesn't work, and neither does force mount.  I'm not sure what the stuff inside the code boxes was(new user) and i didn't want to do something in the wrong order.

could this be caused by the secondary drive being windows?  If anyone has any speculation on this it would be very much appreciated.

---

