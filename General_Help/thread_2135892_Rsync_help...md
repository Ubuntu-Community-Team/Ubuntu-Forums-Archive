---
title: "Rsync help.."
date: 2013-04-15
forum: General Help
---

### Post by sideaway on 2013-04-15
Hey team trying to run an rsync command to keep the 6 latest files from one directory (with sub directories) backed up in another directory.

Currently I have;

rsync `find . type f -exec ls -t '{}' + | head -n 6` /media/500/sync -a

Which by my calculations should produce a list of files in the operating directory, sorted by ls in order of modification (newest first), truncate at 6 files, and handed to rsync to copy... Which works, however my list of files has directories with spaces in a the path name. So my copy of a file with the path;

"/path/to file/one"

ends up interpreted by rsync like this;

path/to
file/one

Rsync then complains there are no directories with that name - which, of course, is correct. Does anyone have a better way of achieving the same thing? Or perhaps a more concise string? Surely there must be a simple way of achieving this.

I'm not worried about maintaining path structure as the destination directory will be read by a database anyway. However the destination directory should only ever contain the 6 newest files, which means that rsync will have to know that the directory has changed.

Another script could run to remove anything older than the 6th oldest file however. Please have it noted that these files can change sporadically and this folder will only be synced once a week on a Thursday evening (as this is the only time the destination directory will be on the local network)

Anyone have any ideas?

Cheers
aim

---

### Post by schragge on 2013-04-15
Perhaps
```

find -type f -printf '%T@:%p\0'|sort -nrz|
xargs -0rx bash -c 'f=("${@::6}"); rsync -a "${f[@]#*:}" /media/500/sync'

```
The same using perl instead of bash:
```

find -type f -printf '%T@:%p\0'|sort -nrz|
perl -0pe 's/^.+?://; last if ++$c>6'|rsync -0a --files-from=- /media/500/sync

```

List of old files to be removed is a bit easier to get however:
```
find -type f -printf '%T@:%p\0'|sort -nrz|xargs -0rx bash -c 'shift 6; rm -f "${@#*:}"' _
```

---

