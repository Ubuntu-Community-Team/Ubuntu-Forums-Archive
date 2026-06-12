---
title: "Find files based on time"
date: 2022-09-28
forum: General Help
---

### Post by raleigh3 on 2022-09-28
I am trying to find files by date.

This is supposed to find files created today, but it returns nothing.
```

find . -type f -ls |grep '"Sept 28"'
```

I would also like to have it search based on file time as well.

---

### Post by oldfred on 2022-09-28
This gives me a lot of recent files.
find /home/fred/.cache/thumbnails -type f -atime +5 -print 

See 
man find

> [FONT=monospace][COLOR=#000000] -atime [/COLOR][COLOR=#000000]n[/COLOR][COLOR=#000000] [/COLOR]
              File  was  last accessed less than, more than or exactly [COLOR=#000000]n[/COLOR][COLOR=#000000]*24 hours ago.  When find figures out how many 24-hour periods ago the file was last [/COLOR]
              accessed, any fractional part is ignored, so to match [COLOR=#000000]**-atime**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**+1**[/COLOR][COLOR=#000000], a file has to have been accessed at least [/COLOR][COLOR=#000000]two[/COLOR][COLOR=#000000] days ago. [/COLOR]



[/FONT]

---

### Post by SeijiSensei on 2022-09-28
Try "Sep" rather than "Sept". Months are almost always represented with three letters in my experience with Linux.

Find has more parameters than you can shake a stick at. I think you're looking for 
```

   -atime n
              File  was  last  accessed less than, more than or exactly n*24 hours ago.  When find figures out how many 24-hour periods
              ago the file was last accessed, any fractional part is ignored, so to match -atime +1, a file has to have  been  accessed
              at least two days ago.

```

Run "man find" for the gritty details.

---

### Post by TheFu on 2022-09-28
'find' has an option to show files with atime, mtime, ctime options from x days ago (and newer).

$ find . -type f -mtime -7 
Will find files modified/created in the last 7 days.  -atime isn't exactly useful, as many people mount file systems with noatime mount option. I do.

As  SeijiSensei points out, the time isn't a specific date, but a number of hours * 24, so some files that were modified on the cusp of the "days ago" value won't be shown, unless the command is run at  1 second after midnight to get all the files.  I usually do a -7 and -8 time value to ensure those files are known.

I suspect that \( -mtime -3 -a mtime -4 \) could be used to bracket specific days ago.

---

