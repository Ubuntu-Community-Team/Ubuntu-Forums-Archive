---
title: "rsync: Files vanished"
date: 2017-02-06
forum: General Help
---

### Post by leunam12 on 2017-02-06
Hi, I do a daily backup at my office from a Ubuntu USB live session, basically I rsync the contents of one internal drive to another internal drive and then to an external drive, something like this:
```
rsync -av --delete /media/ubuntu/drive1/ /media/ubuntu/drive2
rsync -av --delete /media/ubuntu/drive1/ /media/ubuntu/ext_drive
```
transferring to the the second internal drive is always fine (the first line), but transferring to the external drive always gives me a "some files have vanished" error.

I checked all the drives for errors and there are no errors, so I don't know what to do next.
Any help will be greatly appreciated.

Thanks

---

### Post by Impavidus on 2017-02-06
Are there Linux file systems on all those partitions? Is the external drive always properly unmounted before it's unplugged?

Also note that this is not a particularly safe backup strategy. The most likely reason why you may want to use your backups is accidental deletion or corruption of a single file. You destroy those old backups after a single day, which may be before you notice you need them. Better to have versioned backups and keep them at least a few weeks.

---

### Post by leunam12 on 2017-02-06
None of those partitions are Linux filesystems, they are NTFS. 
I always unmount the external drive before unplugging.

I have never encountered a situation in which I needed a file that I deleted from the main drive after more than one day; but it certainly can happen. I'll consider your advice seriously, I think it's a good strategy.  Thanks

---

### Post by HermanAB on 2017-02-06
Beware of --delete.  It is dangerous.  The --delete-after option is a little safer.

When you have to use the delete option always use --max-delete=NUM to give it a limit so that it won't delete more than 10 or so files to prevent a disaster.

---

### Post by howefield on 2017-02-06
Not sure if rsync logs by default but you could use the --log-file=path_to_log option then grep the file for "file has vanished:". Eg,

```
rsync -av --delete --log-file=path_to_write_log_to/rsync.log /media/ubuntu/drive1/ /media/ubuntu/ext_drive
```
```
grep -ir "file has vanished:" /path_to_logged_file/rsync.log
```

---

### Post by leunam12 on 2017-02-06
> **HermanAB said:**
> Beware of --delete.  It is dangerous.  The --delete-after option is a little safer.

When you have to use the delete option always use --max-delete=NUM to give it a limit so that it won't delete more than 10 or so files to prevent a disaster.

We create and receive from outside sources a lot of very large Photoshop files that are temporary in nature. I also receive a lot of compressed files and I have to delete them (the compressed version) when I unzip the files and I don't need the .zip anymore, otherwise the hard drives would be full of files that are completely useless or repeated. If I don't use --delete the files are going to get transferred to the backup drives and I don't want them there. I can keep them for a while, as suggested above, but after some time I have to delete them.

---

### Post by HermanAB on 2017-02-06
Then make the max_delete larger - but do use it and set it to a reasonable average number so that the deletions will eventually catch up, but protect you against a big disaster.  Otherwise if you accidentally delete a directory with a bazilion files, then all those files will also disappear from your backup before you may be able to realize what happened and recover from the backup.

(Long ago, when I supported some lawyers, it happened multiple times that a secretary would accidentally delete tens of thousands of files and on a Linux server, that happens in the blink of an eye.)

---

### Post by leunam12 on 2017-02-06
Makes sense, thanks.

---

### Post by SeijiSensei on 2017-02-06
> **leunam12 said:**
> We create and receive from outside sources a lot of very large Photoshop files that are temporary in nature. I also receive a lot of compressed files and I have to delete them (the compressed version) when I unzip the files and I don't need the .zip anymore

Use include/exclude to limit what you backup.

```
rsync -av source target --exclude=*.zip --delete-excluded
```

would backup everything except ZIP files which will be deleted.  You can have multiple --exclude statements or use --exclude-from with a list of file patterns.

---

### Post by leunam12 on 2017-02-07
Ok, I changed the script and I removed the --delete part, and I also decided to --exclude the "Thumbs.db" files that Windows puts everywhere, I don't need those files. Now the problem seems to be gone.

Thanks everyone, the problem has vanished! :lolflag:

---

