---
title: "Comparing files via dates"
date: 2021-06-20
forum: General Help
---

### Post by dlwy3k on 2021-06-20
I have multiple folders with same .odt file names with different dates.
I need to sort them by date in each folder, then compare the files with the same names in the other folders.
So I can compare older with the latest.

Any help appreciated.
dlw

---

### Post by TheFu on 2021-06-20
If the directories are supposed to be identical, use rsync to put the newer file onto the other side.  This is exactly what rsync does.
If you just want a list of the files that would be replaced, use the dry-run mode and a list of files to be replaced will be provided. 

```
        -n, --dry-run               perform a trial run with no changes made
```

There might be some options needed, I generally use *-avz --progress --status* as options, so just add in the -n and capture the list to a text log file for any specific use.

I suppose the dircmp command can be used too. I just more comfortable using rsync. Rsync is an amazing tool for syncing and copying, but also for getting lists of different files if that's the goal.

---

