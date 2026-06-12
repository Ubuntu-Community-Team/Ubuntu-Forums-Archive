---
title: "Emergency Please Help Recover Lost Data!"
date: 2015-08-20
forum: General Help
---

### Post by shadowknight2 on 2015-08-20
Hi I dont know a whole lot about ubuntu so please be gentle and baby me. That being said my seagate central nas mainboard crashed the other day with TONS of precious data that I had no where else (I was upgrading my pc and moved all the data to it). I opened the case and pulled the drive out. After some research I found that it was in ext4 format and should be plug and play with ubuntu. So I did just that; installed ubuntu and plugged in the drive but nothing. The computer sees the drive but cant do anything with it.  Ive found programs like essext2 and r-linux but the first wont load for whatever reason and the second failed the hdd scan at 1TB out of 2. I really need this data off the drive. The drive works and is functional. I know I can buy another seagate central and swap the drives but Ill be damned if I give that company any more money. Again I dont know alot about linux please be clear. THANK YOU SO MUCH FOR THE HELP. This really means alot to me!!!

[COLOR=#000000][FONT=arial black]EDIT EDIT:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][SIZE=1][SIZE=3][SIZE=2]Alright I got it. Before when I tried to navigate to home/media/username there was nothing there but a public folder. After a reboot the drive was there and Im on my way into 2 days of file transfers!! 
Thanks for all the help guys I really appreciate it. If anyone has this problem in the future USE R-LINUX. Pm me if you need any help getting it to work. Thanks again everyone!!![/SIZE][/SIZE][/SIZE][/FONT][/COLOR]

---

### Post by steeldriver on 2015-08-20
Hello and welcome to the forums

There have been several previous threads about data recovery from Seagate NAS devices - iirc they tend to use LVM2 (logical volumes rather than traditional partitions) and the ext filesystem may use large blocksize

To get started, we will need the details of your device / partition layout - which is easiest to get from the command line, either

```

sudo fdisk -l

```
or (better)

```

sudo parted -l

```

(parted can handle GPT disks and LVM, but might not be installed by default).

---

### Post by ajgreeny on 2015-08-20
This may simply be a permissions problem with the data drive that we can solve very easily but to do so we will need you to tell us a lot more about how the data drive is attached to your new Ubuntu installation and how and where you installed Ubuntu; I hope you did not install to the drive with all the data on it or you will undoubtedly have already overwritten a lot of that precious data that you want to get.

Perhaps you are simply running Ubuntu as a live OS from a USB or DVD?  We can use that live system if necessary.

I have just seen steeldriver's reply, and was not aware that Seagate used LVM on their NAS devices, but even if that is the case you should still be able to get to those files, though it may be just a little more complicated that I thought, needing the installation of a few LVM packages in your Ubuntu OS.

LVM is something I have never used and know little about, so I will leave you now in steeldriver's capable hands, though I will look in on this to see if I can help any further.  Good luck!

---

### Post by shadowknight2 on 2015-08-20
Alright as requested here is the results of the first piece of code you have me [HERE]("http://tinypic.com/view.php?pic=e5kbb8&s=8#.VdXHRZko7qB").
The second piece of code told me the disk had an unrecognizable label. 
To answer a bit ajgreeny's questions if they help the drive to my knowledge had not been initialized or the system. It will not pop up on the toolbar as a mounted usb. I have the drive connected via a sata to usb connection. Finally I'm running ubuntu 14.04 that is installed as the only is on a micro machine I had laying around.
I would aslo like to mention that the main files on the drive that I'm after were password protected.  Will this be a problem?

EDIT:

```
 shadowwrath5@shadowwrath5-NAS:~$ sudo fdisk -l

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc223

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    54364159    27181056   83  Linux
/dev/sda2        54366206    62531583     4082689    5  Extended
/dev/sda5        54366208    62531583     4082688   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 30400 cylinders, total 488378646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  2743214780   ee  GPT


shadowwrath5@shadowwrath5-NAS:~$ sudo parted -l
Model: ATA SanDisk SDSSDRC0 (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  27.8GB  27.8GB  primary   ext4            boot
 2      27.8GB  32.0GB  4181MB  extended
 5      27.8GB  32.0GB  4181MB  logical   linux-swap(v1)


Error: /dev/sdb: unrecognised disk label  


```

---

### Post by steeldriver on 2015-08-20
Can you copy-paste the terminal outputs as text rather than images please? it's easier for everyone to read. If possible, use the forum's ```
 tags (available in the advanced post editor by highlighting the text and hitting the # button).

I'm not sure what to make of your fdisk output, however going forward with the assumption that the NAS device is /dev/sdb and that it *may *be LVM, can you add the outputs of

[CODE]
sudo file -sL /dev/sdb1

sudo pvs

sudo lvs

```

You may need to install the lvm2 package

---

### Post by shadowknight2 on 2015-08-20
Yes sorry about the image I was heading to work and I had to reply on mobile. Anyway I ran the code and lvm2 wasn&#8217;t installed so I did just that and installed it. Here is the outputs of the code post install:

```
shadowwrath5@shadowwrath5-NAS:~$ sudo file -sL /dev/sdb1
/dev/sdb1: ERROR: cannot open `/dev/sdb1' (No such file or directory)
shadowwrath5@shadowwrath5-NAS:~$ sudo pvs
shadowwrath5@shadowwrath5-NAS:~$ sudo lvs
  No volume groups found


```

I ran the same code for /dev/sdb and got this:

```
 shadowwrath5@shadowwrath5-NAS:~$ sudo file -sL /dev/sdb
/dev/sdb: x86 boot sector
shadowwrath5@shadowwrath5-NAS:~$ sudo pvs
shadowwrath5@shadowwrath5-NAS:~$ sudo lvs
  No volume groups found


```

I also edited the post above with code instead of an image.

---

### Post by oldfred on 2015-08-21
You have the somewhat unusual 4k/4k configuration. Most new drives are 512b/4096b.

There was a bug. Suposedly fixed back in 2013.
 Installer crashed when trying to partition 4k/4k sector hard disks
[https://bugs.launchpad.net/ubuntu/+source/partman-basicfilesystems/+bug/1065281](https://bugs.launchpad.net/ubuntu/+source/partman-basicfilesystems/+bug/1065281)

Are you using a new version of Ubuntu and 64 bit?

---

### Post by shadowknight2 on 2015-08-21
Yes I'm using Ubuntu 14.04 and 64bit so I don&#8217;t think there should be an issue there.

I just ran test disk on the drive. It was able to see all the partitions on the drive except a FAT32 sector (which I think is unused space so its fine). The problem is that it sees the LinuxLVM sectors but cannot list the files for whatever reason. I also ran R-linux which was able to recover the files on the public partition on the drive. Which is great except the important stuff that I need is on a password protected other partition. Any other ideas guys???

---

### Post by oldfred on 2015-08-21
You were not showing any LVM partitions inside the physical partitions, so is it just encrypted folders or /home. Or is it a vendor encryption. Normally mounting a encrypted LVM asks for your passphrase.

This was on resizing, but has all the commands to mount a encrypted LVM partition. 
 How to: Mount & Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

If like a /home that is encrypted.

 Includes chroot which you should not need if booted into a system:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by shadowknight2 on 2015-08-21
OKAY OKAY OKAY SOOOOO I read up on your articales and didnt really know  what to do with them as I have full access to the home folder and the  partitions on the drive that are not password protected should show  right?

ANYWAY... I went back to R-linux for another try because  every where I look people swear it works. This time the program found  everything. All files even the password protected stuff!!!

All I need to know now is how the hell do I transfer the stuff straight to my other externall hdd???
The  pc I have linux on only has 32gb of space on it. So I cant transfer the  data to the local disk then to the hdd. How do I find it in the popup  box to select the drive?? The external HDD is mounted and I can access  it. I just dont know the path to the drive.

[SIZE=5][FONT=arial black]EDIT EDIT:
[FONT=arial][SIZE=1][SIZE=3][SIZE=2]Alright I got it. Before when I tried to navigate to home/media/username there was nothing there but a public folder. After a reboot the drive was there and Im on my way into 2 days of file transfers!! 
Thanks for all the help guys I really appreciate it. If anyone has this problem in the future USE R-LINUX. Pm me if you need any help getting it to work. Thanks again everyone!!!
[/SIZE][/SIZE][/SIZE][/FONT]
[/FONT][/SIZE]

---

