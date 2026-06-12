---
title: "Simple Backup questions"
date: 2007-08-30
forum: General Help
---

### Post by earther on 2007-08-30
Two most likely very simple questions that have me stumped: 
 
1. How can I copy the .ful archive to a secondary internal or external drive? I've tried a couple of things but haven't had any success - it won't budge because it's locked. 
 
2. How could I create a backup directly to a secondary internal or external drive? The only options I see are for local (my primary HD) or remote (ssh or ftp) directory. (My secondary drive isn't listed in the options.)
 
TIA for helping me out. :)

---

### Post by edward4130 on 2007-08-30
any external drive will show up under "/media"

so in terminal
```
cp -R /home/username/files /media/USBexternaldrive
```

if permissions do not allow you can always "sudo" before the command "cp" that will ignore permissions.

---

### Post by Zill on 2007-08-30
SBackup produces archive files that are owned by root.  It is therefore necessary to move or copy files as root, either via Nautilus (gksudo nautilus) or via the terminal.

1.  If your secondary internal or external drive is properly mounted to allow read/write then it should be possible to copy (as root) SBackup archives to these drives.

2.  From the SBackup config screen, if you select the Destination tab, then the "other" option, you should be able to select your mounted secondary drive from the file system list.

---

### Post by earther on 2007-08-30
> **edward4130 said:**
> any external drive will show up under "/media"

so in terminal
```
cp -R /home/username/files /media/USBexternaldrive
```

if permissions do not allow you can always "sudo" before the command "cp" that will ignore permissions.
How about copying to a second internal drive?  I tried something like this:
```
 sudo -i cp /home/username/folder/xxxxxx.ful /mnt/seconddrive/backupfolder
```
Kinda new to CLI so something might be wonky.

Thanks.

---

### Post by earther on 2007-08-30
> **Zill said:**
> SBackup produces archive files that are owned by root.  It is therefore necessary to move or copy files as root, either via Nautilus (gksudo nautilus) or via the terminal.

1.  If your secondary internal or external drive is properly mounted to allow read/write then it should be possible to copy (as root) SBackup archives to these drives.

2.  From the SBackup config screen, if you select the Destination tab, then the "other" option, you should be able to select your mounted secondary drive from the file system list.

I tried gksudo nautilus and got this error:
> ~$ gksudo nautilus
Initializing nautilus-image-converter extension
Initializing gnome-mount extension

(nautilus:7706): Eel-CRITICAL **: eel_pango_font_description_get_largest_fitting_font_size: assertion `maximum_acceptable_font_size > minimum_acceptable_font_size' failed

yada, yada


Yes, I can read write to that ext3 partition.  You'd think it would be listed under "other" in the dropdown options but it's not.

Headed out for the day.  Will check back later.  Thanks for your help.

---

### Post by earther on 2007-08-30
Got it all straightened out.  Thanks for pointing me in the gksudo direction.

---

