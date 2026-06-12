---
title: "How to use rsync and get exactly the same result as copy and paste"
date: 2013-06-15
forum: General Help
---

### Post by brunces on 2013-06-15
Hey, guys.

I've been searching for information on how to use rsync correctly, but there are a few different ways when it comes to its parameters.

I want to use rsync and have the same result as I would if I simply used Ctrl+C and Ctrl+V on Nautilus. I've read its help contents and tried the following command:

```
rsync -rv /path/source/ /path/target/
```

So, "r" for recursive (subfolders and files as well) and "v" for verbose (I want to see what's going on). Cool. But I have seen a lot of people suggesting the use of "a" for archive as well. Is that really necessary?

Anyway, as I said, I want exactly the same as copy/paste, so maybe my command lacks parameters, I don't know. What do you say?

Thanks in advance.

brunces

---

### Post by oldfred on 2013-06-15
I think you need archive to preserve ownership & permissions.

I started using rsync with this simple script which also documented the parameters used.

       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh


```
 #!/bin/bash
# backup script
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."
rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

   #rsync -auvP /home /media/backup
echo "done"
exit 0

   make it executable
chmod +x mybackup.sh


```

---

### Post by Dennis N on 2013-06-15
**[FONT=Courier New]rsync -rI[/FONT] <sources...> <destination> **

will give the same result as copying and pasting. Every file in destination gets replaced. Use **a** instead of **a/** for directories as sources. This is not a setup for backup.
If you want to see what was copied, add the i option.

**[FONT=Courier New]rsync -rIi[/FONT]  <sources...> <destination>**

If your objective is copying and pasting, why not just use **cp -r <source files..., source directories...> <destination>**

---

### Post by HiImTye on 2013-06-15
```
rsync -PL /in/file /out/file
```
will copy like the cp command, except that it will follow symlinks (and shows progress)
```
rsync -PLa /in/file /out/file
```
will do the same, but it will keep the file the same (and work recursively, etc)
[quote=http://linux.die.net/man/1/rsync]-P same as --partial --progress
--partial keep partially transferred files
--progress show progress during transfer
------
-L, --copy-links transform symlink into referent file/dir
------
-a, --archive archive mode; equals -rlptgoD (no -H,-A,-X)
-r, --recursive recurse into directories
-l, --links copy symlinks as symlinks
-p, --perms preserve permissions
-t, --times preserve modification times
-g, --group preserve group
-o, --owner preserve owner (super-user only)
-D same as --devices --specials
--devices preserve device files (super-user only)
--specials preserve special files[/quote]
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

