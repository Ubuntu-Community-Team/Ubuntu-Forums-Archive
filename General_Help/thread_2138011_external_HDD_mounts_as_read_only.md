---
title: "external HDD mounts as read only"
date: 2013-04-22
forum: General Help
---

### Post by mkendrick on 2013-04-22
(solution in last post)

Hello, 
I'm having trouble mounting an external HDD on a raspberry pi running raspbian (yes I know this is an ubuntu forum). I'm connecting to the RPi by ssh from my ubuntu machine and thus can only make changes via command line.

From 'sudo fdisk -l' the HDD has the following filesystem:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

```

In '/etc/fstab' I have set the disk as following:
```
/dev/sda1       /mnt/ehdd       ntfs    defaults        0       0

```
Doing 'sudo mount /dev/sda1 /mnt/ehdd' gives:
```
mount: warning: /mnt/ehdd seems to be mounted read-only.

```

I've found a similar post on here ([http://ubuntuforums.org/showthread.php?t=1946755](http://ubuntuforums.org/showthread.php?t=1946755)) which mentioned journalling being a problem. In my case the HDD was originally formatted as NTFS by win7 (iirc), I use this HDD on another system and it's automatically mounted correctly and has been usable.

Doing 'mount' gives the following for the HDD:
```
/dev/sda1 on /mnt/ehdd type ntfs (ro,relatime,uid=0,gid=0,fmask=0177,dmask=077,nls=utf8,errors=continue,mft_zone_multiplier=1)

```

Doing 'chmod' or 'sudo chmod' give the error:
```
chmod: changing permissions of `/mnt/ehdd': Read-only file system

```
Finally, in the linked thread the OP had found a way of changing the journalling option using the command:
```
[COLOR=#000000]sudo /usr/sbin/diskutil disableJournal /Volumes/MyDisk[/COLOR]
```

Which for me returns:
```
sudo: /usr/sbin/diskutil: command not found

```
Hopefully that explains the situation, sorry if I'm missing something simple (I wouldn't mind this being the case)
Martyn

---

### Post by mkendrick on 2013-04-22
update: I tried changing the mount type to 'ntfs-3g' in '/etc/fstab' which returned:
```
mount: unknown filesystem type 'ntfs-3g'
```

The same error is encountered when running 'sudo mount -t ntfs-3g /dev/sda1 /mnt/ehdd'

---

### Post by mkendrick on 2013-04-22
Further update:
doing:
```
sudo mount -o remount,rw '/dev/sda1'
```

returns:
```
mount: cannot remount block device /dev/sda1 read-write, is write-protected
```#

Using the program 'hdparm' does not solve the problem:
```
sudo hdparm -r0 /dev/sda1

/dev/sda1:
 setting readonly to 0 (off)
 readonly      =  0 (off)

```

but then:
```
$ sudo umount /dev/sda1
$ sudo mount -a
mount: warning: /mnt/ehdd seems to be mounted read-only.
```

---

### Post by SeijiSensei on 2013-04-22
This sounds like the physical device itself is set to be read-only.  Is there a physical switch that does that, or perhaps some setting in the device's bios?

What do you see if you run "/sbin/fdisk /dev/sda" and look at the device's partitions, etc.?

---

### Post by mkendrick on 2013-04-22
It's odd as it only does this on this particular machine and works fine on others. There are no physical switches on the device it's just plug and play powered usb external HDD. 
Running [COLOR=#000000]"/sbin/fdisk /dev/sda" returns:
[/COLOR]```
$ sudo /sbin/fdisk /dev/sda

Command (m for help):
```

i.e. it doesn't return anything unless I was supposed to give it a command.


Using the print command I get the same output as in the original post:
```
[COLOR=#000000][FONT=Ubuntu Mono]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
/dev/sda1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT
```

---

### Post by mkendrick on 2013-04-23
Have now solved. 

This turned out to be a more raspbian problem than linux general problem. To enable the drive to be mounted it required that it was mounted with ntfs-3g. When I tried this it didn't work since it was not installed. 
To install do 
```
sudo apt-get install fuse ntfs-3g
```

then you may mount the drive manually, assuming the HDD is on sda and partition sda1:
```
sudo ntfs-3g /dev/sda1 /mnt/HDD
```
Where you may chnage 'HDD' to whatever you want your HDD to be called.

To get this to mount automatically at boot you need to do: (you can use any text editor you like, I used nano as I was configuring via ssh)
```
sudo nano /etc/fstab
```

Add the following line:
```
/dev/sda1       /mnt/HDD       ntfs-3g defaults        0       2
```

here the number 2 at the end is for auto mounting. Also if you changed the HDD name from 'HDD' you should change it here also. Remember to use tabs for breaks and not spaces.

Thanks for the help, hope this helps someone else aswell

---

