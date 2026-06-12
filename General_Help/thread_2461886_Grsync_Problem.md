---
title: "Grsync Problem"
date: 2021-05-09
forum: General Help
---

### Post by thumper76 on 2021-05-09
Using Grsync to back up my home directory to a USB drive. Everything backs up with no problem to the USB, but Grsync also put a copy into the media directory as well. How  can I prevent this. The destination  is set to" /media/rick/backup". "rick" is the home directory and "backup" is the name of the USB.

---

### Post by TheFu on 2021-05-09
Ensure the backup storage is actually mounted before you run grsync?
What most likely happened was at least once, grsync got run when the storage wasn't mounted.

I don't use grsync, but there are a number of techniques to test whether the storage is mounted or not.  HermanAB puts an empty file ".NOT_MOUNTED" into the directory where storage is supposed to be mounted.  When it isn't mounted, that file can be seen. When it is mounted, that file cannot be seen because the mount overlays and hides it.  Testing for the existence of a file in a specific location is bonehead in any scripting language.

For example, say I have a file /tmp/t
```
#!/bin/bash

FILE="/tmp/t"

if [ -f  "$FILE"  ] ;  then
   echo "File: $FILE exists."
else
   echo "File: $FILE does not exist."
fi
```

Testing the script:
```
$ touch /tmp/t

$ ~/bin/T
File: /tmp/t exists.

$ rm /tmp/t                     

$ ~/bin/T
File: /tmp/t does not exist.
```

You could try to mount the backup storage if the file is seen, then run the test again to ensure the mount worked.

---

### Post by thumper76 on 2021-05-10
OK problem solved. I checked again today and there was nothing in the media file!! I plugged in the USB and everything on the USB show up in the media file. For some reason the contents of the USB is mirrored in media. Strange!

---

### Post by TheFu on 2021-05-10
> **thumper76 said:**
> OK problem solved. I checked again today and there was nothing in the media file!! I plugged in the USB and everything on the USB show up in the media file. For some reason the contents of the USB is mirrored in media. Strange!

It isn't strange.
There are clearly known reasons.

The storage target must be mounted.  If you expect that to be magic, it is not.  Setup **autofs** correctly for any external storage and is will let the OS automatically mount the storage without you having to click in a file manager to startup gvfs or gio which are much, much, slower access methods for most storage and do not work with most Linux programs.

Permission denied almost always is due to ownership, groups, or mount options (ntfs/fat-whatever) being incorrect.  If the tool doing the copy/rsync is a snap package, then permission errors can be caused by the security confinement that snaps demand. 

[LIST]
[*]I haven't seen any file listings posted that show permissions, owners, groups for either the source or the target areas.  **ls -al**
[*]I haven't seen any mount details.  **mount** after the target file system is already mounted.
[/LIST]
Neither of those things can properly be shown using a GUI.
Post that information if you are interested in understanding what is actually happening. Please.

---

### Post by thumper76 on 2021-05-11
I should mention that Grsync is successfully writing everything to the USB, so I don't think there's a permission problem. Also if you forget to insert the USB, Grsync will happily write to the media file permanently. 

>  

[LIST]
[*]I haven't seen any file listings posted that show permissions, owners, groups for either the source or the target areas.  **ls -al** 
[*]I haven't seen any mount details.  **mount** after the target file system is already mounted. 
[/LIST]

```

rick@PowerSystem:~$ ls -al
total 196
drwxr-xr-x 27 rick rick  4096 May  6 17:19 .
drwxr-xr-x  3 root root  4096 Sep  5  2020 ..
-rw-rw-r--  1 rick rick 53319 Mar 28 16:50 3.28.21_Package.list
drwxrwxr-x  4 rick rick  4096 Mar  8 21:02 .assaultcube
-rw-------  1 rick rick   406 May 10 13:54 .bash_history
-rw-r--r--  1 rick rick   220 Sep  5  2020 .bash_logout
-rw-r--r--  1 rick rick  3771 Sep  5  2020 .bashrc
drwx------ 18 rick rick  4096 May  9 09:07 .cache
drwxrwxr-x  6 rick rick  4096 Sep  7  2020 .clamtk
drwx------ 31 rick rick  4096 May  5 12:29 .config
drwx------  2 rick rick  4096 Feb 14 12:39 .cups
drwxr-xr-x  2 rick rick  4096 May 10 18:11 Desktop
drwxr-xr-x 11 rick rick  4096 May 11 11:55 Documents
drwxr-xr-x  6 rick rick  4096 May 10 18:53 Downloads
drwx------  3 rick rick  4096 Jan 31 16:41 .gnupg
drwx------  2 rick rick  4096 Sep  6  2020 .grsync
drwxr--r--  2 rick rick  4096 Mar  6 13:27 .hardinfo
-rw-rw-r--  1 rick rick    21 Apr  6 15:05 .iscan_preference
drwxrwxr-x  3 rick rick  4096 Feb  8 13:43 .java
drwx------  3 rick rick  4096 Sep  5  2020 .local
drwxrwxr-x  3 rick rick  4096 Feb  8 14:20 .m2
drwx------  5 rick rick  4096 Sep  5  2020 .mozilla
drwxr-xr-x  2 rick rick  4096 Sep  5  2020 Music
-rw-r--r--  1 rick rick   361 Sep 21  2020 .pam_environment
drwxr-xr-x  9 rick rick  4096 Apr 28 16:07 Pictures
-rw-r--r--  1 rick rick   807 Sep  5  2020 .profile
drwx------  2 rick rick  4096 Apr  4 18:58 .psensor
drwxr-xr-x  2 rick rick  4096 Sep  5  2020 Public
-rw-rw-r--  1 rick rick    66 Mar 14 20:06 .selected_editor
drwxr-xr-x 15 rick rick  4096 Feb  8 13:43 snap
drwx------  2 rick rick  4096 Mar 18 20:27 .ssh
-rw-r--r--  1 rick rick     0 Sep  5  2020 .sudo_as_admin_successful
drwxr-xr-x  2 rick rick  4096 Sep  5  2020 Templates
drwx------  6 rick rick  4096 Feb 12 14:08 .thunderbird
drwxr-xr-x  3 rick rick  4096 Apr  4 17:32 Videos
-rw-rw-r--  1 rick rick   162 Nov 14 12:10 .wget-hsts
drwx------  8 rick rick  4096 Mar 20 14:42 .zoom

```

and I think this is the only line you need from "mount" 

```

/dev/sda on /media/rick/RickBackup type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)

```

---

### Post by TheFu on 2021-05-11
~/ is the HOME directory.  The source directory that is being backed up?  If it is just ~rick/ - then the $HOME would have been sufficient information, but we still need to see the owner, group, and permissions for  /media/rick/RickBackup  
We can make all sorts of valid assumptions about HOME directories, if there is just 1 userid involved.

Good to see ext4. That simplifies correcting issues.

Bad to see there isn't any partition for the backup storage. This is against best practices.  Always have a partition table and always have at least 1 partition.  This will wipe any existing data. Use **gparted** to create a GPT table, add a partition, format as ext4, and probably create a label for the partition - "RickBackup". Then you'll need to mount the storage using the partition device, not the whole-drive device.

Guessing that using udisks2 means that the storage gets mounted through a click in the GUI? I don't use that.

---

