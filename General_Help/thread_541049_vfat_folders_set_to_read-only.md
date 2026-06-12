---
title: "vfat folders set to read-only"
date: 2007-09-02
forum: General Help
---

### Post by Nathan_M on 2007-09-02
Hi,
I have a vfat partition for sharing between OSs (sda3). It has some folders on it which don't cause any problems, but there are other folders (the ones created by Windows) which are set to read-only. The thing is, the files and folders inside these folders are fine. So [vfat dir]/Music/ is read-only but [vfat dir]/Music/Bob Dylan/ isn't.

If I fire up windows (and suffer for ages as I wait for it to load) I can right-click on the offending folders, click properties and deselect the read-only box, but when I start up linux again, it's back to read-only.

This is my fstab, although I don't think the problem is anything here, as it's not the whole partition that's the problem, just some of the folders in it.
```
proc            /proc           proc    defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda3    /home/nathan/share vfat  iocharset=utf8,umask=000  0    0
/dev/sda4  none   swap   sw   0   0
```

Anyone know how I can make them not read-only?

---

### Post by vanadium on 2007-09-02
Unix permissions are used to control the access to files. However, fat32 does not support permissions. Thus, the permissions of the mount point (/home/nathan/share) apply. This to say that I am surprised that, on that volume, some files would have different permissions than others.

Could you post the output of following commands

ls -l /home/nathan | grep share     ##this will list the permissions of your mount point

and then 

ls -l /home/nathan/share

(should show your read only Music folder)

and 
ls -l /home/nathan/share/Music

(should show your read/write Bob Dylan folder.

---

### Post by Nathan_M on 2007-09-02
Thanks, I understand about linux permissions and the FAT32 thing, but surely linux must have a way of changing FAT32's permissions.

Here's the stuff you asked for, with some folders missed out for clarity:
```

~$ ls -l /home/nathan | grep share
drwxrwxrwx 15 root   root    16384 1970-01-01 01:00 share
:~$ ls -l /home/nathan/share
total 112
dr-xr-xr-x 161 root root 16384 2007-08-29 00:51 Music
drwxrwxrwx   3 root root 16384 2007-08-14 15:04 Documents
drwxrwxrwx   3 root root 16384 2007-08-14 18:04 $recycle.bin
~$ ls -l /home/nathan/share/Music
total 2576
drwxrwxrwx  4 root root 16384 2007-08-14 18:43 1990s
drwxrwxrwx  8 root root 16384 2007-08-14 18:43 Air Traffic
drwxrwxrwx  6 root root 16384 2007-08-14 18:43 Antonio Vivaldi
drwxrwxrwx  6 root root 16384 2007-08-14 18:43 Arcade Fire
drwxrwxrwx  3 root root 16384 2007-08-14 18:43 Arcade Fire & David Bowie
drwxrwxrwx  6 root root 16384 2007-08-14 18:43 Arctic Monkeys
drwxrwxrwx  3 root root 16384 2007-08-14 18:43 Ash
drwxrwxrwx  7 root root 16384 2007-08-14 18:43 Belle & Sebastian
drwxrwxrwx  3 root root 16384 2007-08-14 18:43 Ben Folds Five
drwxrwxrwx  3 root root 16384 2007-08-14 18:43 Blood Red Shoes
drwxrwxrwx  5 root root 16384 2007-08-14 18:43 Blur
drwxrwxrwx  3 root root 16384 2007-08-14 18:43 Bob Dylan

```

---

### Post by Nathan_M on 2007-09-02
Oh, I've just thought of a workaround:

~/share$ mkdir M
~/share$ sudo mv Music/* M
~/share$ rm -r Music
rm: remove write-protected directory `Music'? y
~/share$ mv M Music

Hmm. I would rather find the "correct answer" for future reference, though.

---

### Post by capink on 2007-09-03
Change the line in fstab as follows and try mounting again:

```
/dev/sda3    /home/nathan/share vfat  defaults,utf8,umask=000,dmask=000,uid=1000 0       0
```

Replace the uid=1000 with your user id. You can know the value of the current user id by typing:

```
grep `echo $USER` /etc/passwd | awk 'BEGIN { FS = ":" } ; { print $3 }'
```

---

### Post by merlinus on 2007-09-03
Much easier way to find current user id and group id:

```

id

```

-merlin

---

### Post by vanadium on 2007-09-03
Do not touch your fstab for now.

Your mount point and your files are owned by root, not by you, although root has the generosity to let everyone do all. However, some of the folders do not have the write permission set. Thus, since you are not the root, you are not entitled to write to these directories. Since you are not the owner, you are not allowed to change the permissions of these folders.

Except if that drive should be used by other users as well, change the owner (and group) of the mount point to yourself. Then, suddenly, all files on the volume will be yours (fat cannot store user and group info on a per file basis, thus the settings of the mount point apply). At that moment, you will be able to, as a user, set the write permission on the folders that currently are read-only.

Alternatively, you could set the write permissions on these folders as sudo. Then, you will be able to write as a normal user, but only because owner root allowed you. You wont be able to change permissions as a normal user, though.

Edit: Please mark this thread as solved if this helped you

---

