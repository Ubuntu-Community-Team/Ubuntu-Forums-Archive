---
title: "back up and restore file timestamps"
date: 2016-07-06
forum: General Help
---

### Post by Fire Raven on 2016-07-06
I want to add and correct metadata on my .mp3 files, but I want to keep the files' timestamps as they are. I know how to use touch, and that would be ok if I only had 2 or 5 files. But manually running touch on hundreds of files is worse than not having the metadata. Is there some way I can save all filenames+timestamps in a directory to a file and restore them later? Any solution does not need to be recursive.

---

### Post by &amp;KyT$0P# on 2016-07-06
Yes batch getting & saving timestamps can be done.  Check out the [FONT=Courier New]stat[/FONT] command

Write timestamps of all .mp3 files (searching recursively) out to a file in a format that should be relatively machine-readable:
```
find . -iname \*.mp3 -exec stat -c '%n|||%Y' {} \; > timestamp-records.txt
```

If you're not familiar with the [FONT=Courier New]stat[/FONT] or [FONT=Courier New]find[/FONT] commands, I highly recommend that you refer to their man pages before running that code, so that you not only understand it fully but can also tweak it if it's not quite what you want.


Now, as for restoring these timestamps, I'm a bit short on time right now so I won't be suggesting anything there when I don't test it first. ;)

---

### Post by steeldriver on 2016-07-06
Since Ubuntu has GNU find, you could get the timestamps directly using its printf (rather than -exec'ing a call to stat). For example, to print the modification time (mtime) in seconds since epoch

```

find ... -print '%T@'

```

I'd suggest outputing the timestamp(s) first, then the filename(s) - it makes the result easier to parse in the case of filenames containing spaces. To allow even newlines, you can null-terminate the entries instead of newline-terminating them:

```

find . -iname \*.mp3 -printf '%T@\t%p\0' > mtimes

```

You can then read and process the file using a bash while loop

```

while read -r -d '' t f; do touch -md "@$t" "$f"; done < mtimes

```

Like the previous contributor I urge you to experiment with this on some junk files first, to ensure that it does what you want - don't forget there's a distinction between creation, modification, and access timestamps - I'm assuming you want to restore the mtimes

---

