---
title: "USB Harddrive Won't Let Me Write"
date: 2006-10-30
forum: General Help
---

### Post by MyNameUhBorat on 2006-10-30
My external usb harddrive won't let me even change the Read/Write prefrences. It says I don't have permission. Any ideas?

---

### Post by bswilson on 2006-10-30
> **MyNameUhBorat said:**
> My external usb harddrive won't let me even change the Read/Write prefrences. It says I don't have permission. Any ideas?

Yes.  Use **sudo** to change the privileges.  

```
sudo chmod -R o+rw /path/to/usbdrive
```

---

### Post by konst88 on 2006-10-30
maybe the drive is formated as NTFS. if yes, you cant write on it. convert it to fat32.

---

### Post by jordilin on 2006-10-30
what type of format has your usbdrive?

---

### Post by MyNameUhBorat on 2006-10-30
BSWilson I did what you reccomended and it made changes but it didn't switch so I could write to it.

---

### Post by todds on 2006-10-30
this may seem very simple but i have some usb devices,display this problem all it took was a simple unplug and plug back in and i could then write to them,dont know why it happens but does occasionally....

you have probably already tried this but thought i would post it anyway

regards

todds

---

### Post by MyNameUhBorat on 2006-11-01
Ya I tried that and it didn't work. Ugh I'm so frustrated. It worked fine like 3 days ago.

---

### Post by MyNameUhBorat on 2006-11-02
bump

---

### Post by hueoblue on 2006-11-03
I've been having similar problems with my USB flash stick. I tried changing chmod, changing /etc/fstab/, fdisk to both fat16 and fat 32, and nothing worked.
The only work around I have found, is sudo cp any files you want to transfer onto the USB device. 
It's a pain, because if you make any changes to a file, you have to save it to your harddrive and sudo cp it back onto the flash device.

---

### Post by MyNameUhBorat on 2006-11-03
I don't want to risk reformating the hdd because I have quite a substanial amount of music and other important files.

---

### Post by moore.bryan on 2006-11-03
[I]this might sound silly and insulting, but it's not meant to be, so please bear with...
(1) is it mounted; meaning, can you see the files already on it?
(2) if so, try ```
sudo chmod 777 /media/usbdisk
``` now, that assumes your usb drive is at /media/usbdisk.  if it's somewhere else, just put the location in instead.  chmod 777 give everyone read, write, and execute abilities for the disk.
[/I]

---

### Post by dannyboy79 on 2006-11-03
> **moore.bryan said:**
> [I]this might sound silly and insulting, but it's not meant to be, so please bear with...
(1) is it mounted; meaning, can you see the files already on it?
(2) if so, try ```
sudo chmod 777 /media/usbdisk
``` now, that assumes your usb drive is at /media/usbdisk.  if it's somewhere else, just put the location in instead.  chmod 777 give everyone read, write, and execute abilities for the disk.
[/I]

that won't work, I have been seeing this problem over and over lately, it is the way that the system automatically mounts usb drives. they are always owned by root and only read access. you need to umount it, then chown and chmod the folder you want to mount it to, then when you mount it, you need to use these options if it's fat32, vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000. if it's ntfs, then obvisouly that's your problem cause unless you have a special driver or whatever, you can't write to ntfs.

---

### Post by MyNameUhBorat on 2006-11-03
dannyboy I don't quite understand. I'm sorry I'm really very new to this.

---

### Post by dannyboy79 on 2006-11-03
alright, well please tell me what you don't understand.

---

### Post by hueoblue on 2006-11-03
I've been having a very similar problem, as dannyboy mentioned...
The solution he figured out is here... 

[http://www.ubuntuforums.org/showthread.php?t=291849&page=2](http://www.ubuntuforums.org/showthread.php?t=291849&page=2)

to edit your /etc/fstab

```
sudo gedit /etc/fstab
```

then you can insert the line, with the appropriate parameters changed and it should work, as long as your file system isn't NFTS

---

### Post by dannyboy79 on 2006-11-03
or, if it still doesn't work, try this:
finally it is working and all seems well (at least it seems like that at this late hour of the night)
anyway for anyone conserned this is how i did it:

1. systool -vb scsi | grep vendor

get vendor id - in my case HDT72252

2. sudo nano /etc/udev/rules.d/z90-philips.rules

# external HD 1
BUS="scsi", SYSFS_vendor="HDT72252*", NAME="PHILIPS%n"", run+="/bin/mount -a"

3.sudo nano /etc/fstab

/dev/PHILIPS1 /media/PHILIPS1 vfat,ext2 user,auto,rw 0 0
/dev/PHILIPS2 /media/PHILIPS2 vfat,ext2 user,auto,rw 0 0

thanks again for the earlier suggestion it put me on the right track and all was missing was to add ", run+="/bin/mount -a" to the rules file

I am sorry, I just looked into this further and realized that I don't understand how this person knew that he needed to edit z90-philips.rules? so disregard this

---

### Post by moore.bryan on 2006-11-03
> **dannyboy79 said:**
> that won't work, I have been seeing this problem over and over lately, it is the way that the system automatically mounts usb drives. they are always owned by root and only read access. you need to umount it, then chown and chmod the folder you want to mount it to, then when you mount it, you need to use these options if it's fat32, vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000. if it's ntfs, then obvisouly that's your problem cause unless you have a special driver or whatever, you can't write to ntfs.
*i was having the same problem and it solved it for me.  sorry to hear so many others are running into issues where that doesn't solve!  good luck.*

---

### Post by givré on 2006-11-03
You might remove all reference about your external device from /etc/fstab.
fstab is for static device.
removable device are configure when plug.

---

### Post by dannyboy79 on 2006-11-06
> **givré said:**
> You might remove all reference about your external device from /etc/fstab.
fstab is for static device.
removable device are configure when plug.

as I posted in the other thread, your statement is NOT correct for these people.

---

### Post by givré on 2006-11-06
> **dannyboy79 said:**
> as I posted in the other thread, your statement is NOT correct for these people.

*******************

---

### Post by givré on 2006-11-06
Sorry dude, that was over reacting.
Let's talk more seriously about that.

---

### Post by dannyboy79 on 2006-11-06
> **givré said:**
> Sorry dude, that was over reacting.
Let's talk more seriously about that.

Yes it was. I accept your apology. Now, if you have a solution that will work for these types of people than let's hear it but to just say, remove your fstab entry for removable devices and it'll work isn't working according to these people. You say it should be automatic but it isn't working for these people so what should they do other than what I have suggested?

---

### Post by givré on 2006-11-06
> **dannyboy79 said:**
> Yes it was. I accept your apology. Now, if you have a solution that will work for these types of people than let's hear it but to just say, remove your fstab entry for removable devices and it'll work isn't working according to these people. You say it should be automatic but it isn't working for these people so what should they do other than what I have suggested?
Nobody asked him to remove his USB device from fstab. 
The first things to do when you see such situation, is simply to ask for fstab, and `sudo fdisk -l`.
- If there is something in fstab about his USB device, just tell him to remove it.
- If there is nothing in it, and that it still fail, which is rather uncommon and mean than automount will fail in any way, even with a line in fstab, you can ask him some debug info :
```
export PMOUNT_DEBUG=1
pmount-hal /dev/sda1
```
or more simply but less complete:
```
pmount -d /dev/sda1
```

But in any way, you have to be sure that there is nothing in fstab before proposing an alternative solutions. In the majority of the case, those kind  of problem are due to that.

---

### Post by MyNameUhBorat on 2006-11-20
Well the hard drive I have is an old Windows XP partition, so technically speaking if I were to install Ubuntu on it and delete the old partition then I wouldn't have the problem anymore. I have an old desktop where I'm writing all the files from the HD now so deleting the windows partition isn't a problem.

---

### Post by MyNameUhBorat on 2006-11-21
*a polite bump*

---

### Post by givré on 2006-11-21
Hi,

please, give me the output of (when you removable device is plug):
```
sudo fdisk -l
```
and
```
more /etc/fstab
```

Thanks

---

### Post by MyNameUhBorat on 2006-11-21
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris
jeremy@jeremy-laptop:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
jeremy@jeremy-laptop:~$

---

### Post by givré on 2006-11-21
Hum, you didn't plug your usb device, no ?

---

### Post by MyNameUhBorat on 2006-11-27
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16708   134206978+   7  HPFS/NTFS
jeremy@jeremy-laptop:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


Sorry for the delay. Here it is.

---

### Post by givré on 2006-11-27
Your external device is NTFS so you are not able to write to it out of the box since the driver ship with ubuntu is read only.
If you want to write to it, have a look at :
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by MyNameUhBorat on 2006-11-27
It's really strange because I was able to write no problem and then one day it just said I didn't have permission to write anymore. So will following that guide delete all the files on the hard drive?

---

### Post by MyNameUhBorat on 2006-12-02
bump

---

### Post by givré on 2006-12-02
> **MyNameUhBorat said:**
> It's really strange because I was able to write no problem and then one day it just said I didn't have permission to write anymore. So will following that guide delete all the files on the hard drive?
Since it's NTFS, it's impossible that you could get write support by default.
To get it working, just add a repo to your sources.list :
For dapper :
```
deb http://flomertens.keo.in/ubuntu/ dapper main main-all
```
For edgy :
```
deb http://flomertens.keo.in/ubuntu/ edgy main-all
```
Save the file, update and upgrade,
Install ntfs-3g :
```
sudo apt-get install ntfs-3g
```
Plug and that should work.

---

### Post by strabes on 2006-12-02
you guys forgot the -R on the chmod command which makes it RECURSIVE meaning all the subdirectories are also chmodded to 777. ```
sudo chmod -R 777 /media/nameofusb
```

---

### Post by givré on 2006-12-02
> **strabes said:**
> you guys forgot the -R on the chmod command which makes it RECURSIVE meaning all the subdirectories are also chmodded to 777. ```
sudo chmod -R 777 /media/nameofusb
```
That's totaly useless for fat & ntfs filesystem.

---

