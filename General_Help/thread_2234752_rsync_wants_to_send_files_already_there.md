---
title: "rsync wants to send files already there"
date: 2014-07-16
forum: General Help
---

### Post by scottbomb on 2014-07-16
I have successfully mounted a shared folder on another comp using ```
sudo mount -t cifs //laptop-wired/Music ~/mnt -o username=myusername
```

I then try to transfer all the new music files from this comp to the other using (I always do a dry run first) ```
sudo rsync -avn Music/ mnt
```

And the dry run shows every single song in the source as if it's going to transfer ALL of them. The destination already has most of these files. There are only a handful of new ones. Any ideas of what could be wrong?

---

### Post by mooreted on 2014-07-16
Try telling it to ignore existing files:

rsync --ignore-existing <src> <dest>

---

### Post by scottbomb on 2014-07-16
The a switch for archive mode should do that on it's own but I tried it anyway. I got the same result. It's so puzzling as I use this command all the time with another computer and it only copies over the new files.

---

### Post by mooreted on 2014-07-16
The file names on the source and destination are exactly the same? If so, I don't know, it should just work.

---

### Post by SeijiSensei on 2014-07-16
What about the access times?  If all the copies on the source have newer dates than those on the target, rsync might want to update the apparently outdated files.

---

### Post by scottbomb on 2014-07-17
I was wondering about that. I couldn't find anything in the man file to make rsync ignore the dates on the destination. I went ahead and let it run. It didn't take as long as I had worried (I have a LOT of music files). Judging but the time it took, I suspect it did actually update metadata in addition to adding the new files. In hindsight, I wish I had inspected the timestamps and compared them to the timestamps after the operation but it's too late now.

---

### Post by vanadium on 2014-07-17
The -a switch only works as expected on file systems that support linux permissions. Use a command such as
```

rsync -rltDv --modify-window=1 --delete <source> <destination>

```
The --modify-window=1 is important for the incremental feature to work. It will cause rsync to use less accuracy in comparing time stamps: time differences of less than 1 second are ignored.

---

### Post by sedawk on 2014-07-17
You can try recursive copy with "-rvn" instead of archive mode implied by "-avn".
I'm using "-rv" together with "--size-only" a lot as I do not care about timestamps or permissions.
(I'm only adding and removing files, not replacing them with files that might have the same size but are different in content).
Also be aware that there is a huge difference between "sudo rsync -avn Music/ mnt" and "sudo rsync -avn Music mnt".
When the slash at the end of the source is missing it will copy the whole folder, not only what is inside the folder.
If done wrong, rsync tries to create a new subfolder Music on the target and therefore the dry-run is reporting everything to be copied!

---

