---
title: "Folder Error"
date: 2007-07-09
forum: General Help
---

### Post by Zinnin on 2007-07-09
I am not sure how it happened but the folder containing all my music doesn't show up as a folder anymore and shows up as a unknown file type..this means I cant get to my music. I have no clue how to fix this

---

### Post by elachim on 2007-12-17
please can anybode answer this? i have same problem, just save some files to my external hdd (wd mybook 500) and now i cant access some folders on it ..
THANKS in advance!

---

### Post by elachim on 2007-12-18
well i should add that it's fat32 file system (on external hdd), other folders looks ok, please help!
the folder is now shown as single file ("unknown file type") with the same name.
thanks again!
m.

---

### Post by danwood76 on 2007-12-18
what did you do to make the folder come up like that?
we need more info to be able to help.

---

### Post by elachim on 2007-12-18
as i say, i only save some new file (.pdf) to already existing (and accessible) folder. then when i tried to go to folder i couldnt find it, then i noticed that there is a file with the same name. im not aware that i did something wrong, i burned some dvds (k3b), listen to music (rhytmbox) and use bittorrent (azureus) this day. everything else (beside previously mentioned unaccesible folders) works fine ...

---

### Post by danwood76 on 2007-12-18
run a scandisk on the drive.
Windwos chkdisk is probably best for fat32, it will fix the directory you speak of.

---

### Post by danwood76 on 2007-12-18
btw fat32 is probably the worst format for an external HD, if you want it to be universally compatible ntfs is now the way to go, windows has a utility to change fat32 to ntfs

---

### Post by elachim on 2007-12-18
ok, i will try it. fat32 was default file sys on this external hdd, my friend told me to reformate it to ntfs, but i ve been thinking - its default by western digital, they should know why they are do it ... ok, probably not :)

---

### Post by vanadium on 2007-12-18
- If your aim is compatibility, stick to fat32 (can standard be read/written on Windows, Linux, Apple)
- If you use only Linux, change to ext3 (or another Linux format)
- If you use also Windows, change to ntfs (can standard be read/written on more recent Windows and Linux)

That's only my opinion on the matter. fat32 (vfat) can be fully corrected using Linux as well: make sure you know the device name of your disk. There are different ways to see the drives your system knows about, e.g. "blkid" or "sudo fdisk -l". Suppose your defective FAT partition is /dev/sdb1

Then check the disk:

sudo fsck /dev/sdb1

or

sudo dosfsck /dev/sdb1

In order to have the disk "fixed", you need to provide an option, -a for automatic fixing, -r for interactive, eg.

sudo fsck -r /dev/sdb1

---

### Post by elachim on 2007-12-18
thanks for all info!

---

### Post by danwood76 on 2007-12-18
> **vanadium said:**
> - If your aim is compatibility, stick to fat32 (can standard be read/written on Windows, Linux, Apple)
- If you use only Linux, change to ext3 (or another Linux format)
- If you use also Windows, change to ntfs (can standard be read/written on more recent Windows and Linux)


Apple can read ntfs aswell, the linux 3g driver can be run on osx!

---

