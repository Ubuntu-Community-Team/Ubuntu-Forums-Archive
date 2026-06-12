---
title: "Can't change permissions on external HD"
date: 2007-10-23
forum: General Help
---

### Post by nixy_jones on 2007-10-23
I have a USB drive formatted as fat32 as well as four internal ext3 drives. I've mounted each to a folder within my home directory and this worked fine for the internal, ext3 drives.

The USB drive however, gives me an error when I try to change the permissions on the folder I have it mounted to:

         The owner could not be changed.
         Sorry, couldn't change the owner of "My_Book"

Changing permissions was unnecessary for the other drives.

When I try using the sudo chown command, I get an error for each and every file in the directory saying:

         Operation not permitted

I can navigate within the folders on that drive and see that they are intact and are properly read. That's why I don't suspect this is a file system/FAT32 issue.

Any help will be appreciated.

---

### Post by Denn1s on 2007-10-24
are you mounting using pmount, mount or the fstab? i think using pmount for external drives is the best, you must call the comand as user:
```
$ pmount -t vfat /dev/sdx /home/directorythatdoesntexist 
```

---

