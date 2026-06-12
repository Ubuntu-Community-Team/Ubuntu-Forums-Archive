---
title: "rsync messes up usb stick?"
date: 2015-10-28
forum: General Help
---

### Post by triplemaya on 2015-10-28
I have two usb sticks I use for take-with backup at all times. Once a day I use an rsync script to back up files. After a few weeks or months, they start to malfunction. No error messages, just run slow, and when it gets bad, do not complete the function. The first sign of trouble is often that the stick is not automatically recognised on the first try, but works on the second try.

I plug one into windows 7, up comes the 'there may be problems with this drive'. I leave it to check the disk with Automatically fix file system errors' and 'Scan for and attempt recovery of bad sectors' both ticked. It grinds through for half an hour ( the current sticks are both 64 gb Kingston data travellers. All back to normal, until the next time.

I seem to have a bunch of slightly odd symptoms here. And windows seems to be a big help! 

Both sticks are less than 3 months old.

Previous sticks of different top quality names had the same problems.

I would love to know why they are 'going bad'. And whether I should check them on the linux box from time to time, and what to do with them. I always understood reformatting these was not a terribly good idea.

---

### Post by TheFu on 2015-10-29
Does the script properly **umount** the storage? Not doing that will often lead to corrupted file systems on any OS.

---

### Post by sudodus on 2015-10-29
If you are using rsync I guess you are using linux. And in that case I would recommend a linux file system instead of FAT32 or NTFS. In a linux file system you can also preserve the permissions of the rsynced files and directories.

See also this link: [Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by triplemaya on 2015-10-29
> **TheFu said:**
> Does the script properly **umount** the storage? Not doing that will often lead to corrupted file systems on any OS.

I just invoke rsync with a script. The file system I am backing up is the one I am using, so unmounting it is hardly an option. It is only data I backup though.

rsync -r -t -v -a --progress --delete  ...

---

### Post by triplemaya on 2015-10-29
> **sudodus said:**
> If you are using rsync I guess you are using linux. And in that case I would recommend a linux file system instead of FAT32 or NTFS. In a linux file system you can also preserve the permissions of the rsynced files and directories.


Thanks. I use the standard ext4.

---

### Post by sudodus on 2015-10-29
But Windows cannot repair linux file systems, it cannot even read them. I mean the file system in the pendrive.

---

