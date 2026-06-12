---
title: "Changing NTFS hdd owner from root to..."
date: 2012-10-16
forum: General Help
---

### Post by Naike on 2012-10-16
So I wanted to make my 2TB hdd mount automatically at boot and the official help page suggested to use a program called pysdm.
I downloaded it, and used the assistant/wizard for the custom settings.

Then I started wondering why my music player can't access the files, and sure enough the owner of this device (dev/sdc1) is root, and I can't change it back to naike (my username). Not even when starting nautilus as root (it just pops back to root after a sec).

Someone on the net suggested trying to chown the device but that did pretty much nothing (I'm still fine using the hdd with nautilus when logged as root).

How can I change the owner back to myself?

---

### Post by Naike on 2012-10-16
Any ideas?

---

### Post by Slim Odds on 2012-10-16
You don't need to mess with the device (/dev/...), you need to look at the mount point (/media/..., or wherever it's mounted).

P.S. Also, relax... 26 minutes between posts? This isn't IM.

---

### Post by Naike on 2012-10-16
Ah okay.
Well anyway, I've tried to edit my etc/fstab with the program and manually without success.

This is what it currently looks like:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid              0  0  
# / was on /dev/sdb6 during installation
UUID=1fb52f17-fb50-43d5-afc2-f285db6306ed  /            ext4  errors=remount-ro                0  1  
# /home was on /dev/sdb7 during installation
UUID=c5ebc991-0e2c-4f39-97c3-9d278b5c8250  /home        ext4  defaults                         0  2  
# swap was on /dev/sdb5 during installation
UUID=1bf028ea-cff0-4737-81c2-d314885e2e3f  none         swap  sw                               0  0  
/dev/sdc1                                  /media/sdc1  ntfs  nls=iso8859-1,rw,umask=000,user  0  0  
```

It's the last one.
Currently, it's configured in the way you see there, but I've tried other options as well (to the point where I can unmount it but not mount it lol)

I guess this file also affects the mount point (/media)?

---

### Post by Slim Odds on 2012-10-16
> **Naike said:**
> Ah okay.
Well anyway, I've tried to edit my etc/fstab with the program and manually without success.

This is what it currently looks like:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid              0  0  
# / was on /dev/sdb6 during installation
UUID=1fb52f17-fb50-43d5-afc2-f285db6306ed  /            ext4  errors=remount-ro                0  1  
# /home was on /dev/sdb7 during installation
UUID=c5ebc991-0e2c-4f39-97c3-9d278b5c8250  /home        ext4  defaults                         0  2  
# swap was on /dev/sdb5 during installation
UUID=1bf028ea-cff0-4737-81c2-d314885e2e3f  none         swap  sw                               0  0  
/dev/sdc1                                  /media/sdc1  ntfs  nls=iso8859-1,rw,umask=000,user  0  0  
```It's the last one.
Currently, it's configured in the way you see there, but I've tried other options as well (to the point where I can unmount it but not mount it lol)

I guess this file also affects the mount point (/media)?
It definitely affects /media/sdc1 (mount point) because that is where is will mount /dev/sdc1 (file system)

/media/sdc1 is  the point that you need to determine the access rights and ownership.

---

### Post by Naike on 2012-10-16
Ok I tried something.
I made a new test mount point, and I got the same problem.
Well I then made the old sdc1 mount point and reconfigured fstab back from the test configuration, and before I mounted /media/sdc1, I changed the permissions as root (with nautilus) to naike (my user).

But as soon as I mount the device to my mount point, the permissions change from naike to root, and I can only mount/unmount the device via root privileges.
This doesn't happen with other devices, only this one, the problem appeared after I changed the /etc/fstab file with pysdm (store device manager).
I've changed the settings back to defaults (and loaded the backup) many times but still I can't mount or unmount the device without root privileges.

---

### Post by oldfred on 2012-10-16
With NTFS you cannot change it from root, but you give ownership & permissions when you mount it. NTFS does not support LInux ownership nor permissions. 

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

More details:
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Naike on 2012-10-16
Thanks for the answer, but I don't think that's my problem.
I can use the device just fine after I've mounted it via the terminal (sudo mount /media/sdc1), I can read and write etc.

The issues here is that I can't mount it via nautilus (unless I start it with root privileges), nor can I unmount it the same way.
It works with all other NTFS devices I have just fine, and it used to work before something happened.

---

### Post by oldfred on 2012-10-16
Did you try with these settings? And UUIDs is prefered as external devices may not always be the same or always sdc, UUID will not change.

defaults,nls=utf8,umask=000,uid=1000,windows_names

Also you have to unmount before remounting with fstab.

And after editing fstab, run this which should not give any errors if fstab is ok. & it remounts everything in fstab.

sudo mount -a

---

### Post by Naike on 2012-10-16
> **oldfred said:**
> Did you try with these settings? And UUIDs is prefered as external devices may not always be the same or always sdc, UUID will not change.

defaults,nls=utf8,umask=000,uid=1000,windows_names

Also you have to unmount before remounting with fstab.

And after editing fstab, run this which should not give any errors if fstab is ok. & it remounts everything in fstab.

sudo mount -a

Hi, no, I actually found my answer here: 
[http://askubuntu.com/questions/178270/only-root-can-mount-why](http://askubuntu.com/questions/178270/only-root-can-mount-why)

> If you want to be able to manually mount and unmount the drive from Nautilus, just remove the line altogether, or comment it out with a #. That will leave it up to Nautilus to mount/unmount it, which works better in that case.

I commented out my sdc1 line all together, and now it works properly like before, I guess if I want it to automount I have to use fstab and not be able to unmount it from nautilus.

Anyway, thanks for the help.

---

