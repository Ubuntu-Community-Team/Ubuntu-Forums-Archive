---
title: "Duplicity include/exclude without full path"
date: 2019-05-04
forum: General Help
---

### Post by sgharp on 2019-05-04
Hi Guys,

I'm using duplicity on Ubuntu v18.04 and would like to include or exclude files/directories without specifying the full path.  For instance, I'd like to exclude all .swp files regardless of where they reside.

```
--exclude='.*.swp'
--exclude='**/.*.swp'
```

The above doesn't work at all of throws a ton of error messages about possibly locked files within directories which aren't even in the --include list.
 
The following really isn't practical because these files could be scattered all over.

```
--exclude='/whatever-directory/.*.swp'
```

Ideas?

Thanks...

---

### Post by TheFu on 2019-05-05
I don't use duplicity, but the manpage says it follows the same rules as rdiff-backup, which is what I use.
* order of include/exclude options is very important.
* file globbing works differently that we expect. **--exclude='**swp' **should be sufficient.
> where ** matches any path and * matches any path without a / in it. 
* there have been bugs in duplicity caused even between a --dry-run and the following run, somehow.
* If I were having issues like this, I'd make a list of files to be excluded using **find** or **locate** just before starting the backup, then feed those into the tool with an _--exclude-filelist /path/to/list-o-files_

Sorry I don't use duplicity.  90% of the time, I need to restore the most recent backup and having it as a mirror is just too handy to give up.

---

