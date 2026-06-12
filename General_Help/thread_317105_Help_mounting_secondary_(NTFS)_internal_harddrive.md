---
title: "Help mounting secondary (NTFS) internal harddrive"
date: 2006-12-11
forum: General Help
---

### Post by Daneeka on 2006-12-11
I have followed the instructions in this link: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
But I come to a problem when it's time to edit the fstab file.

Here's a copy & paste of the screens up to (and including) that point:


> sudo fdisk -l
```
Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24133   193848291   83  Linux
/dev/hdb2           24134       24321     1510110    5  Extended
/dev/hdb5           24134       24321     1510078+  82  Linux swap / Solaris

Disk /dev/hdd: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        7298    58621153+   7  HPFS/NTFS
```

(The 60GB one is the one I would like to mount)


> sudo nano /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=bb975cba-3a4a-4a1a-bdcc-5a5c4d3dcf5f /               ext3    defaults,erro$
# /dev/hdb5
UUID=defe0125-b900-432b-9711-9c28da8781a1 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

This is where the problem arises. I cannot seem to find /dev/hdd1 in there.

Am I missing something?

Oh, and I just need to access this drive to copy some files over, then I'll unmount it again.

Thanks!!

---

### Post by x64Jimbo on 2006-12-11
The device doesn't need to be in fstab for you to mount it - fstab is just there so your system knows which devices it's supposed to mount automatically every time it boots. Since you're doing a once-off deal here, you can simply mount the device with the mount command.
First, create a mount point:
sudo mkdir /media/hdd1
then mount the device there:
sudo mount /dev/hdd1 /media/hdd1
problem solved!

---

### Post by Daneeka on 2006-12-11
Thanks!

But when I click on the directory, it just says this:

[IMG]http://i2.photobucket.com/albums/y15/mrgreengenes/Screenshot.png[/IMG]

Any clues? Thanks again.

---

### Post by x64Jimbo on 2006-12-11
You need root to be able to access the files.
sudo nautilus
Then once you get the files into your home directory, make sure you take ownership of them from root so that you can access them once again.
sudo chown -R <your username> ~ 
That command takes ownership of your entire home directory recursively

---

### Post by Daneeka on 2006-12-11
The 'sudo nautilus' command worked -> I can now access my files on there (yes!!) - but I cannot figure out how to move them anywhere.

Copy & paste doesn't seem to work, and neither does dragging and dropping.

Is there some way to move them from the terminal perhaps? (Sorry, I've just moved over from windows xp, still learning the non-GUI side of things).

Thanks so much. :)

---

### Post by x64Jimbo on 2006-12-11
Terminal command to copy files recursively:
sudo cp -R <input folder> <destination folder>

---

### Post by Daneeka on 2006-12-12
You, sir, are a genius. :)

Thank you times a million!
Yipee!

---

