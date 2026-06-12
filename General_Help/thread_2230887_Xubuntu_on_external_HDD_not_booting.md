---
title: "Xubuntu on external HDD not booting"
date: 2014-06-21
forum: General Help
---

### Post by ibexslam on 2014-06-21
I've just installed xubuntu 14.04 from a flash drive to an external hard drive. The installation stopped due to a crash on the first attempt, then the second go 'round, wiping out and replacing the contents of the external drive, seemed to go OK.

But when I tried to boot from the drive, after making it past the grub screen, I got this:

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait long enough?)
- check root: (did the system wait for the right device?)
- Missing modules (cat /proc/modules: is /dev)

ALERT! /dev/disk/by-uuid/fdSb07ad-8Se7-4ca2-e2?6-1i86ebd7a9a0 does not exist.
Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:i.21.0-iubuntui) built-in shell (ash)
Enter ‘help’ for a list of built-in commands.

(initramfs) _

...and everything stopped at that point.

Should I reformat the drive and start over? Is that likely to fix this? Maybe it's something else? I'm not knowledgeable enough to know what those messages are trying to tell me.

Any advice will be greatly appreciated. 

I.

---

### Post by nerdtron on 2014-06-22
Try reinstalling again. I think you have installed grub on the wrong drive or something. To be sure, remove the internal hard drives if possible so that you will see only a single drive on the Ubuntu installer.

Regarding your error. It seems that fstab is trying to mount you hard drives and partitions on bootup. That is the UUID of the hard drive it tries to mount. Since it can't find that drive, Ubuntu won't continue to mount.

---

### Post by Bashing-om on 2014-06-22
ibexslam; Hi !

The boot process is a particular interest of mine. I suspect that the boot manager grub ( GRand Unified Bootloader) is not installed to that external drive.
Rather than (re-)installing the Operating System, how about we try and fix the problem by properly installing grub where it needs to be ?
Provide to us the output - Between Code Tags -  of the terminal commands:
```

sudo fdisk -lu
sudo parted -l 

``` to show the present partitioning and format.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once these conditions are known we can consider the means to proceed.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-06-22
As both posts above discuss, any of the auto install options install the grub2 boot loader to the MBR of the sda drive which usually is the internal drive not they external drive. But the only install option which gives a choice on where to install grub is Something Else.

We also see issues with default installs to external USB drives where a large / (root) is not correctly seen. If drive is over 120GB that could also be the issue. Better then to use Something Else and choose a / of 25GB at beginning of drive and use rest of drive as /home or data or shared data with your internal system.

And you may need to reinstall the correct boot loader to sda. 

       Install to external drive. Also any second drive. Several similar examples:
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by ibexslam on 2014-06-22
Hi, folks!

I did disconnect my internal hard drive (which has "7" on it--no UEFI) first and I used the default (not "something else") option. The external drive is bigger than 120 GB--it's 500 GB. So, maybe the installer wanted to install Grub on the disconnected drive and failed at that. I had assumed that would be handled properly by the installer.

Here's the output from those terminal commands. At the moment, my internal hard drive (the Hitachi) is reconnected. The Kingston is my "live" usb flash drive. The Toshiba is the new external drive, the install destination. 

```

xubuntu@xubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   949650344   474825141    7  HPFS/NTFS/exFAT
/dev/sda3       949650345   976768064    13558860    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 15.6 GB, 15610576896 bytes
255 heads, 63 sectors/track, 1897 cylinders, total 30489408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001893d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    30475304    15237621    b  W95 FAT32

Disk /dev/sdg: 500.1 GB, 500107859968 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1d1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *        2048   964454399   482226176   83  Linux
/dev/sdg2       964456446   976771071     6157313    5  Extended
/dev/sdg5       964456448   976771071     6157312   82  Linux swap / Solaris

xubuntu@xubuntu:~$ sudo parted -l

Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  486GB  486GB   primary  ntfs         boot
 3      486GB   500GB  13.9GB  primary  ntfs

Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  15.6GB  15.6GB  primary  fat32        boot

Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdg: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  494GB  494GB   primary   ext4            boot
 2      494GB   500GB  6305MB  extended
 5      494GB   500GB  6305MB  logical   linux-swap(v1)

```

I had considered using the "something else" option, but I thought the default would be much easier. So much for that notion! I've been doing this for a while, but I still feel like a noob. 

So, unpartition/wipe ext. HDD, reinstall with "something else"? I'm a bit lost regarding the options, with that.

I.

---

### Post by oldfred on 2014-06-22
Since install is small, you can quickly test if size of partition is the issue. Use gparted on live installer and just shrink sdg1 to 25GB. It may then boot, although a reinstall of grub sometimes is needed. If not then that is probably not issue.

While you could add partitions and manually edit it may just then be easier to reinstall.

If only having Ubuntu on drive, I now prefer gpt partitioning. But you have to choose that before anything else in gparted. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....            GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

My suggestions, but others may be better depending on how you use system.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
[*]all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by ibexslam on 2014-06-22
Hi, Fred!

That's very helpful, thank you, though a little overwhelming for me. Let me ask you this, for future readers of this thread (and for myself): if a somewhat-noob were to say to you, "I want to install (x)ubuntu onto an external hard drive, what would be the simplest way to accomplish that, and what would the steps be?", what would you tell that person?

I.

---

### Post by oldfred on 2014-06-22
The Something Else install option assumes a lot of basic Linux & system info that many Windows users do not know. Even Windows confuses drives & partitions as a d: drive in Windows could be sda2 or sdb1. Where in Linux sda is first drive and sdb second drive. And number after drive is partition number.

You have to know what partitions and what partitions and formats you need or want.
The links in post #4 walk you thru the install steps. While similar, reviewing each should be all that is really required.

It does look like this is the only one that includes a separate /home.
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
Older one, so graphics are different colors, but steps are the same.
 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

But partitioning is actually very personal. Standard type install but with the extra partition for /home should be ok for most new users, but many may want shared NTFS, extra partitions for data or systems or other uses. 

Some info on partitioning in this as it goes thru creating them with gparted.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
And this which also is above.
      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by ibexslam on 2014-06-22
I'll give it a shot. Thanks, Fred. I'll let you know how it works out.

I.

---

### Post by ibexslam on 2014-06-22
:icon_frown:

I wiped out all the individual bits on the external drive with gparted. Started within Xubuntu, by the way, using the terminal and typing "sudo gparted".

Gparted is tricky. You have to be persistent about deleting the various partitions after a failed install.

All that stuff at about the BusyBox...I think that was a red herring, and was not the real problem. 

I found these instructions helpful, though they don't directly apply to installing with the primary hard drive disconnected.
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)

At Installation Type, after choosing Something Else, I see that the external drive is specified as the Device for Boot Loader Installation.

I clicked on Free Space, then the +, and the Create Partition window popped up. Clicking "New Partition Table" didn't do anything.

I chose 25600 MB (= 25GB) for the size and for Mount Point, selected "/", leaving other selections as is.

Then I selected Free Space again, pressed the +, and on this Create Partition window I entered 12288 MB for the size (= 2 x 6GB (RAM)) and chose Use As: Swap Area.

In my case, putting /home on a separate partition is not a priority for me right now, so I did not to anything special about that. I usually have at least two login accounts, each with its own home (of course), so that could get gnarly. Keeping it simple for now.

After returning to the main Installation Type window, I changed Device for Boot Loader Installation to sdb1, as opposed to the original sdb.

Then I clicked the Install button, and continued with the remaining screens about language, location, names and so on.

After finishing, I restarted, selecting the new external drive from the Boot Menu (Esc on my HP machine).

I now have a black screen with nothing on it, same as before.

[bad word]!

What did I do wrong? Should I have not changed the Device for Boot Loader Installation? Something else? Do I have a bad external drive?

You should see the looks I'm getting from my friends who use those other operating systems. 

Any suggestions? I'm lost.

I.

---

### Post by ibexslam on 2014-06-22
Redoing, using sdb as the Device for Boot Loader Installation, doesn't change things. Black screen again.

---

### Post by Bashing-om on 2014-06-22
ibexslam; Hey,

Still hang'n with the 2 of you.
This:
> 
After returning to the main Installation Type window, I changed Device for Boot Loader Installation to sdb1, as opposed to the original sdb.

Is perhaps an error; unless required otherwise grub should be installed to 'sdb' (MBR), so;
Install grub to the MBR (sdb) rather than to the partition (sdb1).

Booting to a black screen may also be a graphics driver issue. For now let's see about getting the boot code located to the MBR, see how that effects the situation.
From the liveDVD, boot to a terminal and execute terminal commands:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

```
Where 'sdb1' is the location of the root directory containing the final stages of the boot code and 'sdb' is the target where we want the initial stages of the boot code written to.
Reboot now into the install.
If you now boot up into the install, verify/recheck grub:
```

sudo grub-install --recheck /dev/sdb
sudo update-grub

``` this also will pick up and chainload the OS on drive sda.

[INDENT][INDENT]fingers crossed,
[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-06-22
ibexslam; Well !


> 
Redoing, using sdb as the Device for Boot Loader Installation, doesn't change things. Black screen again.


Let's say this is a graphics driver issue.
Boot to the grub boot menu, 'e' key for edit mode -> boot parameters screen, arrow down and across to the terms 'quiet splash' and replace these terms with 'text' with out the quotes. Key combo ctl+x to continue the boot process to a textual terminal interface (TTY1).

If you can login here and enter your password ( no result to the screen for security reasons) then we know the system is installed and most likely now have a graphics driver issue to deal with.

[INDENT][INDENT]if not one thing
[INDENT][INDENT][INDENT]something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-22
Uh-oh. I don't have a grub boot menu. Nothing at all comes up, after the BIOS device selection.

I.

---

### Post by Bashing-om on 2014-06-22
ibexslaml Well, maybe

In bios, set the 1st boot priority to that 2nd hard drive; continue to boot.
As soon as the bios screen clears, depress and hold the right shift key. The grub boot menu ( if exist ) should then appear.

[INDENT][INDENT]hope hope hope
[/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-22
Yes...right shift brought up the grub menu. Proceeding from there...

---

### Post by ibexslam on 2014-06-22
Top left blinking cursor...then Alert! Looks the same as what I posted up top./

/dev/disk/by-uuid/[string of numbers representing drive] does not exist.

Going to try again, and follow your instructions this time!

---

### Post by ibexslam on 2014-06-22
"quiet splash" replaced with "text"...
ending with the same Alert!, stopping with the (initramfs) prompt.

---

### Post by ibexslam on 2014-06-22
"quiet splash" replaced with "text"...
ending with the same Alert!, stopping with the (initramfs) prompt.

---

### Post by ibexslam on 2014-06-22
Sorry...quick reply is acting funny.

---

### Post by Bashing-om on 2014-06-22
ibexslam; yuk.

Back to grub boot error notifications.
OK .. your post #5 shows the external drive as device sdg ! .. and device sdb as the small booting thumb drive, no ?

We need to rerun the 'parted -l ' command and verify what drive is what and adjust the grub install routine to reflect what is truth. That we want grub installed onto the MBR of 'sdg' .. yes ? or whatever the external drive has as a disk identifier. Else, now then 'sdg' as the identifier can and will change in accord with what is attached to the buss and in what order the system recognizes devices , such that the external drive may no longer hold the designator 'sdg'. We Must install grub to the proper drive.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-06-22
I am not sure this applies to external drives:

 ALERT! /dev/disk ... does not exist." error
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"
Also check that drive is hd1 and grub in same drive.

Usually AHCI is preferred.

Some have also in grub boot stanza changed the device entries. If your flash drive used as installer was sdb and external drive was sdg. But then rebooting external drive becomes sdb grub has gotten confused. 
It can be difficult to explain but manually booting or editing boot stanza may work.

Also reinstalling grub sometimes works or booting with Supergrub and reinstalling inside your install works.

Possible entries or similar changes you can do to current boot stanza. If external becomes hd1 or sdb, not sdg.
You can also comment out the search line but then the set root- must be your drive, partition and root= has to be how Ubuntu sees drive like /dev/sdb1. 

      
 set prefix=(hd1,1)/boot/grub
set root=(hd1,1)
linux (hd1,1)/vmlinuz root=/dev/sdb1 ro
initrd (hd1,1)/initrd.img

Instead of text use nomodeset or other video boot options. What video card/chip do you have.

      
 
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

     
    
      
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by ibexslam on 2014-06-22
Now that I've got my C drive disconnected again, here's what parted -l reports:

```

xubuntu@xubuntu:~$ sudo parted -l
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sda: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  15.6GB  15.6GB  primary  fat32        boot

Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  479GB  479GB   primary   ext4            boot
 2      479GB   500GB  21.3GB  extended
 5      479GB   500GB  21.3GB  logical   linux-swap(v1)

```

---

### Post by ibexslam on 2014-06-23
Changing "quiet splash" to "nomodeset" results in the same Alert! as before.

---

### Post by Bashing-om on 2014-06-23
ibexslam; OK,

Now, with out changing anything such that 'sda' remains as the thumb drive ( Kingston DataTraveler ) and 'sdb' remains as the target 500 gig ( TOSHIBA External USB ) drive , re-run the grub install commands as give in post #12:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

``` Where grub is to be installed onto the hard drive known to the system as 'sdb'.

reboot, setting in bios to boot from that external hard drive, at this time what results ? 
If you now boot, we still need to re-confirm after the internal drive is connected ...

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-06-23
I thought we were installing with a smaller / (root) partition as that is one of the major reasons for your Alert type grub cannot find files issues. 

And now external is sdb. So all  the entries in your grub boot stanza refer to wrong drive. The search by UUID is supposed to override that issue but when default drive is so far off like your install to sdg then search also seems to fail. I had same issue when installing from one flash drive to another. I just had to change the hd4,1 to hd2,1 or whatever the correct settings should be. And comment out search line and change set root = /dev/sdg1 to sdb1.

---

### Post by ibexslam on 2014-06-23
Bashing,

On rebooting I get a grub screen that says "Minimal BASH-like line editing is supported..." ending with a grub> _   prompt.

---

### Post by ibexslam on 2014-06-23
Fred,

I'm sorry, I don't know what a stanza is, or how to make those changes you're suggesting. I can start over from scratch again and do it "right" this time. Am I doing something out of the ordinary with this install, or is there something peculiar about my devices? 

Even though I'm not installed yet, I do appreciate the help you folks have been throwing my way.

I.

---

### Post by Bashing-om on 2014-06-23
ibexslam; Yuk !

OK, I have in mind to try and boot the system from that grub > prompt .

We need to know what the system is aware of at this time.

what returns from grub terminal commands:
```

ls -la
ls -la (hd1,msdos1)/vmlinuz
ls -la (hd1,msdos1)/boot/grub/grub.cfg
search -f /sbin/init
set

```
And I will set us up a boot sequence.

That is my thoughts as I am a hands on type of mentality. Find the problem and fix it. But it is a lot of typing on your part.

[INDENT][INDENT]no quit in my nature
[/INDENT][/INDENT]

Once booted into the operating system, I think we should purge and (re-)install grub from within.

---

### Post by ibexslam on 2014-06-23
You're right about the typing! Trying to quickly do some photo > OCR...

---

### Post by Bashing-om on 2014-06-23
ibexslam; Yeah !

However you are able to work it out ...

It is passing midnight my time, and I am about past thinkability, So if I do not get right back with you -> I will on my morrow.

[INDENT][INDENT] ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-23
grub> ls -la
Device hd0: No known filesystem detected - Sector size 5128 - Total size

488386581.5KiB
Partition hd0.msdos5: No known filesystem detected - Partition start at

46?598336KiB &#8212; Total size 20787200KiB

Partition hd0,msdos1: Filesystem type ext* - Last modification time
2014-06-23 01:19:02 Honday. UUID 217ed9a7-cl1a-4:32-8c05-992e8c8932b6 -
Partition start at 1021KiB - Total size 467S96Z88KiB
Device hdl: No known filesystem detected - Sector size 5128 - Total size

15244703.5KiB
Partition hd1,msdos1: Filesystem type fat. UUID 1705-9019 - Partition

start at 31.SKiB - Total size 15237621KiB

grub> ls -la (hd1,msdos1)/vmlinuz
error: file '/vmlinuz' not found

grub> ls -la (hd1,msdos1)/boot/grub/grub.cfg

grub> search -f /sbin/init
hd0,msdos1

grub> set
?=0
cmdpath=(hd0)
color_highlight=black/light-gray
color_nornal=light-gray/black
feature_200_final=y
feature_all_video_module=y
feature_chainloader_bpb=y
feature_default_font_path=y
feature_menuentry_id=y
feature_menuentry_options=y
feature_nativedisk_cmd=y
feature_ntldr=y
feature_platforn_search_hint=9
feature_timeout_style=9
grub_cpu=i386
grub_platform=pc
lang=
locale_dir=
pager=
prefix=(hd0,msdos1)/grub
root=hd0,msdos1
secondary_locale_dir=

OK, I think that's it.

I.

---

### Post by ibexslam on 2014-06-23
I hear you, Bash, about it being late. I'd like to get this behind me, of course, but it's not "mission critical." Thanks for your assistance this evening!

I.

---

### Post by Patricia_Konarski_ on 2014-06-23
Ibexslam, I wish I could do more than what OldFred has said.  I would suggest reviewing, once more, his suggestions in his last post.  All the best.

Patricia Konarski Tucson
--Freelance editor and owner of Patricia Konarski Literary Services of Tucson

---

### Post by Bashing-om on 2014-06-23
ibexslam; Yuk on that output !

> 
grub> ls -la
Device hd0: No known filesystem detected - Sector size 5128 - Total size

where 'hd0' is grub speak for the 1st hard drive the system designates as 'sda' ... so I must ask " where is the world is that external hard drive " ?
A sector size of 5128, now that is a real odd number in my mind .
> 
15244703.5KiB
Partition hd1,msdos1: Filesystem type fat. UUID 1705-9019 - Partition


'hd1' in grub speak is 'sdb' but with a Windows file system where I had expected to see a linux file system - ext4 -, but but I know from prior outputs that the target disk does contain the ext4 filesystem, and the partitions for 'buntu's operating system ... sheeshh .. what is going on here ?? 
-- Gotta be that this is the thumb drive formatted as 'fat', but that is 'sda' ! /// sheesshh.

> 
grub> search -f /sbin/init
hd0,msdos1
 huh ??? There is a linux file on the 1st hard drive; Why is there no file found on the external drive ? Something stinks real bad right now ...!!

> 
prefix=(hd0,msdos1)/grub
root=hd0,msdos1
secondary_locale_dir=
 HUH ?? same same !! what in the world is grub associating ubuntu's boot code doing on that 1st hard drive, rather then onto the external drive ??

My poor mind can not fathom what is going on here presently .. I am going to sleep on it .. perhaps in the meantime others can weigh in here and try and make out what is going on !

Maybe it is time to backup, regroup and see if the system is installed from a full change root before we do anything  else ??
---------------------------------
Even if I take it that the thumb drive is not plugged in here, that does not explain the references to 'hd1' !

Maybe best explained as my wires are crossed expecting the external drive to still be hd1 ??
Maybe try this again on the morrow with the thumb drive removed and then see if the system sees that external drive as 'sda', and grub maps as 'hd0' ??

Hey it is a thought !

[INDENT][INDENT]But will need to wait 'till I can think clearer
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-06-23
Lets plug everything in and from live installer run BootInfo report. Post link it gives you so we can see all the details of your install. 

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You may need both edit of boot stanza or full grub uninstall or reinstall. Often Boot-Repair correctly reinstalls if you tell it external drive is external.

You probably need nomodeset or other boot parameters if you get black screen to temporarily resolve video issue.

---

### Post by Bashing-om on 2014-06-23
ibexslam; Morning !

+1 to the guru's recommendation of a boot-repair report. The report will disclose full details and we take this matter up once more.

Because
[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-23
The Boot Repair URL is [http://paste.ubuntu.com/7691285/](http://paste.ubuntu.com/7691285/)

Very handy!

I.

---

### Post by Bashing-om on 2014-06-23
ibexslam; 

Look'n.

[INDENT][INDENT]be back shortly
[/INDENT][/INDENT]

EDIT: I am back after my looksee at the boot-repair report.

There are 2 things that draw my attention. Let's let oldfred have the time to look at the report before I voice my concerns.
Else these, I do not see why it does not boot, it appears the files required are in place and the UUIDs match.

I do take a back seat to greater experience

---

### Post by oldfred on 2014-06-23
Oldfred's old eyes do not see everything, always better to have several reviews.

It does look like one of the systems that promotes the flash drive to sda or first drive, where most systems make it last.

UUIDs & everything do look correct, but it seems to have the possibly related error where it does not 'see' the boot files on the drive. See line 456. I have seen systems work when that is not shown but may be related to issue.

I would still shrink sdb1 to 25GB with gparted from live installer and reinstall grub2 using Boot-Repair. If that works then we can make the rest of the drive as /home or data partition(s).

---

### Post by Bashing-om on 2014-06-23
@ oldfred; My reasons for hesitation:
> 
 sda1/boot/grub/grub.cfg: ->
        insmod efi_gop
	insmod efi_uga
<snip>
menuentry "Try Xubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.[color=red]efi[/color]  
 is this standard OR are we looking at bios set to boot in efi mode where the ubuntu drive is MBR ? Setting up to boot EFI mode ??

I also made note that from line 456 there were no grub files detected.
Also noteworthy, an older version of grub is being installed into release 14.04, but I would think grub version 1.99 should still boot up 14.04 ??? Yes ?

All I know to do at this point is to boot back to the grub prompt and ask grub what it does see. Then with only the external drive connected (usb thumb drive not plugged in thus out of the equation) // see if we can boot the system. At that point I should expect the external drive to be assigned as 'sda' and that grub maps it as 'hd0' and we should be able to boot as (hd0,msdos1).

I am most assuredly willing to learn better.

What do yall think ?
[INDENT][INDENT][INDENT]if at 1st you do not succeed;
[INDENT][INDENT][INDENT][INDENT]try try again ( sky diving excepted)
[/INDENT][/INDENT][/INDENT][/INDENT] [/INDENT][/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-23
I've shrunk sdb1 to 25 GB. I clicked "Recommended repair" on Boot Repair, which did its thing and gave me [http://paste.ubuntu.com/7691764/](http://paste.ubuntu.com/7691764/) .

Then I rebooted with the live usb removed (and also with it in place on another try) and selected the external drive to boot from. 
Got a normal grub screen, selected Ubuntu. Blinking cursor in upper left...

[very bad word]

Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/[numbers] does not exist. (initramfs) prompt.    ](*,)

I.

---

### Post by Bashing-om on 2014-06-23
ibexslam; Yukkie once more.

Doing all things right, and still appears that /boot/grub/grub.cfg is not being parsed !
- normal.mod loads the grub.cfg file and executes the statements, usually providing a menu to the user etc. - so that begs the question as to why it is not completing. 
I be look'n at the new report, see what I can make of it.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-06-23
Bootinfo script is not updated. I just ran it and have both 12.04 and 14.04 grub versions in different MBR and it is reporting the same version of grub for both. But 14.04 is using grub 2.02.

When you reboot is flash drive still plugged in and you choose the drive or do you unplug flash drive as that then changes drive order. Flash drive is showing as sda or in grub hd0. And then install is hd1 or sdb. But if you unplug flash drive order will probably change and all the references to sdb should be sda and all references to hd1 should be hd0.

Also with just one system, you will not get grub menu unless you hold shift key from BIOS boot. And with nVidia (older) you have to add nomodeset to get system to boot.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ibexslam on 2014-06-23
Same results with flash drive plugged in and not plugged in.

I'll try again with no flash drive, right shift after bios, quiet splash replaced with nomodeset.

Result: same Alert! as before, (initramfs) prompt. 

Defenestration in 3...2...1...

I.

---

### Post by Bashing-om on 2014-06-23
ibexslam; Sheessshhh !

I am all for trying to install once more grub from the liveUSB.
Check setting in bios to boot in non efi mode.

Once grub is re-installed then;
Reboot into the install with that liveUSB not connected, see what then results;
 and if booting to the 'grub >' prompt try once more to boot the operating system from that 'grub >' prompt. Once we are able to boot into the install, then I would suggest we purge grub and (re-)install grub from within the install// remind me to make sure we have a working wired internet connection to do this!, else it is sure to fail with no means to access the software repository .

Maybe best to also await and see what oldfred has to advise, his experience runs very deep.

[INDENT][INDENT]it is an ill wind the
[INDENT][INDENT]blows nobody any good
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-06-23
Are you holding shift key from BIOS until grub menu appears? 
I believe error is after grub menu. And at grub menu you need nomodeset but maybe some manual boot commands.

---

### Post by ibexslam on 2014-06-23
BIOS, shift key, yes.
Nomodeset, yes.

Instead of trying to fix whatever it is that needs to be fixed, is there a way to work around this? Other than trashing Ubuntu and using Windows instead, which, at this point, is the only thing I can think of that will let me get back to work. Three days of this! I'm ready to throw in the towel.

I truly admire your persistence and helpful attitude, Oldfred and Bashing-om. I appreciate all your hard work on this.

I.

---

### Post by Bashing-om on 2014-06-23
ibexslam; How 'bout;

Boot to the grub boot menu -> and let's try and boot to a textual terminal in an attempt to isolate the problem.
Try: replace the terms "quiet splash" with "text" - with out the quotes - 
Do you now boot to TTY1 ?
If so, we can rule out a grub problem.

[INDENT][INDENT]more than one path to an end
[/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-23
BIOS, right shift key...Grub menu, E for edit, changed "quiet splash" to "text" (no quotes).
Ctrl-X. Lines of text roll by. 

Don't know what TTY1 is.

Same Alert! as before, ending at (initramfs) prompt again. 

I.

---

### Post by oldfred on 2014-06-23
At grub menu does second entry give same error? That should say recovery.

We will be hear as long as you want (off and on). 

But sometimes just a new install works. Do you have good backups?

---

### Post by ibexslam on 2014-06-23
> **oldfred said:**
> At grub menu does second entry give same error? That should say recovery.

I can give that a shot.

> But sometimes just a new install works. Do you have good backups?

Do you mean, of my primary, currently disconnected Windows drive? I'm sorry, but I'm not letting this thing anywhere near that, backups or no. The version of Ubuntu I've been using is 10.04, before they got rid of Gnome 2, and I'm running that off an external drive. I had no problems when I installed that four years ago. It doesn't work right any more...probably incompatibilities with Flash. Ugh. I have serious reservations about doing anything that will make that worse instead of better. 

About to try Grub/recovery.

---

### Post by ibexslam on 2014-06-23
"Grub loading."

"Recovery" mode selected.

Lines of text.

Same Alert! as before.

---

### Post by ibexslam on 2014-06-23
Should I use a different flash drive? Use a live CD instead? Get a different external drive? Switch to a different distro? Sacrifice a chicken? Is the installer the problem? Am I clicking on the wrong thing somewhere along the line? This is going to drive me nuts. 

I.

---

### Post by oldfred on 2014-06-23
When you press e on grub menu for first line this is what you see:

```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-217ed9a7-e11a-4e32-8c05-992e8c8932b6' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  217ed9a7-e11a-4e32-8c05-992e8c8932b6
    else
      search --no-floppy --fs-uuid --set=root 217ed9a7-e11a-4e32-8c05-992e8c8932b6
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
```

Change it to this, you can leave in the insmod lines, but totally delete all of the if thru fi section:

      set root=(hd1,1)
linux /vmlinuz root=/dev/sdb1 ro nomodeset
initrd /initrd.img                                                                                                                                    

And if that does not work try with (hd0,1) and sda1 on linux line.

---

### Post by ibexslam on 2014-06-24
Edited as you suggested.

Ctrl-X. Then...black screen...stays that way. 

Retrying with other options...

Ctrl-X. Text scrolls by. 

ALERT!  /dev/sda1 does not exist.

---

### Post by oldfred on 2014-06-24
Did you include nomodeset when you got the black screen. That is typical of video issue needing nomodeset or other boot option.

But I am to the point that you need either a full chroot and reinstall of many internals or an over install to refresh system.

To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php...2&postcount=10]("http://ubuntuforums.org/showpost.php?p=8068512&postcount=10")
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Once you correctly chroot, all text after a # is a comment, do not type:

      
 #houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

update-initramfs 				

Or:
 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by ibexslam on 2014-06-24
Nomodeset, yes, exactly as you'd indicated.

I'm happy to nuke my external drive and start over fresh. But I don't know what I did wrong that I should do right. 

I don't understand...I am but a humble end user, not a technology professional. Is all of this "normal" for an install to an external drive, with the C: drive disconnected? I've done it before without problems. What do you think is the source of these difficulties? Bad hardware? A problem with my flash drive? 

I.

---

### Post by oldfred on 2014-06-24
I have installed to flash drives multiple times, but not an external hard drive. Flash is configured the same on my system. One time I did have issues with drive number and had to manually edit grub to change from sdg to sdd and something similar for grub setting of hdX. One time I just had to experiment.


And I always forget the nomodeset on a new install. I have nVidia card and have to have it to boot live installer and first boot after install.

But I always partition in advance, use a smaller / (root) partition of 25GB or less and rest of drive as data partition. And then use Something Else to choose / partition and its format and to make sure I install grub2's boot loader into the drive the new install is going into.

---

### Post by ibexslam on 2014-06-24
I'm throwing in the towel for now. I'm afraid I'm going to damage the wall with my head. Thanks for taking the time to help, folks.

I.

---

### Post by ibexslam on 2014-06-28
I now have Xubuntu running from my external hard drive. To get here, I started over, doing things differently. I did not try to fix anything. Here's what I did:

I disconnected my internal C: drive.

Using the Universal USB Installer on another (Windows 7) computer, I installed Xubuntu 12.04 (64 bit), not 14.04, to a new USB flash drive, not the one I used before. I wiped everything off my external hard drive with Gparted using the new live USB 12.04 OS. 

I found that Windows could not see the blank external drive, so, using Gparted, I made a partition table and added a new NTSF partition that filled the disk. Then I "quick" formatted the drive under Windows, to restore it to "out of the box" condition.

I referred to this for guidance: [http://ubuntuforums.org/showthread.php?t=1880376&p=11453535#post11453535](http://ubuntuforums.org/showthread.php?t=1880376&p=11453535#post11453535)

From the running live USB, I hit the Install icon on the desktop. I skipped upgrades/3rd party packages during the install. I noticed that the installer was different from the 14.04 installer. I added a 25600 MB ext4 partition with mount point "/", and a 12288 MB one, at the end, used as swap (on the drop-down menu). I plan on enlarging that first partition later.

After restarting, my monitor threw up a "Input Not Support" (sic), then "No signal", but those turned out to be transient, and not a problem. Before long, I had a fully functional 12.04 install.

To upgrade to 14.04, I entered "sudo do-release-upgrade -d" into the terminal, following the advice on this page:
[http://all-tech-thoughts.blogspot.com/2014/04/i-have-just-upgraded-my-samsung-n145.html](http://all-tech-thoughts.blogspot.com/2014/04/i-have-just-upgraded-my-samsung-n145.html)
...which seems to have upgraded the OS to only 12.10 instead of 14.04. It took a very long time.

Right now, I'm upgrading to 13.10, which is taking a very long time. Presumably upgrading from that to 14.04 will also take a very long time.

So far, so good, if slow. If anything interesting or horrible happens, I'll post it here.

I.

---

### Post by Bashing-om on 2014-06-28
ibexslam; OK !

You do good work . I am mystified why the terminal command " sudo do-release-upgrade -d" did not version upgrade to 14.04 from 12.04 .
So far as I know It should have, any one with enlightenment ??
Release 12.10 and 13.04 are End_Of_Life and you may have some additional hoops to jump through as those repositories are turned down.

[INDENT][INDENT]Ya only get out
[INDENT][INDENT][INDENT][INDENT]what you put in
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-28
14.04 keeps crashing on me. It locks up and/or goes screwy during or shortly after starting up. Three times now. The other versions, as I upgraded and restarted each one, did not do this.

---

### Post by ibexslam on 2014-06-28
Four crashes in a row. The last time, I was able to get to the desktop, but when I tried to run Firefox, the cursor froze, then the screen went screwy. No success with 14.04. At least it boots up, for what it's worth.

Five crashes now. I was able to start Gimp and Abiword, but the system locked up soon after. Have not been able to run for more than a few minutes.

Is there something wrong with 14.04? 

I.

---

### Post by Bashing-om on 2014-06-28
ibexslam; Yikes !

I feel for you after all your time and hard work and this is the result.
Release 14.04 is stable and solid on my system ( though my work install remains at 13.10, I have ubuntu 14.04 installed as well as (L)ubuntu 14.04).

In this instance I am at a loss to advise on what to do or a course of action being as how this is a new upgrade from a fresh install.

[INDENT]don't know is not an
[INDENT][INDENT][INDENT]acceptable response, just the way it is[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-29
Yikes is right, Bash. All very mysterious. I might try again, going straight to 14.04. But not tonight. I suppose if I'm forced to stick with 12.04, it's not the end of the world. 

I'm like you, though, I hate to give up. Maybe I, or someone, will think of something. 

I probably should have started this discussion in the "Installation & Upgrades" section. 

I.

---

### Post by Bashing-om on 2014-06-29
ibexslam;

Well, I have thought about this sloppyation .. and even if we were to fix what is wrong now, I would still hold reservations about the system. I Think it would be worth the while and additional effort to boot up with a ubuntu 14.04 release in that "try ubuntu" mode from the liveDVD and see how things look at that point.

Else, we can boot to a terminal - no Xserver (GUI) started and see how the system performs, It could be a fault in the Xserver layer(??). It would still be much faster to install, than to trouble shoot - but if we do trouble shoot, look at all we might learn !

[INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]othertimes I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-29
Bashing-om,

Is your 14.04 32-bit or 64-bit? 

I.

---

### Post by Bashing-om on 2014-06-29
ibexslam; Hey:

I am running 64 bit on dual Athlon (AMD) CPUs. But to be honest, I have been running 'buntu on this box for several years and have never had a problem I did not cause myself. (discounting cats, dogs and grandchildren -> still none caused by system failure !)

I understand that if you have (4) Gigs of ram or less, 32 bit will run better - not having the addressing overhead to deal with.

Let's fire up 14.04 in a liveDVD and see what it takes to have a good experience in 14.04 .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-29
> **Bashing-om said:**
> Let's fire up 14.04 in a liveDVD and see what it takes to have a good experience in 14.04 .

I just grabbed a "fresh" download of Xubuntu 14.04, desktop, 64 bit, and made a Live USB flash drive out of it, using the newish flash drive (not used for OS installs before yesterday) I used the last time, reformatted and "repainted" with Universal USB Installer.

Booted up. Poked around on the desktop. Started Firefox, locked up, hard crash. 

Started up again, started Firefox, no crash so far. It's only been a few minutes...maybe 10 minutes later, still up and running with no problems at this point.

---

### Post by Bashing-om on 2014-06-29
ibexslam; K.

Standing by .. maybe I best go back and read the thread.. but how much ram do you have onboard ? ..Firefox takes some resources.

but
[INDENT][INDENT]hoping for the best
[/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-29
6 GB of ram. Firefox has been OK on this hardware.

I.

---

### Post by Bashing-om on 2014-06-29
ibexslam; 6 Gigs, should scream .

We ready to try a (RE-)install .. 1st look at what is on the hard disk ?
```

sudo fdisk -lu
sudo parted -l

```

Then make up our minds how we want to do this.

[INDENT][INDENT]The care and feeding of
[INDENT][INDENT][INDENT]ubuntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ibexslam on 2014-06-29
```
xubuntu@xubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32    15633407     7816688    c  W95 FAT32 (LBA)

Disk /dev/sdf: 500.1 GB, 500107859968 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000762a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2048    50002047    25000000   83  Linux
/dev/sdf2       952772606   976771071    11999233    5  Extended
/dev/sdf5       952772608   976771071    11999232   82  Linux swap /
Solaris

xubuntu@xubuntu:~$ sudo parted -l

Model: SanDisk Cruzer (scsi)
Disk /dev/sda: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32        boot, lba


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdf: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  25.6GB  25.6GB  primary   ext4            boot
 2      488GB   500GB   12.3GB  extended
 5      488GB   500GB   12.3GB  logical   linux-swap(v1)
 
```

There you go. The internal hard drive is still disconnected. 

I haven't installed anything to the external drive (Toshiba) today. It's still got the incrementally-upgraded-from-12.04-to-14.04-xubuntu-that-crashes on it.

Incidentally, the 14.04 Live USB is still up and running without crashing, so far. 

I.

---

### Post by Bashing-om on 2014-06-29
ibexslam; Humm ..

Partitioning looks good .. I find it rather strange though that the Toshiba drive is now recognized as 'sdf' - there is bunches about assignments i do not know, a far cry from the thumb drive as 'sda' to the Toshiba drive as 'sdf' ... 

Anyway ..How about this // delete the partition for the current root in GParted, leaving the extended partition and swap as is.
Point the installer to drive sdf, and make sure that the installer installs grub to 'sdf' and install 14.04 fresh. - is the Toshiba hard drive still known as 'sdf' at that time ? .. make sure such that grub gets installed properly.

If we are still just testing .. good 'nuff .
IF this is to be permanent, need to think about a partition for /home. - say 50 gigs for starters -

Else let the install wizard have it's way and use that entire hard drive (500Gigs !) for 'buntu's use //

I think we should float test this baby
[INDENT][INDENT]sinks, give it life support
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-06-29
With some BIOS and external drives large / (root) partitions can be an issue.

I might suggest starting with 25GB for / and make rest of drive /home or split as /home and NTFS partition if you may connect to a Windows machine.

You do have to use Something Else to have the option on where to install grub which you want in the MBR of your external. All auto install options default to sda, which you do not want.

Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb, or sdf)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by ibexslam on 2014-07-02
Hi, Bashing-om, oldfred, and anyone tuning in,

My Live USB ran for several days of fairly heavy use before crashing. I had to try three or four times again to get a stable (not locking up within first minute of desktop) go of it. 

Now that I've rebooted, the external drive is called sdb, not sdf. Possibly was connected post-boot last time? Not sure.

I've deleted the boot partition of the external drive. I'm about to try a fresh install of xubuntu 14.04, selecting sdb for the location of the bootloader.

I'll be back.

I.

---

### Post by ibexslam on 2014-07-03
OK, I'm writing from a new install of 64 bit xubuntu 14.04 onto my external hard drive. The first four times I started this up, it locked up soon after starting, the same way the Live USB was behaving. 

It's only been about 15 minutes, so it's too early to pop the cork on the champagne, but at this moment it's OK. Sometimes it's a good boot, and sometimes it isn't? It's odd.  I'm still not sure what is...was...the cause of these problems. 

Thanks for all your help, Bashing-om, and oldfred. Much obliged.

I.

---

### Post by Bashing-om on 2014-07-03
ibexslam; Hello;

OK, Is all good now ? // Do we keep trying, or "something else" ?

[INDENT][INDENT]what ever it may take
[/INDENT][/INDENT]

---

### Post by ibexslam on 2014-07-03
I think I've got it. As far as the crashing I've been experiencing. 

As I've been installing over and over, while installing, I've been leaving unchecked the two boxes about updates and 3rd party software. 

I think the problem was that I really needed that 3rd party software, an Nvidia video driver in particular. After (finally) getting that via Settings > Software & Updates, then restarting (unvoluntarily, as it would happen: crash no. 8 of the day), so far the new OS install seems to be stable.

It probably should have been obvious to me...duh...that there was a video problem. Most of the crashes resulted in a sort of locked textured screen, appearing to have been made of a repeated shred of the original desktop. 

Moral of the story: when installing, get your video driver, if you need one, up front. That's how it seems to me. I'll check back if I find different.

Bash, Fred, I commend you both for your tenacity, persistence and helpful attitude. Again, much obliged!

I.

---

### Post by Bashing-om on 2014-07-03
ibexslam; Hey,

Tough way to learn a lesson, but the recommended procedure with graphics install problems is to boot with the a boot parameter to induce the kernel to load the "fallback" graphics driver, and once installed and to the desktop, then install the required driver ( Additional Drivers utility).

Taking all the time and effort you have, I bet you are now much more comfortable with the operating system as a whole.

[INDENT][INDENT]knowledge is power
[/INDENT][/INDENT]

---

### Post by ibexslam on 2014-07-04
One last bit,

I see now that clicking the "3rd party software" button while installing doesn't grab and install the needed video driver. But it's easy to get afterward via Settings > Software & Drivers. Then a restart.

Happy Fourth, folks.

I.

---

### Post by Bashing-om on 2014-07-04
ibexslam; Looking good .

I am pleased that you are pleased.

Non free codecs for DVD's are not included in the install, and there are additionally 4 ( maybe 5 ) others available with:
```

sudo apt-get install ubuntu-restricted-extras

```
You might want to verify that libdvdread4 is installed:
```

dpkg -l libdvdread4

```
And if there are addition codecs you would like, see:
```

apt-cache show ubuntu-restricted-extras

``` for the links.

Enjoy ubuntu and as this matter is now concluded; 
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
@top right of posting -> thread tools.

[INDENT][INDENT]wasn't nothing but a big thing
[/INDENT][/INDENT]

---

