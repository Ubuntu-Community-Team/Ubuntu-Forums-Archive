---
title: "Help NTFS-3G .fuse_hidden files"
date: 2007-09-13
forum: General Help
---

### Post by prince_niceguy on 2007-09-13
I am having some issues iwth ntfs-3g. I have been using this for quite long now and everything works fine except for one thing. some time when I delete the files permanently they get renamed to

.fuse_hiddenXXXXXXX where XXXX stands for some number.

After this happend no matter what I do I cannot get rid of these files. every time I delete them they assume some other number but size remains the same.

I can go to terminal and clear them using echo but I am not able to delete them any way.

Any idea what this could be...???

---

### Post by Ubuntwan on 2007-10-31
I have the same problem :-(
Sometimes these files can be deleted in nautilus, but then reappear as the view is refreshed. Sometimes they will not be deleted and an error is given:   **Error "File exists" while deleting .fuse_hiddenbalblabla**

---

### Post by Jobjontjo on 2008-01-17
Hello,

I had the same problem. If you unmount the device and mount it again the file is gone, 

```
sudo umount /dev/mydev
```
```
sudo mount
```

cheers,
Johannes

---

### Post by Ubuntwan on 2008-01-21
Thank you, I also noticed that after a reboot it was gone, or at least it could be removed without errors. The un-mounting and re-mounting is a bit of a hassle as I run most of my system from this partition, so that means quitting a few programs, etc. Thanks for the tip though.
cheers ubuntwan

---

### Post by szaka on 2008-01-21
You can safely ignore .fuse_hiddenXXXX files. It means a file was deleted but there is at least one software which is still using it, so it can't be removed permanently. It will be done automatically when the relevant software stops using the file or exists. Such files are always gone after umount/reboot. This is how Linux and any Unix works but only FUSE exposes these files to the user. In the future we may try to make them unvisible but that's not very simple.

---

### Post by Ubuntwan on 2008-01-27
Thank you very much for your reply.
hiding the file will not be of much use though if the space is not freed up. That was the reason I wasn't ignoring these files as you suggested I should. I figured they were harmless and a leftover from having been in use during the delete. The problem is that in my situation most of the time they are part of a dvd file structure and are often more than 1 GB in size.  The program that used them (vlc player for instance) has already quit but not correctly freed the file or something like that. So quiting the program is no solution and only unmounting the partition will remove them. But as I said before, unmounting the partition is not something I like doing.

Not showing the files but not freeing up the space however does not seem a good idea however. Although the files will not go away, at least I know where the disk space has gone. Not showing these leftover files will only make things less clear. Perhaps changing the name to something that explaines the situation a bit more (refering to them as locked or something), or some help info in the ubuntu documentation will help more i think.

Anyway, thank you all for your answers and thanks a lot for developing the ntfs software

---

### Post by _Stevie_ on 2008-02-08
hi!

nice to know what the fuse files are for.
but i have some other problem now...
how can i find out which program access which file?

cause i cant seem to unmount...

---

### Post by szaka on 2008-02-09
> **Ubuntwan said:**
> Not showing the files but not freeing up the space however does not seem a good idea however. Although the files will not go away, at least I know where the disk space has gone. Not showing these leftover files will only make things less clear. Perhaps changing the name to something that explaines the situation a bit more (refering to them as locked or something), or some help info in the ubuntu documentation will help more i think.

Yes, these file names are highly unfortunate and misleading. The <original_file_name>-DELETED.XXXXX form would be probably better.

Other file systems completely hides the removed files if they are still in use. This is how all Unices work unlike for instance Windows which typically denies the removal of such files.

---

### Post by szaka on 2008-02-09
> **_Stevie_ said:**
> how can i find out which program access which file?

The lsof program can tell. Usage: 'lsof full_file_path'.

---

### Post by _Stevie_ on 2008-02-09
thanks szaka! that helped :)

---

