---
title: "Files Migrated to Ubuntu with Special Chars in Filename"
date: 2015-05-15
forum: General Help
---

### Post by frbastiat on 2015-05-15
I recently migrated to Ubuntu Server 14.04 server from WHS 2011. As part of this migration I took an extra HDD copied all files from one disk over to the spare, formatted the original to ext4, then copied all files back. I did this for 4 HDDs. I now have issues with files that contained special characters in the titles. Movies with foreign names like Les Miserable that have letters with an accent show in ls but cannot be accessed. They also have ?? for all attributes. I would like to recover these files but would also settle for their removal if necessary. I have tried rm, mv, and even booting into a live usb to delete but have not had any success. Any suggestions?

On another topic I also have been noticing a strange behavior in some of Ubuntu's outputs. When I fail to stat the before mentioned files the filename is preceded and followed by an â. 
```
mv: cannot stat âLes MisÃ©rables (2012) (1080p)â: No such file or directory
```
This is similarly happening (just where I've noticed) in lsblk output.
```
ââsdd1   8:49   0   2.7T  0 part /mnt/DRU1
```

Any help to either (or both) issues would be greatly appreciated.

---

### Post by dino99 on 2015-05-15
You probably hit a transitional issue from ??? to utf-8 formats; You did not said which app was used to made the diskcopy; maybe some option(s) was needed to avoid such errors 

[http://manpages.ubuntu.com/manpages/dapper/man1/prename.1.html](http://manpages.ubuntu.com/manpages/dapper/man1/prename.1.html)
[http://askubuntu.com/questions/280768/how-to-rename-a-file-in-terminal](http://askubuntu.com/questions/280768/how-to-rename-a-file-in-terminal)
[http://www.tecmint.com/rename-multiple-files-in-linux/](http://www.tecmint.com/rename-multiple-files-in-linux/)
[http://stackoverflow.com/questions/2372719/using-sed-to-mass-rename-files](http://stackoverflow.com/questions/2372719/using-sed-to-mass-rename-files)

---

### Post by frbastiat on 2015-05-15
I booted into a Mint usb and did a simple copy/paste through the GUI.

---

### Post by frbastiat on 2015-05-16
Is there a way to have the filesystem remove the files from its table of contents?

---

### Post by sisco311 on 2015-05-16
Could you post the exact command you used to rename the file? How did you type in the file name?

Please cd into a directory where a file with the special characters is and post the output of:
```
ls -alib
```
also please check if your locale settings:
```
locale
```

---

### Post by frbastiat on 2015-05-16
```
ls -alib *Les*
ls: cannot access Les MisÃ©rables (2012) (1080p): No such file or directory

```

```
locale
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

---

### Post by sisco311 on 2015-05-16
Is you terminal emulator's character encoding set to UTF-8?

---

### Post by frbastiat on 2015-05-16
So I set the character encoding of Putty to UTF-8 as it was set to ISO-8859-1:1998 (Latin-1, West Europe).
Now the output of ls is:
```
ls: cannot access Les Misérables (2012) (1080p): No such file or directory
```
As opposed to:
```
ls: cannot access Les MisÃ©rables (2012) (1080p): No such file or directory
```

---

### Post by sisco311 on 2015-05-20
Sorry for the delay. 

It's strange that bash is able to do the glob expansion (replace *Les* with the actual file name) but ls is unable to find the file. What happens if you left out the glob (*Les*) from the ls command?

Can you access the files with other commands?
```

find ./ 
stat *

```


Did you try to check the partition for errors? See: [uhelp]community/FilesystemTroubleshooting[/uhelp]

As a last resort you should be able to delete the file by its inode number with debugfs.

---

