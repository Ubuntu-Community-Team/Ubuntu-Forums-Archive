---
title: "Is there a reliable way of comparing directory sizes from the command line?"
date: 2015-03-09
forum: General Help
---

### Post by peridian on 2015-03-09
Hi,

Is there a reliable way of comparing directory sizes from the command line?  In a Windows environment, I normally use exact file/directory sizes to ensure that all the files have copied from one place to another correctly.

In Linux, the only two commands I know of are "ls -s" and "du"

But I appear to get inconsistent answers from them.  Does anybody know a better way of doing this?

Regards,
Rob.

ls

```

user@host:/$ ls -s /mnt/usb/
sub-folder1:
total 231367692


sub-folder2:
total 222022056


user@host:/$ ls -s /storage/primary/sub-folder1/
total 231368232


user@host:/$ ls -s /storage/primary/sub-folder2/
total 222022612

```

du

```

user@host:/$ du /mnt/usb/
231367820    /mnt/usb/sub-folder1/
222022216    /mnt/usb/sub-folder2/
453390036    /mnt/usb/


user@host:/$ du /storage/primary/
231368244    /storage/primary/sub-folder1/
222022632    /storage/primary/sub-folder2/
453390880    /storage/primary/


user@host:/$ du --apparent-size /mnt/usb/
231367360    /mnt/usb/sub-folder1/
222021492    /mnt/usb/sub-folder2/
453388851    /mnt/usb/


user@host:/$ du --apparent-size /storage/primary/
231367244    /storage/primary/sub-folder1/
222021352    /storage/primary/sub-folder2/
453388599    /storage/primary/

```

---

### Post by The Cog on 2015-03-09
You don't seem to be using the same version of utilities as I have. However, for the version of du that I have, it reports actual disk usage (including the unused partially filled blocks) unless you use the --apparent-size flag.

---

### Post by Keith_Helms on 2015-03-09
Just comparing directory sizes may not be the best way to verify two directories are the same.  Another option would be to use the rsync command in "dry run" mode to actually compare the files in the two directories.

**rsync -vrnc --delete /dir1/ /dir2**

Note that the first directory name should be followed by a slash due to the way rsync works.   The v option is verbose, r stands for recursive, n stands for dry run (make SURE you include that one!), and c says to compare based on checksum.   If you leave off c, rsync will compare based on file size and modification time.  The --delete option will detect files that are in the second directory, but not the first.  As long as you specify the -n option, it won't actually delete anything.

The command will display a list of any differences found between the two directories.  Anything that is in the first directory, but either doesn't exist or isn't the same in the second directory will print out.   Anything in the second directory that doesn't exist in the first, will print out as "deleting filename".

If one of the directories may have additional files in it that you don't care about, you can make that the second directory in the command and leave off the --delete option.

---

### Post by Bucky Ball on 2015-03-10
I generally right click the source and target folders in a regular file manager, check 'Properties'. If they're the same size, good enough for me. ;)

---

### Post by sudodus on 2015-03-10
> **Keith_Helms said:**
> Just comparing directory sizes may not be the best way to verify two directories are the same.  Another option would be to use the rsync command in "dry run" mode to actually compare the files in the two directories.

**rsync -vrnc --delete /dir1/ /dir2**

Note that the first directory name should be followed by a slash due to the way rsync works.   The v option is verbose, r stands for recursive, n stands for dry run (make SURE you include that one!), and c says to compare based on checksum.   If you leave off c, rsync will compare based on file size and modification time.  The --delete option will detect files that are in the second directory, but not the first.  As long as you specify the -n option, it won't actually delete anything.

The command will display a list of any differences found between the two directories.  Anything that is in the first directory, but either doesn't exist or isn't the same in the second directory will print out.   Anything in the second directory that doesn't exist in the first, will print out as "deleting filename".

If one of the directories may have additional files in it that you don't care about, you can make that the second directory in the command and leave off the --delete option.

+1 for ***rsync***.

It is really worthwhile to learn rsync. The manual page, ```
man rsync
``` is well written, and you find more help, if you browse the internet.

It is very good for backup.

---

### Post by The Cog on 2015-03-10
> **Keith_Helms said:**
> Just comparing directory sizes may not be the best way to verify two directories are the same.  Another option would be to use the rsync command in "dry run" mode to actually compare the files in the two directories.
That's a very fine idea. I wish I had thought of it.

---

### Post by dragonfly41 on 2015-03-10
Meld Diff Viewer also compares directories. But it is a GUI.

---

### Post by peridian on 2015-03-10
@Keith_Helms, sheer genius.  I use rsync all the time for backups, but it never occurred to me to use the -n option as a way of checking that files were the same.

Thanks a lot for that.

Regards,
Rob.

---

### Post by slickymaster on 2015-03-10
> **Keith_Helms said:**
> Just comparing directory sizes may not be the best way to verify two directories are the same.  Another option would be to use the rsync command in "dry run" mode to actually compare the files in the two directories.

**rsync -vrnc --delete /dir1/ /dir2**

Note that the first directory name should be followed by a slash due to the way rsync works.   The v option is verbose, r stands for recursive, n stands for dry run (make SURE you include that one!), and c says to compare based on checksum.   If you leave off c, rsync will compare based on file size and modification time.  The --delete option will detect files that are in the second directory, but not the first.  As long as you specify the -n option, it won't actually delete anything.

The command will display a list of any differences found between the two directories.  Anything that is in the first directory, but either doesn't exist or isn't the same in the second directory will print out.   Anything in the second directory that doesn't exist in the first, will print out as "deleting filename".

If one of the directories may have additional files in it that you don't care about, you can make that the second directory in the command and leave off the --delete option.
Fabulous idea, indeed.

---

### Post by peridian on 2015-03-10
An additional note for anybody wanting to use rsync for comparison, I strongly recommend using the following command instead of the above quoted ones:

```

rsync -vrn --size-only --delete /dir1/ /dir2/

```

I have found that the -c option is immensely slow, especially on large complex files such as videos.  Most articles point to the -c option not being useful, since rsync does do various checksums after determining differences.

--size-only works for when you have done a copy of a file and the modified time has been updated where you copied it; otherwise rsync would normally tell you all the files you have copied are different when they are not.

Regards,
Rob.

---

