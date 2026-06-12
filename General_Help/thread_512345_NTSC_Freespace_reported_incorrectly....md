---
title: "NTSC Freespace reported incorrectly..."
date: 2007-07-29
forum: General Help
---

### Post by Pillzbury on 2007-07-29
Okay, first off let me state that I am new to the linux world.
I have three drives in my PC, two of them being NTFS from my windows installation.  One is used mainly as storage, and one as a windows system disc.  After installing Fesity Fawn (onto a third drive) I was able to access the files on the NTFS drives, but not write to the disc.  I followed a guide to enable ntfs writing using some third-party ntfs drivers.  I cannot seem to find the guide again, and I have no clue what the drivers were called.  

Anyway, my problem is this.  After downloading several gigabytes of data onto my storage drive, my free space was nearing zero, so I deleted roughly 40gb of older, now backed up or unnecessary files.  My free space didn't increase a single byte.  It is now reporting a Free Space of 0 bytes.  I can still download files to this drive, and seemingly (hopefully) without error.  Could anyone help me figure out why it is not reporting correctly?

---

### Post by forestpixie on 2007-07-29
I assume you mean ntfs - the driver is ntfs-3g

```
sudo apt-get install ntfs-3g
```

Have you emptied the trash - deleting files puts them there

If the files are in windows partitions and you still can't empty the trash - try booting windows and doing it there

---

### Post by Pillzbury on 2007-07-29
Corrected.  It's very late or very early, depending on how you look at it.  

Anyway, thank you for the help.  I have resloved the issue.  It was ntfs-3g that I had installed.  After looking at the "man ntfs-3g" I found a link to their support page.  It turns out that the files are moved into ".Trash-*username*" in the root of the drive where they were located, and it does not clear up that space until they are deleted from there.  They do not, however, show up as being in the trashcan on the bottom right of the gnome desktop.  

So now I have two questions...  1, how do/can I have files from my other two drives appear in the trash can to be easily emptied, or do I have to manually navigate to the ".Trash-*username*" folder everytime I wish to delete them.

2, I have a few files in the trash on my ubuntu disk that will not erase because of permissions. They are owned by "root" and I cannot seem to delete them no matter what I do.  Any help there?

Edit:  I was able to delete the files in trash from command line using "sudo -rf ~/.Trash/*"  Is there an easier way to delete files that have root ownership without resorting to the terminal?  Why would it let me move them to trash in the first place if they were root owned?

---

### Post by forestpixie on 2007-07-29
I don't think that there are any easier ways of doing both those things. Might be wrong though

certainly sudo -rf ~/.Trash/* has to be easier than using terminal to open nautilus as root and then navigating to the folder and then deleting files :)

---

### Post by motin on 2007-08-11
> **Pillzbury said:**
> So now I have two questions...  1, how do/can I have files from my other two drives appear in the trash can to be easily emptied, or do I have to manually navigate to the ".Trash-*username*" folder everytime I wish to delete them.

Edit:  I was able to delete the files in trash from command line using "sudo -rf ~/.Trash/*"  Is there an easier way to delete files that have root ownership without resorting to the terminal?  Why would it let me move them to trash in the first place if they were root owned?

Press Shift + Del to delete the files directly without moving them to Trash. Helps avoid this problems in these cases and when accessing media player / memory cards' file systems. 

When I mount an NTFS drive however, 0 bytes is reported always, even though there is about 40 Gb available. I can write to the drive, although only through cp using the terminal - Nautilus complains about no free space... Is this is what you are encountering as well?

---

