---
title: "Cannot rename files"
date: 2007-07-20
forum: General Help
---

### Post by themeone on 2007-07-20
I've just created a new logical partition /dev/hda7 with gparted, formatted as ext3, and mounted by fstab.  That all seemed to work OK.

I then created a couple of directories on the new partition, and moved some files from hda6.

Now I can't rename the files.  If I right click on the file the Rename option is greyed out, and if I use command line I get this:

Bareword "flac" not allowed while "strict subs" in use at (eval 1) line 1.

flac is the extension of the file I want to rename.  I want to keep flac as the extension, just rename the first bit.

---

### Post by tbroderick on 2007-07-21
Does rename or mv from the terminal  work as sudo?

---

### Post by themeone on 2007-07-21
sudo mv does work, which is what I did in the end, but rename is greyed out in Nautilus and produces the "bareword" error message when used in terminal

---

### Post by tbroderick on 2007-07-23
What does the line in /etc/fsatb look like? Check the permissions on the files(s) too. Make sure they are owned by your user and not root.

---

### Post by themeone on 2007-07-23
fstab line is as follows:

```
/dev/hda7       /media/hda7     ext3    defaults        0       2

```

The immediate problem was solved via permissions though and I can now rename.  The files and directory they were in were owned by root, as you suggested.

---

### Post by stchman on 2007-07-23
> **themeone said:**
> I've just created a new logical partition /dev/hda7 with gparted, formatted as ext3, and mounted by fstab.  That all seemed to work OK.

I then created a couple of directories on the new partition, and moved some files from hda6.

Now I can't rename the files.  If I right click on the file the Rename option is greyed out, and if I use command line I get this:

Bareword "flac" not allowed while "strict subs" in use at (eval 1) line 1.

flac is the extension of the file I want to rename.  I want to keep flac as the extension, just rename the first bit.

you need to do the following:

sudo chown -R <user>:<user> <mount point for /dev/hda7>

---

