---
title: "USB Won't unmout"
date: 2016-12-16
forum: General Help
---

### Post by box02-0 on 2016-12-16
Ubuntu 14.04   32 bit

Hi.

I have a 16gb usb3 formatted to ntfs. I can copy data to the stick, but can't  "eject" or "safely remove drive". When I try to "eject" or  "safely remove drive" the usb icon on the desktop disappears, but the usb icon in the launcher remains.

It does not appear to be data sensitive, and I know there is no file in use on the usb.

When I get in this state (usb icon remains in launcher after "eject" or "safely remove"), I try a  "sudo umount /dev/sdb1" and I get "umount: /media/mg/usb: not found".

One time I got an "unable to stop drive" message when I try to "safely remove", but this happened only once.

When I am in this state, data on the stick is not useable. If I pull the usb stick out and reinsert, I get:
Error mounting /dev/sdb1 at /media/mg/USB 16gb NTFS: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/mg/USB 16gb NTFS"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. 

I must reformat with Gparted.

The problem is that the system is not flushing out the data and cannot unmount properly

I've tried twiddling the asus BIOS to no avail. USB settings are currently:
Legacy Support:  Enabled  
Intel XHCI Mode:  Smart Auto
EHCI Hand Off:  Disabled

Strangely enough, if I format the usb to FAT32, it works just fine.

Any thoughts would be greatly appreciated.

Thanks,

M..

---

### Post by westie457 on 2016-12-16
You could try issuing the 'sync' command in the terminal to flush the buffers to the usb stick.
see 'man sync' for more info.

Another option when you get the mounting error is to plug into a Windows machine and let Windows run 'chkdsk' on the usb stick.

---

### Post by sudodus on 2016-12-17
Please run the following commands in a terminal window when the USB stick is plugged in, and post the results.

```
df
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
sudo mount
```

It will help us understand the situation and give help. Otherwise we can only guess.

-o-

Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

### Post by box02-0 on 2016-12-17
Hi.

Here is the requested output. I was able to copy a few files to the usb and properly eject. So the usb is AOK at this point:

```

**mg@ubuntu:~$ df**
Filesystem     1K-blocks     Used Available Use% Mounted on
udev            16394936        4  16394932   1% /dev
tmpfs            3282184     1592   3280592   1% /run
/dev/sda4       41767916 33976568   5646596  86% /
none                   4        0         4   0% /sys/fs/cgroup
none                5120        0      5120   0% /run/lock
none            16410912      116  16410796   1% /run/shm
none              102400       48    102352   1% /run/user
/dev/sdb1       15137788  2162624  12975164  15% /media/mg/usb


**mg@ubuntu:~$ sudo lsblk -f**
NAME   FSTYPE LABEL                 MOUNTPOINT
sda                                 
&#9500;&#9472;sda1 ntfs   Sys Res               
&#9500;&#9472;sda2 ntfs   Win8 & Apps           
&#9500;&#9472;sda3                              
&#9500;&#9472;sda4 ext4   Ubuntu Live           /
&#9500;&#9472;sda5 ntfs   DData                 
&#9500;&#9472;sda6 ntfs   Temp                  
&#9500;&#9472;sda7 ntfs   Virtual Box WIN7      
&#9492;&#9472;sda8 ntfs   Partial DData Backups 
sdb                                 
&#9492;&#9472;sdb1 ntfs   usb                   /media/mg/usb
sr0                      

**mg@ubuntu:~$ sudo lsblk -m**
NAME     SIZE OWNER GROUP MODE
sda      477G root  disk  brw-rw----
&#9500;&#9472;sda1   350M root  disk  brw-rw----
&#9500;&#9472;sda2   100G root  disk  brw-rw----
&#9500;&#9472;sda3     1K root  disk  brw-rw----
&#9500;&#9472;sda4  40.6G root  disk  brw-rw----
&#9500;&#9472;sda5   200G root  disk  brw-rw----
&#9500;&#9472;sda6     6G root  disk  brw-rw----
&#9500;&#9472;sda7    22G root  disk  brw-rw----
&#9492;&#9472;sda8  56.7G root  disk  brw-rw----
sdb     14.4G root  disk  brw-rw----


**mg@ubuntu:~$ sudo parted -ls**
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  368MB  367MB   primary   ntfs         boot
 2      368MB   108GB  107GB   primary   ntfs
 3      108GB   469GB  361GB   extended               lba
 5      108GB   322GB  215GB   logical   ntfs
 6      322GB   329GB  6441MB  logical   ntfs
 7      329GB   353GB  23.6GB  logical   ntfs
 8      353GB   413GB  60.8GB  logical   ntfs
 4      469GB   512GB  43.6GB  primary   ext4


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.5GB  15.5GB  primary  ntfs


&#9492;&#9472;sdb1  14.4G root  disk  brw-rw----
sr0     1024M root  cdrom brw-rw----


**mg@ubuntu:~$ sudo mount**
/dev/sda4 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=mg)
/dev/sdb1 on /media/mg/usb type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


```


Then I tried copying a few more files onto the usb and tried "safely remove" & "eject". Then I got the "unable to stop drive message". I pulled out the stick, and plugged it back in and got the expected "unable to mount usb". Here is the output of your requested commands when the usb is in the "bad" state:

```

**mg@ubuntu:~$ df**
Filesystem     1K-blocks     Used Available Use% Mounted on
udev            16394936        4  16394932   1% /dev
tmpfs            3282184     1592   3280592   1% /run
/dev/sda4       41767916 33976576   5646588  86% /
none                   4        0         4   0% /sys/fs/cgroup
none                5120        0      5120   0% /run/lock
none            16410912      116  16410796   1% /run/shm
none              102400       52    102348   1% /run/user

[B]
mg@ubuntu:~$ sudo lsblk -f[/B]
[sudo] password for mg: 
NAME   FSTYPE LABEL                 MOUNTPOINT
sda                                 
&#9500;&#9472;sda1 ntfs   Sys Res               
&#9500;&#9472;sda2 ntfs   Win8 & Apps           
&#9500;&#9472;sda3                              
&#9500;&#9472;sda4 ext4   Ubuntu Live           /
&#9500;&#9472;sda5 ntfs   DData                 
&#9500;&#9472;sda6 ntfs   Temp                  
&#9500;&#9472;sda7 ntfs   Virtual Box WIN7      
&#9492;&#9472;sda8 ntfs   Partial DData Backups 
sdb                                 
&#9492;&#9472;sdb1 ntfs   usb                   
sr0                            


**mg@ubuntu:~$ sudo lsblk -m**
NAME     SIZE OWNER GROUP MODE
sda      477G root  disk  brw-rw----
&#9500;&#9472;sda1   350M root  disk  brw-rw----
&#9500;&#9472;sda2   100G root  disk  brw-rw----
&#9500;&#9472;sda3     1K root  disk  brw-rw----
&#9500;&#9472;sda4  40.6G root  disk  brw-rw----
&#9500;&#9472;sda5   200G root  disk  brw-rw----
&#9500;&#9472;sda6     6G root  disk  brw-rw----
&#9500;&#9472;sda7    22G root  disk  brw-rw----
&#9492;&#9472;sda8  56.7G root  disk  brw-rw----
sdb     14.4G root  disk  brw-rw----
&#9492;&#9472;sdb1  14.4G root  disk  brw-rw----



**mg@ubuntu:~$ sudo parted -ls**
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  368MB  367MB   primary   ntfs         boot
 2      368MB   108GB  107GB   primary   ntfs
 3      108GB   469GB  361GB   extended               lba
 5      108GB   322GB  215GB   logical   ntfs
 6      322GB   329GB  6441MB  logical   ntfs
 7      329GB   353GB  23.6GB  logical   ntfs
 8      353GB   413GB  60.8GB  logical   ntfs
 4      469GB   512GB  43.6GB  primary   ext4


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.5GB  15.5GB  primary  ntfs



**mg@ubuntu:~$ sudo mount**
/dev/sda4 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=mg)



```

I hope this output sheds some light on the problem. Please let me know.

As per westie457, I will try the sync command after I reformat the usb. I will also try formatting as ext4 and see if that makes any difference. 
I prefer to use ntfs as I often have to transfer data to a WIN7 system.


Thanks for your help.

M....

---

### Post by sudodus on 2016-12-17
> **box02-0 said:**
> Hi.

Here is the requested output. I was able to copy a few files to the usb and properly eject. So the usb is AOK at this point:

```

**mg@ubuntu:~$ df**
Filesystem     1K-blocks     Used Available Use% Mounted on
...
/dev/sdb1       15137788  2162624  12975164  15% /media/mg/usb

**mg@ubuntu:~$ sudo lsblk -f**
NAME   FSTYPE LABEL                 MOUNTPOINT
...
sdb                                 
&#9492;&#9472;sdb1 ntfs   usb                   /media/mg/usb
sr0                      

**mg@ubuntu:~$ sudo lsblk -m**
NAME     SIZE OWNER GROUP MODE
...
sdb     14.4G root  disk  brw-rw----

**mg@ubuntu:~$ sudo parted -ls**
...
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.5GB  15.5GB  primary  ntfs

**mg@ubuntu:~$ sudo mount**
...
/dev/sdb1 on /media/mg/usb type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```

Then I tried copying a few more files onto the usb and **[COLOR="#cc0000"]tried "safely remove" & "eject". Then I got the "unable to stop drive message". I pulled out the stick, and plugged it back in and got the expected "unable to mount usb"[/COLOR]**. Here is the output of your requested commands when the usb is in the "bad" state:

... [and the drive is not mounted 'in the "bad" state']

I hope this output sheds some light on the problem. Please let me know.

As per westie457, I will try the sync command after I reformat the usb. I will also try formatting as ext4 and see if that makes any difference. 
I prefer to use ntfs as I often have to transfer data to a WIN7 system.

Thanks for your help.

M....

I see that at first the drive is mounted like it should, but not after unplugging it. I think the problem is that it was not unmounted correctly, so the file system was damaged. Maybe it needed even longer time to flush the buffers, but I think more likely there was some problem, that the write operations could not finish because of some error.

Because it is a Windows file system, I would use a Windows tool to repair the file system *and* check for bad blocks,

```
chkdsk X: /f
```
```
chkdsk X: /r
```

See this link for more details, [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

You can also try to unmount the partition with the following command instead of the 'eject command':

```
sudo umount /dev/sdb1
```

and wait for the prompt to return. Do not unplug the drive until the prompt has returned. If it 'never' returns or if there is an error message, please *reboot* the computer and check if the file system 'survived'.

---

### Post by box02-0 on 2016-12-17
Hi.

ext4 seems to work fine (had to change permissions), as does fat32.

I reformatted to ntfs, copied data, and tried "sudo umount /dev/sdb1"
I got NO response from the system. I can type in whatever I want, but the command never properly completes. It is not quite hung or waiting on anything, just off in space somewhere.

I reformatted to ntfs, copied data, and tried "sync"
Once again, I got NO response from the system. I can type in whatever I want, but the command never properly completes.

In both cases, I had to Terminate terminal to get out. This leads to "Close this terminal?  There is still a process running in this terminal" message. What is the system waiting for???


I wonder if this is a permissions problem? If so, I would have thought the system would say "permission denied".

 Is there any way to log each step of the "sync" or "umount" command, sort of like a dmesg ? 


The plot thickens.

M....

---

### Post by box02-0 on 2016-12-17
Hi again.

More news.

I tried the ntfs reformat again. Copied some data. Then "eject" and went for lunch. When I got back, the system finally got back and said "drive successfully ejected". I usually wait a minute or so after I hit "eject" before I give up, but it looks like it takes a whole lot longer. I will try to repeat the process and time how long it takes. 

Why the delay?

M....

---

### Post by box02-0 on 2016-12-17
Hi.

More info:

16:35  Reformat to ntfs, copy data to USB
16:40  Eject usb on the usb desktop icon. It disappears but icon remains on Launcher
16:44  Eject on Launcher usb icon - icon remains
16:48  Go into Nautilus - try to open  USB  - message "Unable to Mount - An operation is already pending" Exit Nautilus
16:50  Message on desktop: USB successfully ejected and launcher Icon disappears. Remove & reinsert USB. Data is AOK

Takes a few seconds to write data to the USB, and about 10 minutes to flush buffers to USB.

Problem only occurs after writing more data. Same problem with another USB stick. 

Seems to be only with ntfs.

Any ideas?

M....

---

### Post by ajgreeny on 2016-12-17
It sounds as if the system is taking a very long time to write to the USB for some reason.

If you try to copy a large file to the USB, eg, an image file such as an ubuntu.iso file do you get a File-operation notification pop up with the speed of file transfer.  I realise that is not the same thing as the speed of writing to the USB but it might remove slow transfer speed from the list of possible causes.

---

### Post by yancek on 2016-12-17
The most common reason I've seen for the original error you posted (ntfs in an inconsistent state) is because a windows 8/10 system is hibernated rather than fully shut down as the default.  You show windows 8 in your post so if you use the flash on windows, make sure you fully shut down the system before using it on Ubuntu.  If you are not using it on windows then it may need a chkdsk from windows.

---

### Post by box02-0 on 2016-12-17
Hi.

ajgreeny: "....do you get a File-operation notification pop up with the speed of file transfer"   YES, and it's really fast.

Maybe it is writing a byte at a time instead of multiblocks???



yancek: "...if you use the flash on windows, make sure you fully shut down the  system before using it on Ubuntu.  If you are not using it on windows  then it may need a chkdsk from windows."

I haven't been using the flash on windows at all for our discussion. All formatting and writing is being done under Ubu 14.04.
I would think chkdsk would find a problem with the flash sine Ubu has not properly flushed the buffers.


So it seems writing to the usb is very slow for ntfs and now I'm finding out that it is also slow for ext4 as well.

Is this a BIOS setup problem? My current setup is:

Legacy Support:  Enabled  
Intel XHCI Mode:  Smart Auto
EHCI Hand Off:  Disabled


M...

---

### Post by sudodus on 2016-12-18
The problem could also be inside the USB pendrive. You could try with another one. This should work fairly well even with a cheap 4GB USB2 pendrive, for example Sandisk Cruzer Blade.

You can monitor the read/write operations with ***iotop*** in another terminal window.

```
sudo apt-get install iotop
```

```
sudo iotop -o
```

Sometimes a USB drive's internal management gets 'overwhelmed' or confused and will work slowly. Eventually it will not work at all, and the drive is read-only. This is sometimes called 'gridlocked'. The next step is that the drive is completely dead. ***It can help to wipe the whole drive***, to overwrite it with zeros, so that the internal management need not keep track of a lot of assignments between logical addresses and physical memory cells.

You can do it with [mkusb](https://help.ubuntu.com/community/mkusb). I use this method when a pendrive is getting slow, and it can restore the write speed to almost the original speed (of the new pendrive). See these links for more details,

[Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by box02-0 on 2016-12-18
Hi.

Here is a summary of what's been happening:

**USB very slow buffer Flush when "Eject"ing  (up to 10 minutes) for NTFS & EXT4 format. Works fine for FAT32. Fails on multiple USB sticks, some of which are brand new.**

Terminal sudo umount /dev/sdb1,  sudo eject /dev/sdb1, sudo umount -f /dev/sdb1  commands yield the same result - slow.



I tried the "iotop -o" command, but had difficulty figuring out what it is doing because the display is going too quickly and I don't know the TID that I am trying to track.

The mkusb is not applicable since I have tried multiple USB sticks, as well as a new Patriot Rage 64gb. Most of the USB sticks I am trying have never even seen a Windows system.

As expected, I have to write some data to the USB for this problem to occur. When I plug in a USB and just read data, I can Eject with no delay since there are no buffers to Flush.

I can't explain why FAT32 formats work fine.

I have an older Ubuntu (12.10) on a DELL computer. I don't remember having this problem on the older machine, but I will put it together, and see what happens on it.

Are there any other Ubuntu params, BIOS params, or USB drivers that I should be looking at???


I really appreciate all the input,

M...

---

### Post by sudodus on 2016-12-18
This is something that has not happened to me, and am using USB pendrives every day, often with ext4 and NTFS file systems. I don't know what is happening, but if I get an idea, I promise to tell us.

Which version of Ubuntu are you running? Maybe you can also describe the computer (brand name and model (or motherboard). Someone reading this might know.

---

### Post by box02-0 on 2016-12-19
Hi.

Ubuntu 14.04 LTS
Asus Z97 pro mother board
Intel I7 4790K Haswell quad core 4 ghz
32GB RAM Corsair Vengeance Pro DDR 1866 Latency

Are the BIOS USB params set up properly? :

   [COLOR=#333300][SIZE=2]Legacy Support: Enabled  [/SIZE][/COLOR] 

 [COLOR=#333300][SIZE=2]Intel XHCI Mode: Smart Auto[/SIZE][/COLOR]

 [COLOR=#333300][SIZE=2]EHCI Hand Off: Disabled[/SIZE][/COLOR]



Here is a copy of etc/mtab after a "good" usb is mounted:
/dev/sda4 / ext4 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=mg 0 0
/dev/sda5 /media/mg/DData fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/mg/USB3\040NTFS\04016gb\040Lexar fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

The usb is /dev/sdb1.


It appears to me that the system is writing one byte at a time, rather than the specified blksize of 4096. 



Thanks for all the input,

M...

---

### Post by sudodus on 2016-12-19
Maybe you should not specify the blocksize, instead let the system set it to whatever it wants to set it.

You can also try with live systems (booted from a USB drive) of 14.04.1 LTS, and 16.04.1 LTS to see if they behave like your installed system.

---

### Post by box02-0 on 2016-12-19
Hi.

How would I remove block size from mtab? I thought mtab is generated by the mount command. How do I tell the system to default the block size for sdb1?

Thanks,

M..

---

### Post by sudodus on 2016-12-20
I find no specified block size in my /etc/mtab. How do you mount these devices?

I suggest that you live systems of 14.04.1 LTS, and 16.04.1 LTS to see if they behave like your installed system. There might be something wrong with your installed system. If all operating systems suffer from this problem, I would suspect a problem with the hardware or the UEFI/BIOS software.

---

