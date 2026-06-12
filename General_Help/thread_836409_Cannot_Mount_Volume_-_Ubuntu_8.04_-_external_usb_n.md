---
title: "Cannot Mount Volume - Ubuntu 8.04 - external usb ntfs drive"
date: 2008-06-21
forum: General Help
---

### Post by rlj1965 on 2008-06-21
Hello,

Relative newbie here so please accept apology if I am not well versed in using Ubuntu.

I was using Win XP Pro SP3 on my old machine. The OS mucked up for the last time (crashed so bad so as to require a clean install) after installing a new antivirus program (Avast). 

I decided to make the move to Ubuntu. No problem since all files on the primary drive of the old machine were just OS related. I kept all of the important stuff (music, documents, reg codes, etc.) on an external Seagate 500gb drive which is formatted in NTFS. Obviously, the external drive was not disconnected/shut down properly in windows since windows crashed. I purchased some new equipment and decided this was a good chance to upgrade both hardware. After setting up the new PC I decided to use my Ubuntu 7.04 live CD to boot and install to my new PC. The install went really well. I was prompted to do upgrades. After all upgrades were installed I added the Amarok program since I was used to Media Monkey in Windows and read that Amarok was similar. The computer had no problem importing the songs on the external drive to the music library. I am playing songs and loving it. 

Next day I decided to upgrade to Ubuntu 8.04 and set out to do a clean install so I downloaded the 8.04 DVD, Burned it to a disc and then wiped my computer clean. I did the install and initial upgrades with no problem. Now the problem... when I connect the external drive, the OS recognizes the drive, but will not mount it. 

I get a box stating:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdf1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sdf1 /mnt/external/ -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sdf1 /mnt/external/ ntfs-3g defaults,force 0 0



Before posting here I did a lot of research about the problem on the net and have not been able to find a solution that works for me. That is why I am hoping to appeal to a more experienced person to assist me in solving this problem. I do not have a windows pc in the house right now so I am unable to connect the drive and then properly shut it down. I have tried suggestions to force the drive to mount with no luck. I am able to post any log files that are needed if you ask. Please help. Why did this drive work well in Feisty Fawn but not in Hardy Heron?

Thanks,

Rich (rlj1965)

---

### Post by avtolle on 2008-06-21
Quick thought, which might help: is nfts-3g installed on your system? From terminal```
sudo aptitude update && sudo aptitude install nfts-3g
```
If it tells you the program is already installed, then my thought isn't any good. If it installs the app and its dependencies, then after you are back to the prompt, try the mount command again. Good luck.

---

### Post by MaxGhost on 2008-06-21
I'm actually having really similar troubles. I got a 250gb seagate external (freeagent). I just have the 7.04 CD and I booted my computer from it. Windows gave me a Blue Screen of Death, so I needed to drop all my important files from my internal to my external. I got that error too a few hours ago, but I just rebooted my comp and had a fresh boot of Ubuntu... 

I made a topic about my troubles last night, but after a while nobody posted in it, didn't get help anymore, so I made a second one...

[http://ubuntuforums.org/showthread.php?t=835940](http://ubuntuforums.org/showthread.php?t=835940)
[http://ubuntuforums.org/showthread.php?t=836196](http://ubuntuforums.org/showthread.php?t=836196)

Let me know if any of that helps you, or if anyone can help me?

---

### Post by rlj1965 on 2008-06-21
> **avtolle said:**
> Quick thought, which might help: is nfts-3g installed on your system? From terminal```
sudo aptitude update && sudo aptitude install nfts-3g
```
If it tells you the program is already installed, then my thought isn't any good. If it installs the app and its dependencies, then after you are back to the prompt, try the mount command again. Good luck.

Here is what I got... paste from the terminal:

richard@richard-desktop:~$ sudo aptitude update && sudo aptitude install nfts-3g
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "nfts-3g"
Couldn't find any package whose name or description matched "nfts-3g"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
richard@richard-desktop:~$

---

### Post by rlj1965 on 2008-06-21
> **rlj1965 said:**
> Hello,

Relative newbie here so please accept apology if I am not well versed in using Ubuntu.

I was using Win XP Pro SP3 on my old machine. The OS mucked up for the last time (crashed so bad so as to require a clean install) after installing a new antivirus program (Avast). 

I decided to make the move to Ubuntu. No problem since all files on the primary drive of the old machine were just OS related. I kept all of the important stuff (music, documents, reg codes, etc.) on an external Seagate 500gb drive which is formatted in NTFS. Obviously, the external drive was not disconnected/shut down properly in windows since windows crashed. I purchased some new equipment and decided this was a good chance to upgrade both hardware. After setting up the new PC I decided to use my Ubuntu 7.04 live CD to boot and install to my new PC. The install went really well. I was prompted to do upgrades. After all upgrades were installed I added the Amarok program since I was used to Media Monkey in Windows and read that Amarok was similar. The computer had no problem importing the songs on the external drive to the music library. I am playing songs and loving it. 

Next day I decided to upgrade to Ubuntu 8.04 and set out to do a clean install so I downloaded the 8.04 DVD, Burned it to a disc and then wiped my computer clean. I did the install and initial upgrades with no problem. Now the problem... when I connect the external drive, the OS recognizes the drive, but will not mount it. 

I get a box stating:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdf1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sdf1 /mnt/external/ -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sdf1 /mnt/external/ ntfs-3g defaults,force 0 0



Before posting here I did a lot of research about the problem on the net and have not been able to find a solution that works for me. That is why I am hoping to appeal to a more experienced person to assist me in solving this problem. I do not have a windows pc in the house right now so I am unable to connect the drive and then properly shut it down. I have tried suggestions to force the drive to mount with no luck. I am able to post any log files that are needed if you ask. Please help. Why did this drive work well in Feisty Fawn but not in Hardy Heron?

Thanks,

Rich (rlj1965)



I should also add that when I try to mount the drive manually, it tells me that only root can do that.

---

### Post by MaxGhost on 2008-06-21
do the fallowing code to get ntfs-3g:

sudo apt-get install ntfs-3g ntfs-config

---

### Post by rlj1965 on 2008-06-21
> **MaxGhost said:**
> do the fallowing code to get ntfs-3g:

sudo apt-get install ntfs-3g ntfs-config

OK MaxGhost... thats done and I selected to allow to write to external drives. Still getting the cannot mount volume error. Anyone have complete directions for a fix from here? Thanks in advance.

Rich

---

### Post by halfling85 on 2008-07-10
Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

---

### Post by garloosh on 2008-07-10
Thanks Halfling - That worked for me. I have a seagate external hd and am running hardy heron

---

### Post by rlj1965 on 2008-07-13
> **halfling85 said:**
> Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

Thanks halfling85,

I ended up taking the drive in to my office where I have a few Windows machines. I connected it via usb, allowed it to be recognized and then unmounted it through the disconnect hardware aplet. That reset the logfile and when i brought it back home and connected it on my 8.04 machine it mounted perfectly!

rlj1965

---

### Post by slambrick on 2008-07-16
I can't say how pleased i was to find your post which fixed my access issue to my external HD (Lacie 500gb).
Cheers

S.Lambrick

---

### Post by nothingspecial on 2008-07-16
Me Too

---

### Post by lacrosse_man16 on 2008-07-23
> **halfling85 said:**
> Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

If you weren't a dude I would totally make out with you right now.

---

### Post by Hapkidoan on 2008-07-25
me too! there should be a sticky on this! I spent 3 hours working on this problem and this solution took 2 min. THANKS!!! \\:D/\\:D/\\:D/

---

### Post by andale on 2008-08-13
edit: Forget it. I installed windows on another pc real quick and just took care of it that way.

<hr>
Sorry guys, I am not a winner here.
I tried what the suggestion window said to force it, then i tried adding the line to /etc/fstab and then i tried everything i saw here and now i keep getting
```
andale@linux:~$ sudo aptitude update && sudo aptitude install ntfs-3g
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
andale@linux:~$ sudo apt-get install ntfs-3g ntfs-config
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
is it cuz i've got the line in fstab?
i added the line at the bottom
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=cb725b6f-e843-467a-870b-4a232c91c1cc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=7b5db197-346d-4afc-a9ec-a0da53af2131 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdf2	/media/freeagent_tim's ntfs-3g, force 0	0
```
okay, i added one more line to the fstab because somehow, after restarting a third time, the drive finally mounted, and now i wanna get the other one to mount as well. Unfortunately for me, i now am getting the 'you are not privileged to mount this volume' on the other drive.

sorry, i should mention maybe that these are partitions on a single drive

the added line was
```
/dev/sdb3	/media/Free_Agent ntfs-3f, force 0 0
```

---

### Post by squid636 on 2008-09-08
I just wanted to say THANK YOU for this fix.  I too spent too much time working on this and the fix took me about 30 secs.  Thanks.:)

---

### Post by yani1shu on 2008-09-13
I really hope somebody watching this thread can help me, i'm kind-of out of ideas here. I have two external hard drives, a 500Gb and a 1Tb. The both work fine  when only one of the is plugged in via usb, however, as soon as i plug the other one in then the original one disappears. Not even fdisk -l sees the original drive. This is in a brand new installation of Heron with all updates applied. 
**_Here are the resulst of fdisk -l with both drives plugged in:_**

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16561655

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe206899
[U][B]
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

Here is my fstab:[/B][/U]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7c68ae64-480b-4620-9f1a-89bf2cddcba2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6fb9b929-0741-4634-9084-ed098820316b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[B][U]
And here is my mtab:
[/U][/B]
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/yani1shu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=yani1shu 0 0
/dev/sdc1 /media/disk fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

**_Also, here is results from dmesg (beginning at the USB part, from what i can tell)_**

[   23.091148] usb-storage: device scan complete
[   23.091721] scsi 2:0:0:0: Direct-Access     WD       5000AAJ External 1.06 PQ: 0 ANSI: 0
[   23.093307] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   23.135057] usb-storage: device scan complete
[   23.135646] scsi 3:0:0:0: Direct-Access     Maxtor   OneTouch         0121 PQ: 0 ANSI: 4
[   23.206921] usb 4-4: reset high speed USB device using ehci_hcd and address 2
[   23.339320] usb 4-4: failed to restore interface 0 altsetting 0 (error=-71)
[   23.339351] usb 4-4: USB disconnect, address 2
[   23.339401] sd 2:0:0:0: [sdb] Write Protect is off
[   23.339405] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   23.339409] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   23.339654] sd 2:0:0:0: [sdb] READ CAPACITY failed
[   23.339658] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[   23.339664] sd 2:0:0:0: [sdb] Sense not available.
[   23.339713] sd 2:0:0:0: [sdb] Write Protect is off
[   23.339716] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   23.339719] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   23.339767] sd 2:0:0:0: [sdb] Attached SCSI disk
[   23.339828] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   23.340826] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
[   23.341905] sd 3:0:0:0: [sdc] Write Protect is off
[   23.341909] sd 3:0:0:0: [sdc] Mode Sense: 2d 08 00 00
[   23.341912] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   23.343083] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
[   23.343852] sd 3:0:0:0: [sdc] Write Protect is off
[   23.343856] sd 3:0:0:0: [sdc] Mode Sense: 2d 08 00 00
[   23.343859] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   23.343864]  sdc:<6>usb 4-4: new high speed USB device using ehci_hcd and address 5
[   23.588223] usb 4-4: configuration #1 chosen from 1 choice
[   23.594165] scsi4 : SCSI emulation for USB Mass Storage devices
[   23.602224] usb-storage: device found at 5
[   23.602227] usb-storage: waiting for device to settle before scanning
[   28.599343] usb-storage: device scan complete
[   28.599960] scsi 4:0:0:0: Direct-Access     WD       5000AAJ External 1.06 PQ: 0 ANSI: 0
[   29.470359] Linux agpgart interface v0.102
[   29.639688] agpgart: Detected an Intel 830M Chipset.
[   29.639844] agpgart: Detected 892K stolen memory.
[   29.769899] agpgart: AGP aperture is 128M @ 0xf0000000
[   29.769936] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   29.901516] intel_rng: Firmware space is locked read-only. If you can't or
[   29.901521] intel_rng: don't want to disable this in firmware setup, and if
[   29.901523] intel_rng: you are certain that your system has a functional
[   29.901525] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   29.960799] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.073307] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.125727] input: Power Button (FF) as /devices/virtual/input/input4
[   30.137016] ACPI: Power Button (FF) [PWRF]
[   30.137230] input: Sleep Button (CM) as /devices/virtual/input/input5
[   30.152954] ACPI: Sleep Button (CM) [SLPB]
[   30.171094] iTCO_vendor_support: vendor-support=0
[   30.229987] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.236799] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   30.236899] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.850192] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   34.272680] parport_pc 00:09: reported by Plug and Play ACPI
[   34.272745] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   34.515597] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   34.515637] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   34.883438] intel8x0_measure_ac97_clock: measured 54869 usecs
[   34.883445] intel8x0: clocking to 48000
[   36.438610]  sdc1
[   36.438730] sd 3:0:0:0: [sdc] Attached SCSI disk
[   36.438797] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   36.440950] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   36.556090] usb 4-4: reset high speed USB device using ehci_hcd and address 5
[   36.690229] sd 4:0:0:0: [sdb] Write Protect is off
[   36.690236] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   36.690240] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   36.691335] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   36.807578] usb 4-4: reset high speed USB device using ehci_hcd and address 5
[   37.055073] usb 4-4: reset high speed USB device using ehci_hcd and address 5
[   37.189121] sd 4:0:0:0: [sdb] Write Protect is off
[   37.189128] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   37.189132] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   37.189142]  sdb:<6>usb 4-4: reset high speed USB device using ehci_hcd and address 5
[   39.908511] lp0: using parport0 (interrupt-driven).
[   40.238957] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   41.039286] EXT3 FS on sda1, internal journal
[   43.793518] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.929292] No dock devices found.
[   47.572199]  sdb1
[   47.572315] sd 4:0:0:0: [sdb] Attached SCSI disk
[   47.572378] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   47.753526] usb 4-4: reset high speed USB device using ehci_hcd and address 5
[   49.805447] apm: BIOS not found.
[   50.148780] ppdev: user-space parallel port driver
[   50.303374] audit(1221338799.844:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4934 profile="/usr/sbin/cupsd" namespace="default"
[   52.979082] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   53.198626] Bluetooth: Core ver 2.11
[   53.206657] NET: Registered protocol family 31
[   53.206664] Bluetooth: HCI device and connection manager initialized
[   53.206669] Bluetooth: HCI socket layer initialized
[   53.230564] Bluetooth: L2CAP ver 2.9
[   53.230572] Bluetooth: L2CAP socket layer initialized
[   53.294730] Bluetooth: RFCOMM socket layer initialized
[   53.295072] Bluetooth: RFCOMM TTY layer initialized
[   53.295078] Bluetooth: RFCOMM ver 1.8
[   55.230490] NET: Registered protocol family 17
[   57.114836] NET: Registered protocol family 10
[   57.115554] lo: Disabled Privacy Extensions
[   65.535571] [drm] Initialized drm 1.1.0 20060810
[   65.556474] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   65.556488] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   65.556621] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   68.084225] eth0: no IPv6 routers present
[   77.940469] usb 4-4: reset high speed USB device using ehci_hcd and address 5
[   78.073336] usb 4-4: device descriptor read/all, error 0
[   78.187909] usb 4-4: reset high speed USB device using ehci_hcd and address 5
[   78.706845] usb 4-4: device not accepting address 5, error -71
[   78.818668] usb 4-4: reset high speed USB device using ehci_hcd and address 5
[   79.225800] usb 4-4: device not accepting address 5, error -71
[   79.337597] usb 4-4: reset high speed USB device using ehci_hcd and address 5
[   79.744766] usb 4-4: device not accepting address 5, error -71
[   79.744981] usb 4-4: USB disconnect, address 5
[   79.745614] scsi 4:0:0:0: Device offlined - not ready after error recovery
[   79.748941] scsi 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   79.748955] end_request: I/O error, dev sdb, sector 40
[   79.748961] Buffer I/O error on device sdb, logical block 5
[   79.748969] Buffer I/O error on device sdb, logical block 6
[   79.748974] Buffer I/O error on device sdb, logical block 7
[   79.748977] Buffer I/O error on device sdb, logical block 8
[   79.748981] Buffer I/O error on device sdb, logical block 9
[   79.748985] Buffer I/O error on device sdb, logical block 10
[   79.748989] Buffer I/O error on device sdb, logical block 11
[   79.749009] scsi 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   79.749014] end_request: I/O error, dev sdb, sector 976773160
[   79.749017] Buffer I/O error on device sdb, logical block 122096645
[   79.749056] Buffer I/O error on device sdb, logical block 122096645
[   79.749106] Buffer I/O error on device sdb, logical block 122096645
[   79.856600] usb 4-4: new high speed USB device using ehci_hcd and address 6
[   79.968320] usb 4-4: device descriptor read/64, error -71
[   80.206574] usb 4-4: configuration #1 chosen from 1 choice
[   80.225709] scsi5 : SCSI emulation for USB Mass Storage devices
[   80.239950] usb-storage: device found at 6
[   80.239959] usb-storage: waiting for device to settle before scanning
[   85.233761] usb-storage: device scan complete
[   85.345493] usb 4-4: reset high speed USB device using ehci_hcd and address 6
[   85.478095] usb 4-4: can't restore configuration #1 (error=-71)
[   85.478313] usb 4-4: USB disconnect, address 6
[   85.589562] usb 4-4: new high speed USB device using ehci_hcd and address 7
[   85.722025] usb 4-4: configuration #1 chosen from 1 choice
[   85.764600] scsi6 : SCSI emulation for USB Mass Storage devices
[   85.772216] usb-storage: device found at 7
[   85.772224] usb-storage: waiting for device to settle before scanning
[   90.788327] usb-storage: device scan complete
[   90.898345] usb 4-4: reset high speed USB device using ehci_hcd and address 7
[   91.031227] usb 4-4: device descriptor read/all, error 0
[   91.145865] usb 4-4: reset high speed USB device using ehci_hcd and address 7
[   91.389370] usb 4-4: reset high speed USB device using ehci_hcd and address 7
[   91.632861] usb 4-4: reset high speed USB device using ehci_hcd and address 7
[   91.765790] usb 4-4: failed to restore interface 0 altsetting 0 (error=-71)
[   91.766028] usb 4-4: USB disconnect, address 7
[   91.876350] usb 4-4: new high speed USB device using ehci_hcd and address 8
[   92.010121] usb 4-4: configuration #1 chosen from 1 choice
[   92.065849] scsi7 : SCSI emulation for USB Mass Storage devices
[   92.092097] usb-storage: device found at 8
[   92.092104] usb-storage: waiting for device to settle before scanning
[   97.089143] usb-storage: device scan complete
[   97.201748] usb 4-4: reset high speed USB device using ehci_hcd and address 8
[   97.334521] usb 4-4: device descriptor read/all, error 0
[   97.451298] usb 4-4: reset high speed USB device using ehci_hcd and address 8
[   97.582033] usb 4-4: device descriptor read/all, error 0
[   97.696789] usb 4-4: reset high speed USB device using ehci_hcd and address 8
[   97.832365] usb 4-4: reset high speed USB device using ehci_hcd and address 8
[   97.965159] usb 4-4: failed to restore interface 0 altsetting 0 (error=-71)
[   97.965203] usb 4-4: USB disconnect, address 8
[   98.079845] usb 4-4: new high speed USB device using ehci_hcd and address 9
[   98.213085] usb 4-4: configuration #1 chosen from 1 choice
[   98.249782] scsi8 : SCSI emulation for USB Mass Storage devices
[   98.255712] usb-storage: device found at 9
[   98.255721] usb-storage: waiting for device to settle before scanning
[  103.245617] usb-storage: device scan complete
[  106.363905] scsi 8:0:0:0: Direct-Access     WD       5000AAJ External 1.06 PQ: 0 ANSI: 0
[  106.365869] sd 8:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  106.479161] usb 4-4: reset high speed USB device using ehci_hcd and address 9
[  106.726438] usb 4-4: reset high speed USB device using ehci_hcd and address 9
[  106.858751] usb 4-4: failed to restore interface 0 altsetting 0 (error=-71)
[  106.858783] usb 4-4: USB disconnect, address 9
[  106.859246] sd 8:0:0:0: [sdb] Write Protect is off
[  106.859252] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  106.859256] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  106.859519] sd 8:0:0:0: [sdb] READ CAPACITY failed
[  106.859522] sd 8:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  106.859529] sd 8:0:0:0: [sdb] Sense not available.
[  106.859576] sd 8:0:0:0: [sdb] Write Protect is off
[  106.859580] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  106.859582] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  106.859637] sd 8:0:0:0: [sdb] Attached SCSI disk
[  106.859700] sd 8:0:0:0: Attached scsi generic sg4 type 0
[  106.977187] usb 4-4: new high speed USB device using ehci_hcd and address 10
[  107.110509] usb 4-4: device descriptor read/all, error -71
[  107.225429] usb 4-4: new high speed USB device using ehci_hcd and address 11
[  107.358270] usb 4-4: device descriptor read/all, error 0
[  107.472962] usb 4-4: new high speed USB device using ehci_hcd and address 12
[  107.495127] usb 4-4: device descriptor read/all, error 0
[  107.608658] usb 4-4: new high speed USB device using ehci_hcd and address 13
[  108.015835] usb 4-4: device not accepting address 13, error -71
[  602.181078] end_request: I/O error, dev fd0, sector 0
[  602.205024] end_request: I/O error, dev fd0, sector 0


Any thoughts and suggestions would be greatly appreciated. This is getting ridiculous.

Thanks

---

### Post by shud on 2008-09-15
Will this work for internal drives? I have two drives that were hooked up during a bad shutdown a few months ago, and another 500gb that has been in a Windows environment since then. The 500gb mounts fine, the others put up a fight.

---

### Post by pucenavel on 2008-09-15
I find it hard to believe that the first reply wasn't:

"Hook it up to a Windows box - do Safely Remove Hardware, unplug and hook back to Linux box."!?!

10 seconds and problem solved v. typing in commands that may or may not solve the problem (and could make matters worse).

---

### Post by 47_MasoN_47 on 2008-09-16
Why would you want to do that?  All Windows does is reset the logfile just like these guys were doing with the terminal commands.

---

### Post by SeattleToJerusalem on 2008-09-18
First off...thanks all for the great info!
However, I'm having a slightly different problem now...
I got Ubuntu to recognize and read ntfs, but I am still unable to mount the volume. The error is:

Cannot obtain lock on /media/.hal-mtab

???

---

### Post by pucenavel on 2008-09-27
> **47_MasoN_47 said:**
> Why would you want to do that?  All Windows does is reset the logfile just like these guys were doing with the terminal commands.

Because not all of us are that comfortable running commands that start with "sudo" that are given to us by "experts".  I've twice now had to pretty much start over with a clean install of Ubuntu because my system became unstable following such advise.

I am now more wary to look for simpler solutions.

---

### Post by nothingspecial on 2008-09-27
> **pucenavel said:**
> I find it hard to believe that the first reply wasn't:

"Hook it up to a Windows box - do Safely Remove Hardware, unplug and hook back to Linux box."!?!

10 seconds and problem solved v. typing in commands that may or may not solve the problem (and could make matters worse).


Oh yeah, great. I`ll just go and buy a £300 windows machine to fix a £7 usb stick. 
"Expert" advice. What a "simple solution".
:wink:

---

### Post by rlj1965 on 2008-10-25
The saga continues now from my original post. Itook the two little ones out for a halloween hayride and left my pc logged on as me (administrator). My teenage son was using the machine and somehow mucked up the permissions on the external drive. 

When I right click on the drive or any file in it, it now appears that ownership of the drive belongs to root. I keep all of my music, movies and critical data on there, so something as simple as editing a track id3 tag or document is not allowed because you need root permission to do that. How do I change my permissions back to the way they were where any user on the machine (especially me) is able to read/write to this drive??? 

As a second question to this post, how do I encrypt a given folder on this deive so that it requires a password to read/write?

Thanks in advance - rlj1965 (OP)

---

### Post by jerome1232 on 2008-10-25
As far as permission on ntfs you have to set them up at mount time. If you wanted it mounted at boot time and be readable/writable by everyone you would make an fstab similiar to this (just an example I don't know what your actual setup is)

umask sets the permissions of file's and directories, 000 is world readable/writeable

```
/dev/sdxx /media/ntfsdrive ntfs-3g umask=000 0 0
```

I think encfs can do what you want (encrypt a folder transparently) I'm not sure if it's in hardies repos though. Haven't used it so no advice there.

---

### Post by WorldPax on 2008-11-29
Thank you all, just bought a new external HD, had this issue, and now all is well thanks to this thread. Tally-Ho.

---

### Post by macpointman on 2008-12-04
Another reason not to use Windows.  Simply inserting it into a windows machine and ejecting it properly worked.  This should be made aware to the masses because alot of people may not know this fact.

MacPointMan

---

### Post by notanerd on 2008-12-15
I just used those commands to fix access my external hard drive on Ubuntu 8.10. Thank you so much!

---

### Post by dave1314 on 2008-12-30
Thanks so much - works perfectly for me too!!!

---

### Post by mikemccoy on 2009-01-26
> **rlj1965 said:**
> Thanks halfling85,

I ended up taking the drive in to my office where I have a few Windows machines. I connected it via usb, allowed it to be recognized and then unmounted it through the disconnect hardware aplet. That reset the logfile and when i brought it back home and connected it on my 8.04 machine it mounted perfectly!

rlj1965

I did the same thing.  This worked no problem.  Thanks!

---

### Post by andale on 2009-01-27
For something that's so easy to fix it was the single most stressful moment I've had yet while playing with linux.
I thought I'd lost a 500G hdd!

---

### Post by halfling85 on 2009-01-27
Wow I hadn't checked this thread in months, I am happy I was able to scour the internet (it wasn't my idea), post it here, and help so many folks :)... I just get all warm and fuzzy inside... lol

---

### Post by mikecj on 2009-02-18
> **halfling85 said:**
> Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

Oh my god you have absolutely no idea how much I love you right now!!! Even windows XP and Vista put together couldn't solve that problem. I am a very very very very very happy man. Thank you!!!

---

### Post by jannisary on 2009-02-18
thank you so much for supporting and admistirating for our ubuntu ///  viva la turkey

---

### Post by shootdorisday on 2009-03-04
identical problem to the OP some of the others in this thread.

the fix given works a treat.

i've been lurking here leeching your help as a luddite not overly new to ubuntu and signed up specifically to say thank you to the chap that gave the command line.

worked perfectly.

thank you very much.

---

### Post by farhado on 2009-03-05
> **halfling85 said:**
> Hey RLJ, fellow noob here...

Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

I (a noob of course) have the same story here with an unmountable flash memory that suffers from a unsafe removal in my badly degraded windows machine. I have tried several different receipts, including safe remove in windows (it safely removes, but can not read the usb). I also tried ntfsfix that you explained. 

Unfortunately after executing 

[HTML]sudo ntfsfix /dev/sdb1[/HTML]

I receive this message:

[HTML]Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.[/HTML]

I tried 
chkdsk --help
but it says:

bash: chkdsk: command not found


I have no idea of what to do now.
it is really frustrating: hours that I am wandering around the net to find a solution to solve this slight problem (appearently a very common bug)  out. I even think to reinstall windows, That is buy a coat for my bottom!

---

### Post by farhado on 2009-03-05
I (a noob of course) have the same story here with an unmountable flash memory that suffers from a unsafe removal in my badly degraded windows machine. I have tried several different receipts, including safe remove in windows (it safely removes, but can not read the usb). I also tried ntfsfix that you explained. 



 I receive this command when I plug it


> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


Unfortunately after executing 

> sudo ntfsfix /dev/sdb


> Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

I tried 
chkdsk --help
but it says:

bash: chkdsk: command not found


I have no idea of what to do now.
it is really frustrating: hours that I am wandering around the net to find a solution to solve this slight problem (apparently a very common bug)  out. I even think to reinstall windows, That is buy a coat for my bottom!

---

### Post by jerome1232 on 2009-03-07
chkdsk is a Windows Program, not a Linux program, you need to run chkdsk from within Windows or from within a Windows recovery console.

---

### Post by pvfjr on 2009-03-08
> **halfling85 said:**
> Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

This just worked for me with Intrepid and a Calvary 1TB external USB drive.  Thanks a bunch!

---

### Post by neophytepwner on 2009-03-13
Alright, so I switched to Ubuntu after my comp died completely to several hundred viruses in a spyware attack from hell. 
Needless to say I was unhappy, but I had been thinking of switching to linux for years, due to years of terrible windows experiences (you don't want to know how many computers I have had to reformat due to windows crashing and hardware compatibility issues.  
I could rant all day, but I am here because I have over 200gb of music that I need to access on my 250g seagate IDE OEM HDD via linux. It NTFS formatted and apparently linux has a different way of accessing USB devices (whatever I'm cool with that), except for the fact that I get the same bloody error message that the system cannot Mount the volume, blah blah.  I don't know how to force mount it, I have been browsing these forums for a solution and I came across Halfling's post.  I gave it a shot, but to now avail.  Here is the message I get from terminal:

peter@peter-laptop:~$ sudo ntfsfix /dev/sbd1
Failed to determine whether /dev/sbd1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

---

### Post by Volt9000 on 2009-03-15
Thanks, halfling85!

I tried what you suggested on my WD external 1TB and it worked like a charm!

Using 8.10 Intrepid Ibex.

---

### Post by Wezel on 2009-03-22
Thanks a bunch ! Worked perfectly

---

### Post by slick1a on 2009-03-23
sorry to jump on the band wagon guys , to save time [http://ubuntuforums.org/showthread.php?p=6942190#post6942190](http://ubuntuforums.org/showthread.php?p=6942190#post6942190)

having similar issues with mounting an external drive i tried to mount in win2k ....it will boot into an xp machine but not in my linux machine ...why ?

pls help.

---

### Post by itsme_n8 on 2009-03-24
> **halfling85 said:**
> Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

Halfling... freakin beautiful!  Thanks so much for this post.

---

### Post by Blanchard on 2009-04-08
I was able to fix my issue with my iOmega external drive thanks to Halfling's commands;

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1

I just had to make sure my netbook was connected to the Internet.  This forum is really useful!

---

### Post by battleshipterry on 2009-04-17
cannot mount drive
cannot obtain lock on media .hal-mtab ubuntu

 I had the above error show up when I tried to mount a different drive (additional and USB stick drive) I searched for help but there was no recent data, but a old post on a different forum led me to Wine problem so I removed Wine and Ubuntu now mounts other drives.:D

---

### Post by Buzzygirl on 2009-04-17
> **halfling85 said:**
> Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

... 

Halfling

Halfling,

Thank you so much! This solution worked great for me. I was having troubles getting an NTFS Iomega eGo 250 gb external HD to mount, and this solution fixed it. 

This is why I love the Ubuntu forums... there is so much knowledgeable and friendly help here. I don't post here much because most of the time, a quick search will locate what I need to solve a problem. So I'm making it a point from now on to *publicly* thank whomever posts a solution to a problem I'm having with Ubuntu.

---

### Post by nichpakaich on 2009-04-24
Right now, I'm doing what halfling85 suggested (running the ntfsfix).. and then, the process started:
```
Mounting volume... Did not find any restart pages in $LogFile and it was not empty.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... 

```
after a long waiting, it's done.. But still, the external drive cannot be mounted.

Any other bright solution in here? I'd be thankful.

---

### Post by &#24859; am best on 2009-04-26
I've tried Halfling's suggestion but it comes out with this error:

```

Refusing to operate on read-write mounted device /dev/sde1.

```

any help? :(

---

### Post by telmac on 2009-04-26
I had a similar problem, a family friend died and I enherited his external hard drives, there was an old 250 gb seagate, I do not know what the model is, but the serial number is 5ND1PPEN, that did not work, and although this may not matter, it is not seagate because there is a newer seagate that works fine with it, and it can't be that it is too old because the is an older 120 gb WD.

---

### Post by slick1a on 2009-04-28
heres what i did and got :

Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_GB
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                          
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages                        
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "nfts-3g"
Couldn't find any package whose name or description matched "nfts-3g"
The following packages are unused and will be REMOVED:
  localechooser-data 
The following packages have been kept back:
  acpid libfreetype6 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 81.9kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 171879 files and directories currently installed.)
Removing localechooser-data ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
slick@slick-desktop:~$ sudo apt-get install ntfs-3g ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
ntfs-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by slick1a on 2009-04-28
after then trying :

ntfsfix /dev/mdo     >    sudo apt-get install ntfsprogs

i got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libntfs10
The following NEW packages will be installed
  libntfs10 ntfsprogs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 391kB of archives.
After this operation, 950kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main libntfs10 2.0.0-1ubuntu2 [122kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main ntfsprogs 2.0.0-1ubuntu2 [269kB]
Fetched 391kB in 1s (242kB/s)     
Selecting previously deselected package libntfs10.
(Reading database ... 171872 files and directories currently installed.)
Unpacking libntfs10 (from .../libntfs10_2.0.0-1ubuntu2_i386.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Setting up libntfs10 (2.0.0-1ubuntu2) ...

Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by slick1a on 2009-04-28
which is all because of:

$MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sdf1': input/output error NTFS is either inconsistant, or you have hardware faults, or you have SoftRAID/FakeRAID hardware. In the first case run chdsk /f on windows then reboot Windows TWICE.The useage of the /f parameter is very important! if you have SoftRAID/FakeRAID then you must first activate it and mount a different device under the /dev/mapper directory, (e.g. /dev/mapper/nvidia_eahaabcc1).

---

### Post by slick1a on 2009-04-28
still no joy , i guess thats a 320gig external drive wasted , as i can only use it on a windows machine - gutted i am.

---

### Post by slick1a on 2009-04-28
Bus 003 Device 006: ID 0d49:3200 Maxtor   < this will not mount <
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000

---

### Post by mic98989 on 2009-05-17
Thank you so much Halfling85 that was just what i needed. i had to install ntfs-3g first in my system, but then I did your fix and bam the external was mounted and now files are flowing...Thanks :)

---

### Post by cynicalcylon on 2009-05-22
I've had this exact problem and I just wanted to say thank you, Halfling, very much for the brilliant instructions (below).
Worked like a charm!

> **halfling85 said:**
> Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

---

### Post by Narchya on 2009-10-23
> **farhado said:**
> Unfortunately after executing 

[html]sudo ntfsfix /dev/sdb1[/html]I receive this message:

[html]Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.[/html]I tried 
chkdsk --help
but it says:

I have this problem aswell.

I just installed Ubuntu 8.04 with hardly any software added to it. My external hard-drive is an iOMEGA and works fine on my other PC with Ubuntu 9.04. However I am running a 64 bit PC and I encountered problems with the generic 9.04., so I installed 8.04 on this one. The computer does recognize the hard-drive in the "Places" dropdown in Ubuntu, but not in the "media" file.

---

### Post by Narchya on 2009-10-24
Just upgraded to 8.10

No juice. 

Any help will be greatly appreciated and digitally awarded with hugs ;).

---

### Post by iheartmuseums on 2009-10-25
> **halfling85 said:**
> Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

Thank you so much for this fix, it worked like a charm for me when my external drive wasn't mounting. Whoo!

---

### Post by mistypotato on 2010-01-24
> **halfling85 said:**
> Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling



[B]This also worked for me.
Thanks![/B]

---

### Post by bnsmith001 on 2010-08-02
Tried the suggestion in #2. then saw the typo.

> Quick thought, which might help: is nfts-3g installed on your system? From terminal

```
sudo aptitude update && sudo aptitude install nfts-3g
```

If it tells you the program is already installed, then my thought isn't any good. If it installs the app and its dependencies, then after you are back to the prompt, try the mount command again. Good luck.

Should be ...

> Quick thought, which might help: is **ntfs-3g** installed on your system? From terminal

```
sudo aptitude update && sudo aptitude install **ntss-3g**
```

If it tells you the program is already installed, then my thought isn't any good. If it installs the app and its dependencies, then after you are back to the prompt, try the mount command again. Good luck.

I saw my error messages go by, and noticed that **nfts** is not **ntfs**.

Hopefully, other newbies (like me) weren't confused by this typo.

Peace.

---

