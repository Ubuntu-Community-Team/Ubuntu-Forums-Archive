---
title: "Why does Ubuntu wait to write all the data to my PSP?"
date: 2008-03-18
forum: General Help
---

### Post by Gerlads Mod on 2008-03-18
Whenever I put something on my PSP it never writes the whole thing at one time. It will wait and finish when I unmount the volume. 

Why is this?

It gets kinda annoying because sometimes I forget.

Is there anyway to stop it from doing this?

Thanks.

---

### Post by tgalati4 on 2008-03-18
I believe that the auto mounter is designed for USB flash drives.  Since their write/rewrite life is limited, writes get cached.  When there is a lot to write to the disk, it gets written at once.  When you unmount the drive, the write cache must be emptied.  So you have to wait.

Also realize that flash memory has a controller with a wear-leveling algorithm.  This can slow down write speed to the memory.  When you are copying a bunch of files, this write operation can take a long time.

I'm sure there is a way to change the auto mounter behavior, I just don't know it.  You can search for autorun USB drive for some tips on how to change USB mounting behavior.

There may be a simple /etc/fstab switch that you can use.  Search fstab.

---

### Post by sleepingdragon on 2008-03-18
You could use the program *pysdm* in the repos to change the USB write behaviour, but it is not the friendliest of programs - it takes a little time to get used to. The option in pysdm is "I/O to the file system should be done synchronously" for a given USB device. However, as mentioned by **tgalati4**, it's not the healthiest thing for a USB read/write shelf life.

---

### Post by danwood76 on 2008-03-18
You can change the action in the fstab if you find the drives UUID change it to sync instead of async will cause it to write to teh disk like a floppy drive.

---

### Post by Gerlads Mod on 2008-03-18
Okay this is my fstab.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e45ff3d5-cdab-466d-baf6-f7c7d9987b58 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=413a5347-90cc-4203-90b4-bedfb91f9c3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

My PSP comes up as sdc1 and there is no sdc1 in this list.
Should I add it?

---

### Post by danwood76 on 2008-03-18
Yes you can so you could add a line like:
```

/dev/sdc1 /media/PSP (drive format) auto,sync,rw,user 0 0

```

That will allow auto mounting, synchronus data (written when you create/move files), read write properties, user mounting.

I dont know the PSP drive format, I would assume its something like FAT32 but you will have to check the drive once its auto mounted.

It is better to use UUIDs when specifying removable drives in the fstab just incase its dev allocation changes.

-- edit --

also you will need to create the mount point so:
```

sudo mkdir /media/PSP

```

---

### Post by Gerlads Mod on 2008-03-18
So what would I put first?
This: /dev/sdc1 /media/PSP (drive format) auto,sync,rw,user 0 0
Or this: sudo mkdir /media/PSP

Also the PSP is VFAT not FAT32.

---

### Post by danwood76 on 2008-03-18
Vfat is both fat32 and fat16 :)

well add this to the fstab and create the directory, it doesnt really matter which order.
Then plug the PSP in and test if it works (it should appear as PSP on the desktop).
The correct line for the fstab is then:
```

/dev/sdc1 /media/PSP vfat auto,sync,rw,user 0 0

```

if it doesnt work you may need to reboot, im not really sure if the fstab is loaded each time a device is plugged in or if its just once upon startup.

---

### Post by Gerlads Mod on 2008-03-18
I restarted and connected my PSP. It still goes to /media/disk and nothing was changed.

If I look under Computer I see a disk icon that says PSP.
If I click it, it says "Unable to mount the selected volume" "mount: mount point /media/psp does not exist"

My fstab now looks like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e45ff3d5-cdab-466d-baf6-f7c7d9987b58 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=413a5347-90cc-4203-90b4-bedfb91f9c3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

sudo mkdir /media/PSP
/dev/sdc1 /media/PSP vfat auto,sync,rw,user 0 0

```

What should I do now?

---

### Post by Gerlads Mod on 2008-03-18
Finally I got it to work.

My PSP is actually sdb1.
fstab looks like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e45ff3d5-cdab-466d-baf6-f7c7d9987b58 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=413a5347-90cc-4203-90b4-bedfb91f9c3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/sdb1 /media/PSP vfat auto,sync,rw,user 0 0
sudo mkdir /media/PSP

```

There is a few problems though.
1. Nothing in my root folder of my PSP is capitalized now. All lowercase.
2. Doesn't open up folder automatically now.

I have to test that it writes all the data at the same time now.

Thanks man.

---

### Post by danwood76 on 2008-03-19
Sorry we had a bit of a miss communication then.
sudo mkdir /media/PSP shouldnt be in your fstab, that was a command to make the mount point and only needed running once.

If somethings in the fstab it may not open the folder automatically.
There is an option in the removable drives and media preferences panel that might help labelled 'Auto open files on new drives and media' which may solve that issue.

Im not really sure how it would change the capitalisation on the drive, is this much of an issue to you?

---

### Post by danwood76 on 2008-03-19
Also the auto mount wont work when you chuck it in the fstab.
You have to mount manually but it will sync the data as you write it.

---

### Post by bodhi.zazen on 2008-03-19
Be careful with mounting usb devices with sync :

destroy device: [http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)

IMO you are est off leaving the system as is (removing the line from fstab). Thiss allows the device to auto mount. Data will be written to the device when you unmount it.

It you want to write data to the device earlier, use the sync command in the terminal.

```
sudo sync
```

[http://www.hmug.org/man/8/sync.php](http://www.hmug.org/man/8/sync.php)

---

