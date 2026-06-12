---
title: "HDD Ubuntu is installed on doesn't show in Vista"
date: 2007-05-15
forum: General Help
---

### Post by afinita on 2007-05-15
I recently decided to try out Ubuntu, as I have a friend who loves it.  I had way to many issues with it, so I want to reclaim my hard drive to use as my RecordedTV folder in Media Center once again.  My problem is it isn't listed in my 'Computer' anymore.  I am sure its just me being noob that I don't know how to fix this, but I post this on a Ubuntu forum instead of a Vista forum because I figure Ubuntu can hide the HDD it is installed on(?)

Is my hard drive lost for all eternity?  Or am I just overlooking a stupid little thing?

Thanks for reading,

Christian

[EDIT]

Heh, let me give a bit more info :P

The hard drive Ubuntu is installed on is an old IDE disk, while Vista is on a SATA disk.  The IDE shows up in the device manager, but I don't think you can do anything with it from there.  I tried all the letter thingy's like c:/ b:/ d:/ in the command prompt, to no avail.(Used to be d:/ )  I just want to reformat it with a FAT32 file system.

---

### Post by dcstar on 2007-05-16
> **afinita said:**
> I recently decided to try out Ubuntu, as I have a friend who loves it.  I had way to many issues with it, so I want to reclaim my hard drive to use as my RecordedTV folder in Media Center once again.  My problem is it isn't listed in my 'Computer' anymore.  I am sure its just me being noob that I don't know how to fix this, but I post this on a Ubuntu forum instead of a Vista forum because I figure Ubuntu can hide the HDD it is installed on(?)

Is my hard drive lost for all eternity?  Or am I just overlooking a stupid little thing?
........

Windows will not recognise Linux EXT2 partitions without extra software, just go into fdisk and select the correct physical drive.

---

### Post by asipi on 2007-05-17
quite ridiciolus that M$ could not get to the level to implement support of other filesystems, yet...
I guess the cause is not they are unable to do it, but rather they do not want, and that is sad...

---

### Post by louistan3 on 2007-05-17
if youre not gona use it for ubuntu anymore.. then you could probably just reformat it and set ntfs as its filesystem.. i think this is what you want..

but on the other hand.. if you just want access to the drive without formatting it.. you need a filesystem driver like fs-driver...

[URL="http://www.fs-driver.org/"]
http://www.fs-driver.org/[/URL] 

its kinda tricky installing it with vista... you need to install it with admin privileges.. and it still has a few bugs with vista.. but only minor.. its still fully usable.. 

hope this helps.. :)

---

