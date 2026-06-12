---
title: "File copy doesn't complete in Hardy"
date: 2008-04-26
forum: General Help
---

### Post by Jugney on 2008-04-26
I recently did a fresh install of Hardy and things are going very sweetly in general. But I'm having a problem getting a virtual disk image for VirtualBox copied back onto my hard drive from a USB hard drive. 

It's a 15.6GB file and whenever I try to copy, at about 2.0GB it says:

Error while copying "Windows Vista.vdi"

There was an error copying the file into /home/username/destinationfolder/WindowsVista.VDI

When I click show more details, it says

Error reading from file: Input/output error

The file properties say the .vdi file is 15.6 GB. I have tried creating an archive of the file, but that never completes. I tried making an .iso with Kiso, and that showed the file to be about 3.7 GB.

It looks like the file might be broken but the properties still show it's original size. I was there when the whole thing copied to the USB drive and I watched it copy all 15.6 GB, so it should all be there. Is there anything that can be done? Could any of this have to do with it being read off a USB drive?

Thank you,
Jugney

---

### Post by daengbo on 2008-04-26
Is the hard drive in the USB enclosure old? Are you sure the drive was unmounted properly after the original file was copied onto it?

---

### Post by Jugney on 2008-04-26
Well, I got it refurbished last summer, but it has always worked fine. I have done very large transfers at a time (more than 50GB) although it's uncommon for a single file to be 15gb. 

It's possible it wasn't unmounted correctly last time, but all the other files are accessed and copy fine from it. 

Is there anything that can be done if this file was affected by incorrect unmounting?

---

### Post by daengbo on 2008-04-26
If it was unmounted incorrectly, the file may not have finished writing completely. If that's the case, then no. there'll be nothing you can do to recover lost data because it never got to your disk. Always unmount a disk before removing.

That may not have happened, though, so let's try something else.

Is the hard disk small enough to fit onto the free space of your internal drive? If so, you can use dd to copy the disk image over and mount the disk image instead of the physical disk. That will at least take out the possibility of hardware problems.

> dd if=/dev/YOUREXTERNALDISK of=backup.img

---

### Post by Jugney on 2008-04-27
Thanks daengbo. I just tried it and this is what I get when I type in 

sudo dd if="/media/Bodhi Drive" of=image.img

> dd: reading `/media/Bodhi Drive': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00070268 s, 0.0 kB/s


Help?

---

### Post by Jugney on 2008-04-27
bump

---

### Post by daengbo on 2008-04-27
Jugney,

You used the /media location and not the /dev device, so the operation failed. Plug in your drive and find the /dev file using 
> mount
The string should look like /dev/sdb1. Then re-run the command using that string.

---

### Post by Jugney on 2008-04-28
Ah, thank you! It copied all 88GB of data on the drive.

Now I just need to know how to mount the .img file...?

---

### Post by daengbo on 2008-04-28
Create a directory in you home called something like Data
> mkdir Data
Mount the file
> mount -t ext3 /home/user/file.img /home/user/Date -o loop
Replace ext3 with the filesystem of the disk.

---

