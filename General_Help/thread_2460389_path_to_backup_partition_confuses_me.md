---
title: "path to backup partition confuses me"
date: 2021-04-08
forum: General Help
---

### Post by sofasurfer on 2021-04-08
I created a backup partition linked the /media directory. This may sound odd but I can not for the life of me remember how I linked them. Maybe I did it when I installed the OS. Anyway, the point of this post is to ask this...
Why is the path to the backup partition /media/username/backup instead of /media/backup. In the file browser when I click on the media folder I go to a /username folder which is empty. When I click on the backup folder under "other locations" I am in the backup folder with a path of /media/username/backup.

Am I missing something obvious? Did I link the backup partition to /media incorrectly? I just do not understand this.

---

### Post by oldfred on 2021-04-09
File browser now creates new mounts in /media/$USER, it used to not include the user.

So if you created a partition with the label backup, it would auto mount to /media/$USER/backup.
If internal partition often better to create mount point, give yourself ownership & permissions & add mount entry in fstab, so on reboot it is auto mounted without you having to click on it in your file browser.

Post this:
[FONT=monospace][COLOR=#000000]ls -l /media/$USER[/COLOR]

and:
lsblk  -o NAME,LABEL,PARTLABEL,SIZE,MOUNTPOINT | egrep -v "^loop"
[/FONT]

---

### Post by sofasurfer on 2021-04-09
OK, here are the outputs...

```
 
$ ls -l /media/$USER
total 0

$ lsblk  -o NAME,LABEL,PARTLABEL,SIZE,MOUNTPOINT | egrep -v "^loop"
NAME   LABEL  PARTLABEL   SIZE MOUNTPOINT
sda                     223.6G 
&#9500;&#9472;sda2                      1K 
&#9500;&#9472;sda3                    512M 
&#9500;&#9472;sda5                   74.1G /
&#9492;&#9472;sda6 BACKUP            50.2G 
sr0                      1024M
```

After I click on the backup partition in the file browser the commands show...

```
 ls -l /media/$USER
total 4
drwxrwxrwx 3 root root 4096 Apr  8 14:41 BACKUP

$ lsblk  -o NAME,LABEL,PARTLABEL,SIZE,MOUNTPOINT | egrep -v "^loop"
NAME   LABEL  PARTLABEL   SIZE MOUNTPOINT
sda                     223.6G 
&#9500;&#9472;sda2                      1K 
&#9500;&#9472;sda3                    512M 
&#9500;&#9472;sda5                   74.1G /
&#9492;&#9472;sda6 BACKUP            50.2G /media/daryl/BACKUP
sr0                      1024M 

```

---

### Post by oldfred on 2021-04-09
That then is all per the defaults.
If you want it mounted anywhere else, you have to specify in fstab.

I do not like Disks as it may not use correct parameters. Better to use template/example and adjust for your specifics
[https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup](https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

If you need specify example with your details, post these:
cat /etc/fstab
sudo blkid -c /dev/null -o list
or 
lsblk  -o NAME,LABEL,PARTLABEL,SIZE,fsused,MOUNTPOINT,uuid | egrep -v "^loop"

** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

