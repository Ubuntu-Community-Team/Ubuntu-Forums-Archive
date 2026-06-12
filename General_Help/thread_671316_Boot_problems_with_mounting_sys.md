---
title: "Boot problems with mounting /sys"
date: 2008-01-18
forum: General Help
---

### Post by almandris on 2008-01-18
I booted up my Dell 131L laptop this morning and it fails to boot up properly.  I am running a version 7.10 right now that had been upgraded from 7.04.  The error I got at first was something to do with GDB and Gnome not starting up, but that was because of another error with the /sys directory.  I dont know why this happned.  I finally got the system up and running in recovery mode with a terminal and it doesn't look good.  The main problem is this error " mouting /sys on /root/sys failed"

Somehow my /sys directory is not a directory anymore instead it is a symlink (that looks odd to me) like this: "sys -> document-print-preview.png".  I dont know how or why this happned, as I would have not done anything like this to my system.  I hadn't done any upgrades recently so I am not sure it was a problem related to that.  

Does anyone know what might have happened? 

I don't know much more than the basics about symlinks or the file systems setup so I don't know if there is a way to look into this.  Is there a way to look for or recover my /sys directory that anyone knows of?


Just looking for ideas before i have to nuke the system to get it up again.  Thanks

---

### Post by atoponce on 2008-01-18
Will you paste your /etc/fstab here please?

---

### Post by chrisccoulson on 2008-01-18
There isn't anything to recover in /sys anyway, as it's a volatile filesystem - which means it gets re-created when you boot. Your problem is obviously related to the fact that /sys is no longer a directory, but instead a sym-link to another file.

The fix should just be to delete the symlink and recreate the /sys empty folder. Whether you can do this from recovery mode or whether you have to use the live CD will dictate the method for doing this.

Does recovery mode still work? (I'd be surprised if it did)

If it does, it should just be a case of doing:
```
rm /sys
mkdir /sys
reboot
```
...but only if you are absolutely positive that /sys hasn't mounted correctly. If you want to make sure, do a cat /etc/mtab. If you have a line that looks like this:
```
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
```
...then /sys is still mounted and you have another issue. Also, if you can access recovery mode, you'll be able to post your /etc/fstab, as suggested above by atoponce. Do this before messing about just in case there is something really wrong with your fstab.

If you need to use the live CD, do the following from a terminal within the live CD environment:
```
sudo mkdir /media/target
sudo mount -t ext3 /dev/xxxx /media/target
sudo rm /media/target/sys
sudo mkdir /media/target/sys
```
where /dev/xxxx is your root filesystem (if you know this). If not, you'll have to have a look at the output of fdisk -l and work out which partition it it. If you're not sure, post the output here and I'll try and help/

Reboot, and you should be good to go.

---

### Post by chrisccoulson on 2008-01-18
Also, I don't know how /sys ends up being replace by a symlink. Once your system is up and running again, it might be worth doing:
```
sudo touch /forcefsck
```
before you reboot. This will force a fsck on the next boot to check your disks. Your problem might be indicative of a failing hard drive.

---

### Post by almandris on 2008-01-18
Ok I am in recovery mod in a terminal right now so it somehow booted that far.

Here is my /etc/ftsab file: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=db4ff49d-cd1c-4014-90f1-f6089bd10841 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=713d7950-6071-43bb-bd98-d076303189a5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

mtab shows no information containing any /sys directory or setup.

---

