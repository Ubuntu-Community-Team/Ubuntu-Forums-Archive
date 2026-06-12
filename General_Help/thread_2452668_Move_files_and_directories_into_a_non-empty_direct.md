---
title: "Move files and directories into a non-empty directory"
date: 2020-10-26
forum: General Help
---

### Post by alain.roger on 2020-10-26
Hi,

I was looking for a way to move content of a directory (files + sub-directories) into another directory.
I understood that MV command does not move content if destination directory includes some directories that are not empty.
Therefore i check rsync that seems to do it correctly, except that i would like to remove from source directory, all files and sub-directories that were successfully move to destination.
I saw rsync has an option --remove-source-files, but it deals with files only.

Therecore is there a command line or option to remove source content (files + directories) after successful move to destination directory ?
thx

---

### Post by TheFu on 2020-10-26
I would use rsync, then use an inverse-recursive rmdir to clean up empty directories.  Then I'd assume that any directories that aren't empty, had some other issue.

I've never used the --remove-source-files option.  I'd just run, then re-run the rsync without that option, but with progress and status options so any non-copied files would be clear. That would tell me clearly if there are issues or not.  Then use a rm -rf on the source when all was clear.

And I would have excellent backups for all directories involved before beginning any of this.

---

