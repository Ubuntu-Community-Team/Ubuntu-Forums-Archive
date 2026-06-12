---
title: "Confused ... Is rsync working?"
date: 2008-06-05
forum: General Help
---

### Post by Ciego on 2008-06-05
I attempted to use rsync to backup my home directory with the following command ... 

```
sudo rsync --progress --exclude "directoryA" --exclude "directoryB" --exclude "directoryC" -avhe ssh /home/user user@192.168.1.109:/media/MyBook/Backup_user
```

I am backing up to a networked computer at IP 192.168.1.109 that I have an external FAT32 drive attached to and is mounted at /media/MyBook

I can see that files are being copied and I can see the transfer rate and percentage but when I navigate to the backup location it appears as though there are no files in the directory.  

The entire file structure seems to be there but there are no files in it.

I am getting some errors about failing to set times and some other ones about symlinks too (these are errors on individual files).


I am confused .... what am I doing wrong?

---

### Post by Sam Lars on 2008-06-05
> **Ciego said:**
> I attempted to use rsync to backup my home directory with the following command ... 

```
sudo rsync --progress --exclude "directoryA" --exclude "directoryB" --exclude "directoryC" -avhe ssh /home/user user@192.168.1.109:/media/MyBook/Backup_user
```

I am backing up to a networked computer at IP 192.168.1.109 that I have an external FAT32 drive attached to and is mounted at /media/MyBook

I can see that files are being copied and I can see the transfer rate and percentage but when I navigate to the backup location it appears as though there are no files in the directory.  

The entire file structure seems to be there but there are no files in it.

I am getting some errors about failing to set times and some other ones about symlinks too (these are errors on individual files).


I am confused .... what am I doing wrong?

That command doesn't look quite right to me... try this instead:
```
sudo rsync -avh --rsh=ssh --progress --exclude=directoryA --exclude=directoryB --exclude=directoryC  ssh /home/user user@192.168.1.109:/media/MyBook/Backup_user
```
Notably I moved the options to the front, added an = to the exclude arguments, and removed the quotes from the directories (I don't know if you put those in the terminal or not).

---

### Post by Ciego on 2008-06-05
Thanks for the tip.  I will give that a try. 

I am clearing out the drive right now so that I can reformat as EXT3.  I have read in many places that rsync does not like FAT32.

---

### Post by Ciego on 2008-06-06
Everything is working now. 

I reformatted the drive and used the command that you suggested and it is backing up as we speak.  The EXT3 works much better than the FAT32 with regards to timestamps, filenames (cases), and permissions.  That first backup takes FOREVER but it is really nice when you run it again and it skips over all of the files that haven't changed (I had to stop the backup to test that out but it seemed to work nicely).

Thank you for your help.  I can now rest assured that my data is backed up.

---

