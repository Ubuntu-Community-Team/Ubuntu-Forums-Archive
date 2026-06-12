---
title: "from where can I get examples.gz"
date: 2006-07-11
forum: General Help
---

### Post by ShirishAg75 on 2006-07-11
Hi all,
      Whenever we use the live CD to boot up we get a pretty cool desktop with the examples compressed folder/file. Now I want to view this example file/folder in windows also.  AFAI see the live cd is made in something called "filesystem.squashfs" so tht I can't explore the whole thing. Most probably some kind of compression algorithim or something. Any other way to get the examples.tgz to my desktop C:/ . Also I wanna make some screenshots & put them on my hdd from the live cd. The filesystem in this hdd is FAT32. Thnx in advance. :)

---

### Post by Gustav on 2006-07-11
Boot the live-CD, mount the windows drive, copy the files.

Mounting the windows drive can be done like this:```
mkdir windows
sudo mount -t vfat /dev/hda1 windows/
```(If hda1 is your windows drive)

Then copy the files to the windows directory and umount it```
sudo cp <file> windows/
umount windows/
```

---

### Post by ShirishAg75 on 2006-07-11
Thnx Gustav. Is there a command to know if it's /dev/hda1 or something else? Thnx in advance.

---

### Post by joe343 on 2006-07-11
To know on which disk/partition windows is installed, run
```

sudo fdisk -l

```

---

### Post by nanotube on 2006-07-11
and beware: if your windows drive is ntfs, then you cannot write to it (linux only supports read from ntfs, otherwise you can screw up your partition). so this advice only works if your windows drive is fat32.

if it is not, you can just plug in a usb stick drive, and copy the examples over to that, then read it again in windows.

or burn it to cd.

or upload it to the web somewhere.

so to summarize - offload it somewhere that you can read later with your windows. :)

---

