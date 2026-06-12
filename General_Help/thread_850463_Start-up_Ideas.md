---
title: "Start-up Ideas"
date: 2008-07-05
forum: General Help
---

### Post by Powerman2442 on 2008-07-05
I'm trying to figure out how to do a few different things when I boot into Ubuntu. I would like to make it so Katapult opens when Ubuntu first loads. Is there any guide to setting up start-up programs? Or even a program to help set them.

Also since the combined volume of my Linux install was 15 GB I wanted to use my Windows partition to save large files, like ISO images, etc. I mounted my Windows volume and made a "Link to Linux" shortcut on my desktop. (Linux being a folder on my C: drive within Windows where I store all my ISO images and other Linux downloads) Will I be able to access that Link to Linux folder every time I boot into Ubuntu, or will I have to mount my Windows partition before being able to use the Link to Linux? If so is there any way to make it automatically mount that partition on boot.

Thanks,
Powerman2442

---

### Post by TeoBigusGeekus on 2008-07-05
1)System->Preferences->Sessions
Startup Programs tab. You can take it from here...

2)You can force Ubuntu to automatically mount the volume on boot up by fiddling with your fstab file.
Post us the output of 
```
sudo fdisk -l
```
and the contents of your fstab file
```
sudo gedit /etc/fstab
```

---

### Post by Powerman2442 on 2008-07-05
> **TeoBigusGeekus said:**
> 1)System->Preferences->Sessions
Startup Programs tab. You can take it from here...

2)You can force Ubuntu to automatically mount the volume on boot up by fiddling with your fstab file.
Post us the output of 
```
sudo fdisk -l
```
and the contents of your fstab file
```
sudo gedit /etc/fstab
```

Thanks I found the Startup Programs tab right after I posted.

sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30a0b457

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12636   101489660    7  HPFS/NTFS
/dev/sda2           12637       14593    15719602+   5  Extended
/dev/sda5           12637       14505    15012711   83  Linux
/dev/sda6           14506       14593      706828+  82  Linux swap / Solaris

and

sudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=6639b8b2-1f55-44f0-86fc-f98853119f4c /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda6
UUID=1ecc442a-0e56-42cf-9f95-43d59ff3f241 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by TeoBigusGeekus on 2008-07-05
Sorry, forgotten to tell you to post us the mount point of your window$ partition.
Mount it and post us the output of
```
sudo mount
```
I promise that's the last :lolflag: !

---

### Post by Powerman2442 on 2008-07-05
> **TeoBigusGeekus said:**
> Sorry, forgotten to tell you to post us the mount point of your window$ partition.
Mount it and post us the output of
```
sudo mount
```
I promise that's the last :lolflag: !

Not a problem. By the way the command I used to start Katapult on boot "sudo Katapult" ... will this work? Thanks

sudo mount

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/derek/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=derek)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by TeoBigusGeekus on 2008-07-05
Ok! Add this line at the end of your fstab file
```
/dev/sda1       /media/disk                               ntfs   relatime        0       2
```
reboot and post us what happened...

About the Katapult. It won't work - at least in the way you expect it to work. You will still have to enter your password.

---

### Post by stich0602 on 2008-07-05
Run "sudo gedit /etc/fstab" again, and add this line to the end:

/dev/sda1 /media/disk ntfs-3g defaults 0 2

Save and close. When you reboot into Ubuntu next, the drive should be mounted.

---

### Post by Powerman2442 on 2008-07-06
> **TeoBigusGeekus said:**
> Ok! Add this line at the end of your fstab file
```
/dev/sda1       /media/disk                               ntfs   relatime        0       2
```
reboot and post us what happened...

About the Katapult. It won't work - at least in the way you expect it to work. You will still have to enter your password.

Okay, I added this line and the volume is mounted on reboot or power on. I did notice that it takes a while longer to boot. Does the auto-mounting of my Windows volume cause this?

Thanks,
Powerman2442

---

### Post by Powerman2442 on 2008-07-06
> **stich0602 said:**
> Run "sudo gedit /etc/fstab" again, and add this line to the end:

/dev/sda1 /media/disk ntfs-3g defaults 0 2

Save and close. When you reboot into Ubuntu next, the drive should be mounted.

I edited the /etc/fstab file with TeoBigusGeekus' method and it works but it seems to slow down when booting up. Will your method cause the same thing?

Edit: Can anyone help me with setting the command for Katapult loading on boot?

---

### Post by stich0602 on 2008-07-07
> **Powerman2442 said:**
> I edited the /etc/fstab file with TeoBigusGeekus' method and it works but it seems to slow down when booting up. Will your method cause the same thing?

Edit: Can anyone help me with setting the command for Katapult loading on boot?

Since your partition was created and is maintained by a Windows installation, you probably shouldn't use the relatime option. Try with the defaults option in its place, save and restart. Tell us if this speeds the process up.

Found something that may be of help with Katapult:
[http://ubuntuforums.org/showthread.php?t=369574](http://ubuntuforums.org/showthread.php?t=369574)

---

### Post by Powerman2442 on 2008-07-07
> **stich0602 said:**
> Since your partition was created and is maintained by a Windows installation, you probably shouldn't use the relatime option. Try with the defaults option in its place, save and restart. Tell us if this speeds the process up.

Found something that may be of help with Katapult:
[http://ubuntuforums.org/showthread.php?t=369574](http://ubuntuforums.org/showthread.php?t=369574)

I typed katapult into terminal and got this:

derek@derek-laptop:~$ katapult
kbuildsycoca running...
Ignored duplicate item: Kaffeine
Ignored duplicate item: Windows Wireless Drivers
Ignored duplicate item: Volume Control
Ignored duplicate item: Software Sources
Ignored duplicate item: Printing
Ignored duplicate item: Partition Editor
Ignored duplicate item: Shared Folders
Ignored duplicate item: Update Manager
Ignored duplicate item: Network
Ignored duplicate item: Time and Date
Ignored duplicate item: System Monitor
Ignored duplicate item: Login Window
Ignored duplicate item: Services
Ignored duplicate item: Users and Groups
Ignored duplicate item: Hardware Testing
Ignored duplicate item: Network Tools
Ignored duplicate item: onBoard
Ignored duplicate item: onBoard Settings

And Katapult did load. I am going to make the changed to /etc/fstab first then mess around with having katapult load a boot.

---

### Post by Powerman2442 on 2008-07-15
My Windows partition non longer mounts automatically and I can't manually mount it. Keeps saying "Cannot mount volume -- You are not privileged to mount his volume." Never had a problem before. Any clue?

Thanks,
Powerman2442

---

### Post by cyclobs on 2008-07-15
i did ```
sudo mount -a
```

---

