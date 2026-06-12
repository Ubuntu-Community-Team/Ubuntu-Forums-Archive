---
title: "How to delete Read-only file system files"
date: 2008-04-30
forum: General Help
---

### Post by Yangshuo Joe on 2008-04-30
Hi, 

Brand new to Linux - been using Ubuntu Heron for about 3 days now.

Today I put in a flash drive that I had been using in Windows and saw that it had some virus files on it, two .exe and one autorun.inf

I'm pretty sure these aren't any threat to my Linux system (right?) but I still want to clean the drive without having to format.

When I tried to delete them, it said they were read-only system files and couldn't be deleted.

I tried navigating to the file location and running:  

sudo rm filename

But that also didn't work. 

I could go into windows and delete them with an AV scan easy enough, but I'd really like to learn how to delete files like this in Ubuntu.

As I said, I'm brand new at this, so hope this isn't a ridiculous question! I really did try to find the answer in google :confused:

Appreciate any help!

YJ

---

### Post by kdwillia on 2008-04-30
Normally, a Windows Virus will not use an autorun.inf to execute.   If you found these on the pen drive, there is a good chance that they are a program that the pendrive uses in Windows to create a readonly area for "suggested" software.  U3 is a good example of this.

What are the names of the .exe files?

---

### Post by Kevinator on 2008-04-30
Please show us the output of 'ls -al <insert-drive-mount-point-here>' on the drive, and 'mount'.

---

### Post by Yangshuo Joe on 2008-04-30
I hadn't considered that it could be something like U3. The Flash drive is some generic chinese brand and the iafsayr.exe especially gets a lot of chinese language hits on google. I'll try to check more to see if it is something like U3.

I also installed the ClamTk Virus Scan program from synaptic. It gets a hit on the iafsayr.exe but not on the lwkfnpg.exe. Still won't let me delete the one it identifies as a virus though.

The output of ls -al /media/disk/

total 144
drwx------ 7 yuki root 16384 1970-01-01 08:00 .
drwxr-xr-x 4 root root  4096 2008-05-01 07:32 ..
drwx------ 3 yuki root  4096 2001-02-25 18:59 2008
-rwx------ 1 yuki root   169 2008-04-04 13:55 autorun.inf
-rwx------ 1 yuki root 27257 2007-10-17 17:30 iafsayr.exe
-rwx------ 1 yuki root 72583 2008-04-04 14:05 lwkfpng.exe
drwx------ 2 yuki root  4096 2005-01-08 16:33 Recycled
drwx------ 8 yuki root  4096 2005-01-08 16:33 System Volume Information
drwx------ 2 yuki root  4096 2001-02-25 18:47 yuki
drwx------ 2 yuki root  4096 2007-07-08 21:06 yukifamily


and mount gives me:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-386/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/disk type vfat (ro,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


I also opened the .inf file in Writer using the Chinese character set encoding and get:

[AutoRun]
open=iafsayr.exe
shell\open=&#25171;&#24320;(&O)
shell\open\Command=iafsayr.exe
shell\open\Default=1
shell\explore=&#36164;&#28304;&#31649;&#29702;&#22120;(&X)
shell\explore\Command=iafsayr.exe

The first chinese phrase should mean 'open' and the second is something like 'resource manager device'.

Hope this helps..

---

### Post by RATM_Owns on 2008-04-30
FIRST = Opens

SECOND = Resource management

---

### Post by Yangshuo Joe on 2008-05-01
Upon doing a little more testing and research, I realize that the whole drive is read-only. I can't delete any files or add any new ones.

So it seems I am trying to set the drive to be read write.


From /etc/fstab I get:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=0e755c2c-6533-4fc4-b967-dbb9a1522abf / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=2fdcee67-eb9d-4443-a532-7d0d6e37acb0 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0


I also unmounted the usb drive then mounted again and ran a dmesg:

[snip]
[39684.322871] usb 4-2: USB disconnect, address 3
[39690.326010] usb 4-2: new full speed USB device using uhci_hcd and address 4
[39690.502157] usb 4-2: configuration #1 chosen from 1 choice
[39690.512722] scsi6 : SCSI emulation for USB Mass Storage devices
[39690.514564] usb-storage: device found at 4
[39690.514571] usb-storage: waiting for device to settle before scanning
[39695.516407] usb-storage: device scan complete
[39695.519401] scsi 6:0:0:0: Direct-Access     Teclast  Coolflash        7.77 PQ: 0 ANSI: 2
[39695.531392] sd 6:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[39695.536381] sd 6:0:0:0: [sdb] Write Protect is on
[39695.536389] sd 6:0:0:0: [sdb] Mode Sense: 03 00 80 00
[39695.536392] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[39695.548361] sd 6:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[39695.553833] sd 6:0:0:0: [sdb] Write Protect is on
[39695.553840] sd 6:0:0:0: [sdb] Mode Sense: 03 00 80 00
[39695.553843] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[39695.553850]  sdb: sdb1
[39695.560502] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[39695.560572] sd 6:0:0:0: Attached scsi generic sg2 type 0


I also tried the following bit of code I found in another post, but it didn't work and I'm not quite clear on what the error message means:

sudo mount -o remount,rw /media/disk

[mntent]: warning: no final newline at the end of /etc/fstab
mount: block device /dev/sdb1 is write-protected, mounting read-only


Any thoughts on where to go from here?

---

### Post by chrisccoulson on 2008-05-01
```
[39695.553833] sd 6:0:0:0: [sdb] Write Protect is on
```
This might be a silly question, but is there not a write protect switch on the flash drive? As far as your Ubuntu machine is concerned, this device is write protected and will only mount read-only.

---

### Post by Yangshuo Joe on 2008-05-01
haha!

I guess in all the complexities of learning a new operating system, I overlooked the obvious solution - flipped the switch and problem is solved 

:oops:

I guess on the plus side, I learned a lot of new commands and things about file permissions.

Well thanks for asking your 'silly question' chrisccoulson. Otherwise, I would have probably had another sleepless night

Issue solved

---

### Post by kdwillia on 2008-05-01
There is a Mastercard Commercial in Here Somewhere....

Ubuntu Linux.... 0$

Using an older PC and not having to buy a new one.... 0$

Paying for the Co-Pay for your Doctor because you hit yourself in the forehead after you realized you flipped the "Read Only" switch on your Pen Drive.... $25

Not being infected by a Windows Virus because you decided Linux was a better choice and safer.....   PRICELESS

---

### Post by ezsit on 2008-05-01
Since your device is being mounted as:

/dev/sdb1 on /media/disk 

I would do a:

sudo chown username:username -R /media/disk

This command changes ownership of the mountpoint and sets the ownership to your "username." The "username:username" argument specifies the owner and group you wish to set for the mountpoint. The "-R" tells the command to recursively change the ownership and travel through and folders.

Once the ownership is changed for the mountpoint, more than likely, you will be able to delete and edit and save files to the device for the duration of the session it is plugged in. Since the mountpoint gets recreated each time you insert a USB device, the ownership will revert to root each time you plug and unplug USB flash drives.

---

### Post by chrisccoulson on 2008-05-01
> **ezsit said:**
> Since your device is being mounted as:

/dev/sdb1 on /media/disk 

I would do a:

sudo chown username:username -R /media/disk

This command changes ownership of the mountpoint and sets the ownership to your "username." The "username:username" argument specifies the owner and group you wish to set for the mountpoint. The "-R" tells the command to recursively change the ownership and travel through and folders.

Once the ownership is changed for the mountpoint, more than likely, you will be able to delete and edit and save files to the device for the duration of the session it is plugged in. Since the mountpoint gets recreated each time you insert a USB device, the ownership will revert to root each time you plug and unplug USB flash drives.

Just to point out - that won't work (certainly with a FAT or NTFS flash drive). The permissions and ownership are determined by the mount options, and you can't chown or chmod to alter them.

And chown or chmod won't make a read-only volume become read-write. If it's been mounted read-only (as in this case), this is either because the 'ro' option was specified to mount it (in which case, you remount with 'rw' to fix), the volume has errors (in which case, you run fsck to fix), or as in this case, the write protect switch was in the wrong position.

---

### Post by ezsit on 2008-05-03
> Just to point out - that won't work (certainly with a FAT or NTFS flash drive). The permissions and ownership are determined by the mount options, and you can't chown or chmod to alter them.

And chown or chmod won't make a read-only volume become read-write. If it's been mounted read-only (as in this case), this is either because the 'ro' option was specified to mount it (in which case, you remount with 'rw' to fix), the volume has errors (in which case, you run fsck to fix), or as in this case, the write protect switch was in the wrong position.

Thanks. I didn't know this. I only use ext3 on all my external hard drives and flash drives. I use my method all the time for ext3 filesystems and it works just fine. I gave up on MS filesystems when I dumped Windows back in 2005. Sorry.

I realize that the OP already solved their problem, so all this is merely academic now.

---

### Post by chrisccoulson on 2008-05-03
No probs:)

---

### Post by lies on 2009-04-04
> **chrisccoulson said:**
> ```
[39695.553833] sd 6:0:0:0: [sdb] Write Protect is on
```
This might be a silly question, but is there not a write protect switch on the flash drive? As far as your Ubuntu machine is concerned, this device is write protected and will only mount read-only.

And if the flash drive doesn't have a switch?
Mine is a Kingston 2GB flash drive.

---

### Post by majamba on 2009-04-04
rm -rf * 
that will deleate the files run it at own risk

probably you need to be root and then chmod those files to be writable by or you can make chmod 777

and then delete them by using the

rm filename

---

### Post by fabricator4 on 2009-04-04
> **kdwillia said:**
> Normally, a Windows Virus will not use an autorun.inf to execute.   If you found these on the pen drive, there is a good chance that they are a program that the pendrive uses in Windows to create a readonly area for "suggested" software.  U3 is a good example of this.


I just wanted to point out that this is incorrect (sorry! ;-)

There are virus varients such as Sality that infect pen drives by placing a file called system.exe and an autorun.inf script in the root directory.

When these are plugged into another Windoze machine the script is run, and the virus infects the new machine.  This virus actually goes looking for other drive letters to put this rubbish on, so it's possible to infect shared logical devices and drives over a network if they have a drive letter on the infected machine.

If I could, I'd turn autorun off on every XP machine I ever come across.

If you plug an infected pen drive into an Ubuntu machine, it will ask if you want to run the DOS/Windows executable.  The answer is, of course, NO! :-)


Chris.

---

### Post by lies on 2009-04-04
I think there is a problem now, I've copied the files to the HDD and formated the flash drive with NTFS, and now the write speed is only 3.2 MB per second, plus there are 10 MB of used space in it right now but there is nothing in the flash drive, I'm sure this isn't normal for NTFS disks.

---

### Post by Slim Odds on 2009-04-04
> **lies said:**
> I think there is a problem now, I've copied the files to the HDD and formated the flash drive with NTFS, and now the write speed is only 3.2 MB per second, plus there are 10 MB of used space in it right now but there is nothing in the flash drive, I'm sure this isn't normal for NTFS disks.

There is no reason to format a small flash drive with NTFS. It will be slower and have more overhead (both space and speed). Use FAT32.

---

### Post by lies on 2009-04-04
So that's normal... And if I want to save files of more that 1 GB? I really need to, I remember FAT32 cant save those... And that's the reason my 2nd partition cant write more that 33 MB per second?

Thanks

---

### Post by lies on 2009-04-04
Formated the flash drive FAT32 but the write speed is still 3.3 MB per second.
I got this flash drive in 2006 Xmas... but I don't use it often, still think is going to die...:cry:

---

