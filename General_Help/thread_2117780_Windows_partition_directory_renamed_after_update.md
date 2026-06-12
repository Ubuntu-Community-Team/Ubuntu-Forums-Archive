---
title: "Windows partition directory renamed after update"
date: 2013-02-19
forum: General Help
---

### Post by bfuzze on 2013-02-19
I'm running Ubuntu 12.04 LTS.  I ran the Update Manager when I got in this morning and rebooted my desktop.  When it came back up I found the partition I share with a Windows OS was renamed from Storage to Storage_.  I was a little freaked out to say the least.  No notices or explanations offered during he update process.  Obviously all my symlinks are messsed up now too.  The old directory is still there but doesn't point at anywhere).

Any ideas about what happened?

---

### Post by oldfred on 2013-02-19
Are you mounting in /home or /media? Usually when you mount there it has both entries in Nautilus with the one with the underscore not working. 

I mount in /mnt/data and /mnt/storage and use links and have not had any issues. I use /mnt as then it does not show in Nautilus unless I drill down thru system. But with links I do not need that.

Another way is to change fstab.
       Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

### Post by bfuzze on 2013-02-19
I mount in /media, but I didn't know there was a difference.  I know for sure that /media/Storage_ was not there previously.  

Before the update:
/dev/sda6 -> /media/Storage

After the update
/media/Storage (no mount, just empty dir)
/dev/sda6 -> /media/Storage_

I configured about a year ago. I think I did it in the fstab (not sure how else I would've done it other than a mount cmd in a startup script which I know I didn't do).  Looking in the fstab I don't see a line for my mounted filesystem which is also confusing because now I don't know where/how it is being configured on startup.

These are the only lines in my fstab:
UUID=e1866af0-ac4d-439c-9632-8a60c38c4067 /               ext4    errors=remount-ro 0       1
UUID=c3cfcb1f-787c-4c4b-b405-19f1e0bbb69b none swap sw 0 0

Updates that f* with my file-system with no explanation or warning... not cool.  Ubuntu just lost a confidence point in my book.

---

### Post by oldfred on 2013-02-19
Then it is getting auto mounted by Nautilus. Is it a installed by or external?

If internal I would add to fstab.

       from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

   For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

---

### Post by bfuzze on 2013-02-19
It is internal.  Thanks for the info.

---

