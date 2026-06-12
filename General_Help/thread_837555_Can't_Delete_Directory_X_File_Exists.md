---
title: "Can't Delete Directory X: File Exists"
date: 2008-06-22
forum: General Help
---

### Post by e.honda on 2008-06-22
OK this is weird. I'm trying to delete a directory inside my mounted flash-drive. It's currently mounted on /dev/sdb1 in /media/disk and the type is fuseblk. The output of ls -l:
```
drwxrwxrwx 1 root root          0 2008-06-22 11:56 test
```
```
drwxrwxrwx 1 root root 12288 2008-06-22 12:31 disk
```
If I do **sudo rm -r test/** or **sudo rm -rf test/** it gives me this:
> rm: cannot remove directory `test/test1': File exists
If I create another new file or directory and store it in the flash-drive, I am able to remove it with no problem. But this particular folder called **test** cannot be removed.

Any help would be appreciated.

---

### Post by TeoBigusGeekus on 2008-06-22
```
sudo rm -r test/ or sudo rm -rf test/
```
Shouldn't it be
```
sudo rm -r [COLOR="Red"]/[/COLOR]test or sudo rm -rf [COLOR="#ff0000"]/[/COLOR]test
```

---

### Post by e.honda on 2008-06-22
No. Any other ideas?

---

### Post by mali2297 on 2008-06-22
Is the flash drive formatted as NTFS? 

If that is the case, see
[http://ntfs-3g.org/support.html#emptydir](http://ntfs-3g.org/support.html#emptydir)

---

### Post by CaKiwi on 2008-06-22
It seems to me that what you're doing should work but what do you get if you enter
>  cd /media/disk/test
ls -la

If there are any files there other than . and .. use 

sudo rm -rf

to remove them and then use
> cd /media/disk
sudo rm -rf /media/disk/test to remove the offending directory

---

### Post by e.honda on 2008-06-23
Ok new updates...When I access my flash-drive and cd to **media/disk/test/test1** then use the **ls** command an error comes up:
```
ls: reading directory .: Input/output error
total 0
```
And yes I'm pretty sure that it's NTFS. If I mount it like the following and try to delete the folder, the same errors are produced:
```
sudo mount.ntfs /dev/sdb1 /mnt/memory
```
Still can't remove the folders **test and test1** located in /media/memory.

Also if I do it like this I still get back the same results:
```
sudo mount.ntfs-3g /dev/sdb1 /media/memory
```
I checked out the link mentioned above but it totally confused me.

To be specific and I'm not sure but I think I created the folders **test/test1** with slackware...can this by any way affect ubuntu?

I will try to remove this under slackware to see if I get the same results. I'll post back.


-----
UPDATE:

I tried removing the 2 folders **test and test1** under slackware and I still get back the same results but to be more specific. This is the exact error:
> rm: cannot remove directory `test/test2': Directory not empty

---

### Post by mali2297 on 2008-06-23
It might be a bug in NTFS-3G driver. Try updating to the [latest stable release]("http://ntfs-3g.org/index.html"). 

If that does not work, you might want to check for corruption in the file system. I would then have suggested to run fsck but it is [not yet available]("http://www.linux-ntfs.org/doku.php?id=ntfsck") for NTFS, as it seems. Perhaps you can try the suggestion to run
```

ntfsresize -fi /dev/hdXY

```
[color=red]DISCLAIMER: Use at own risk. I do not know what this command does.[/color] If you have a Windows machine available, I suggest using that to check the flash drive.

Regarding my previous post, do you use some special locale (that is non-English)?

---

### Post by szaka on 2008-06-23
> **e.honda said:**
> ```
ls: reading directory .: Input/output error
total 0
```

See [http://ntfs-3g.org/support.html#ioerror](http://ntfs-3g.org/support.html#ioerror)

---

### Post by e.honda on 2008-06-23
> It might be a bug in NTFS-3G driver. Try updating to the latest stable release.
I currently have **ntfs-3g 1.2216.** I downloaded the new drivers from the official site and now it's updated to **ntfs-3g-1.2531.** I used **checkinstall** to install it.

After reading the link above about I/O errors, I'm certain that the 2 folders(test/test2) in my flash-drive is corrupted. According to windows, when I tried to delete it, it said that it's corrupted and unreadable.
> If that does not work, you might want to check for corruption in the file system. I would then have suggested to run fsck but it is not yet available for NTFS, as it seems. Perhaps you can try the suggestion to run

ntfsresize -fi /dev/hdXY

DISCLAIMER: Use at own risk. I do not know what this command does. If you have a Windows machine available, I suggest using that to check the flash drive.
Good idea. To be specific, I booted up windows in safe-mode and popped in the flash-drive. Then I right-clicked on drive **F:** and selected the option **Automatically fix file system errors** followed by **Scan for and attempt recovery of bad sectors.**
> Regarding my previous post, do you use some special locale (that is non-English)?
I don't use any special locale language. I only use English.

Conclusion...I updated ntfs-3g driver to the latest version and installed it with checkinstall. I booted up windows in safe-mode and popped in the flash-drive located in drive **F:** Then I used window's tools to **Fix file system errors and attempt recovery of bad sectors** on drive **F:**

With all that said and done, everything is fine now. I was able to delete the 2 folders. Thanks for the help.

---

