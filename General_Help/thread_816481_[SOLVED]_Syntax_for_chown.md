---
title: "[SOLVED] Syntax for chown"
date: 2008-06-02
forum: General Help
---

### Post by ricardisimo on 2008-06-02
I'd like to change the permissions on a storage drive to include my wife. Let's assume that I had originally done this:
```
sudo chown -R ricardisimo:ricardisimo /media/storage
sudo chmod -R 777 /media/storage
```
What should I run to add my wife as an owner? Let's call her "wife". Would her user name go next to mine after a space, a comma, a dash? Thanks in advance.

---

### Post by Monicker on 2008-06-02
You can't both be owners of a file, but you can both be in the same group.  For example, you could create a group called spouses, make you and her both members of it, and then change the group permissions.

```

sudo chown -R ricardisimo:spouses /media/storage
sudo chmod -R 774 /media/storage
```


You should be careful about chmodding as 777, because it means anyone on the system can change those files. It would probably be okay if there are no other users on the machine, but I stil don't think its good practice.

---

### Post by ricardisimo on 2008-06-03
She's already in the admin group. Couldn't I just ```
sudo chown -R ricardisimo:admin /media/storage
sudo chmod -R 774 /media/storage
```
or is admin not usable for this sort of thing?

---

### Post by Monicker on 2008-06-03
That would work too.  Just make sure you want to her to have access to other files where the group is set to admin.

---

### Post by bodhi.zazen on 2008-06-03
The commands chown and chmod will work on any *Linux Native* file system (ext2, ext3, JFS, XFS, Reiser, etc ...).

Will not work on vfat (FAT) or NTFS. For windows native file systems permissions and ownership are set at the time of mounting.

Also you can use a . rather then a : (I find a dot easier to type)

chown root.users /media/share
chomd 770 /media/share

users is probably a better group for sharing (rather then admin).

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by ricardisimo on 2008-06-07
Thanks to all. I used admin after all, and it seems to be working just fine. I wanted to use an existing group to save a step or two, and that group was perfect.

---

### Post by geirha on 2008-06-07
As mentioned earlier, doing **chmod -R 777** is a bad idea, I would also say that **chmod -R 774** is a bad idea, because it sets the same mode for both files and folders, giving all your files execute permission. Files should only have execute permission if they are executable. I would recommend using the find command to find and set permissions to all directories and all files seperately.

The following finds all files in /media/storage and sets read and write permissions (2+4=6) for owner and group, and read-only (4) for others.
```
sudo find /media/storage -type f -exec chmod 0664 {} \;
```

The following finds all directories in (and including) /media/storage and sets read, write and execute permissions (4+2+1=7) for owner and group, and read and execute (4+1=5) for others. In addition, it sets the setgid-bit on the directories. That bit ensures that new files created inside such a directory will inherit the group ownership. When creating a file it usually gets your initial group (first group printed by the "groups" command) as group owner, but with the setgid-bit you can control this.

```
sudo find /media/storage -type d -exec chmod 2775 {} \;
```

If users not in admin group shouldn't have read-access, change the last digits to 0. I.e. 0640 and 2770 respectively.

---

