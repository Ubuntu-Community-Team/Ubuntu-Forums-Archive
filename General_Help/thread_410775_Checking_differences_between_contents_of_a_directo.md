---
title: "Checking differences between contents of a directory and an archive copy"
date: 2007-04-16
forum: General Help
---

### Post by WebDrake on 2007-04-16
I make an informal backup of some of my directories by using rsync -a to create an archive copy on an external hard disk.  Because I haven't used the --delete option it's likely that the archive directory will now contain various files I've deleted from the original.

I'd like to compare and see what's in the archive that's not currently in the original, to check whether it's safe to run rsync --delete.  Is there a way of doing this?

Thanks for any suggestions,

     -- Joe

---

### Post by Rinzwind on 2007-04-16
**comm -3 <(ls ~/dir-new/) <(ls ~/dir)**
(Replace ~/dir-new and ~/dir with your locations)
This will show all files that are in the 1st dir (1st comlumn) and in the 2nd dir (2nd column) and not in the other one.

Add 
**>compare.txt **
to add what's found into a textfile compare.txt

1thing: this requires you to un-archive your archive :)

diff 
will compare files line by line (comparing content). So if you want to see if the content of a file is different compared to another file use diff.

---

### Post by WebDrake on 2007-04-16
Nice suggestions, thank you.  I now know a new shell command. :)

You inspired me to do a bit more looking around and I realised there is a "dry run" option in rsync which will show you the results of the action without actually doing it.

So if you type,```

rsync -avn --delete-after /joe /media/TOUGHDATA/ | grep deleting

```
... you can see what's about to go.

-a = archive (not an actual archive, it copies the files with lots of useful options)
-v = verbose
-n = dry run
--delete-after = after you're done, delete the extra files (the ones not in the source) from the receiving end

---

