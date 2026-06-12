---
title: "synchronize Firefox bookmarks"
date: 2008-05-08
forum: General Help
---

### Post by dondad on 2008-05-08
Does anyone know of an easy way to synchronize bookmarks between two Firefox profiles. I have two profiles set up, one for FF2 and the other for FF3 and would like to keep the bookmarks synchronized. I use both versions because I want to play with FF3, but need some of the plugins that only work in FF2 for some of the stuff I do.

---

### Post by fain on 2008-05-08
you could set up a script to check the modification date of the two bookmarks.html files and copy the newer one to over write the older one. Then at the end of the script start the browser.

I wrote this little script just now

```

#!/bin/bash
file1=/path/to/first/bookmarks.html
file2=/path/to/second/bookmarks.html

date1=$(date -r $file1 +%s)
date2=$(date -r $file2 +%s)

        if [ $date1 -gt $date2 ]; then
                cp -p $file1 $file2
        else
                cp -p $file2 $file1
fi

```

you'll want to change the file1 and file2 variable to the actual path to bookmarks.html in your profiles directorys

you could set up a cron job to run this or make it execute the firefox you want to run at the end on the line before "fi" so it synchronizes before launch.

Be sure to make a backup of the bookmarks before you run this just to be safe.

---

### Post by smcleish on 2008-05-08
It may be overkill for two profiles on the same machine, but you could use one of the bookmark synchronization plugins. They don't tend yet to have 3.0 compatibility, but I use Foxmarks which has a beta version that you can use with 3.0 if you join the testing program.

---

### Post by dondad on 2008-05-08
> **fain said:**
> you could set up a script to check the modification date of the two bookmarks.html files and copy the newer one to over write the older one. Then at the end of the script start the browser.

I wrote this little script just now

```

#!/bin/bash
file1=/path/to/first/bookmarks.html
file2=/path/to/second/bookmarks.html

date1=$(date -r $file1 +%s)
date2=$(date -r $file2 +%s)

        if [ $date1 -gt $date2 ]; then
                cp -p $file1 $file2
        else
                cp -p $file2 $file1
fi

```

you'll want to change the file1 and file2 variable to the actual path to bookmarks.html in your profiles directorys

you could set up a cron job to run this or make it execute the firefox you want to run at the end on the line before "fi" so it synchronizes before launch.

Be sure to make a backup of the bookmarks before you run this just to be safe.

Thanks, I thought of that, but if I had new bookmarks in both files, one would overwrite the other and not synchronize. I would lose one set of new ones.

---

### Post by dondad on 2008-05-08
> **smcleish said:**
> It may be overkill for two profiles on the same machine, but you could use one of the bookmark synchronization plugins. They don't tend yet to have 3.0 compatibility, but I use Foxmarks which has a beta version that you can use with 3.0 if you join the testing program.

Thanks, I will take a look at that one.

---

### Post by fain on 2008-05-08
> **dondad said:**
> Thanks, I thought of that, but if I had new bookmarks in both files, one would overwrite the other and not synchronize. I would lose one set of new ones.

O ya i didnt think of that. Maybe you could use the diff command to merge the two files. But if you started the script up each time you started either browser, theres no way you could have written to the other bookmarks with out checking which is newer first. I dont think.....

I was thinking of using diff, but i didnt know how to merge a file, this might be the better choice.

---

