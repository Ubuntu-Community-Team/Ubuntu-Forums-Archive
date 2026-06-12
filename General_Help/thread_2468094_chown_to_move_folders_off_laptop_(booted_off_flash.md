---
title: "chown to move folders off laptop (booted off flash drive)"
date: 2021-10-18
forum: General Help
---

### Post by webmanoffesto on 2021-10-18
I have a laptop that isn't working correctly. I booted it up using a flash drive. Now I want to go into folders and copy files and folders to another drive (new laptop or external drive). 

The files are folders such as Misc
/media/lubuntu/83e59733g756a-446a-8f6e-18d6aa957328/home/tom/Documents$ ls -lha
drwx------ 128 1000 1000  80K Sep 14 16:24 Misc

What's the correct chown command to give me the permissions I need.

---

### Post by TheFu on 2021-10-18
chown or chmod?
If it were me, I'd leave both of those alone, then create a new user on the current OS with a uid of 1000, then su - into that userid and access to the files will all work.
Or you can probably use **sudo cp -rp  {source} {target} ** or even better, **sudo rsync -avz {source} {target} **. This will get the files AND retain the current permissions. Just be 100% certain that the {target} area has a native Linux, POSIX compliant, file system ... not exFAT, FAT32, or NTFS.

---

