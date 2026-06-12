---
title: "bash command doesn't work under /media"
date: 2013-10-01
forum: General Help
---

### Post by uh-huh on 2013-10-01
I use the following to replace spaces with underscores:

```
for FILE in *; do mv "$FILE" "$(echo $FILE | sed -e 's/ /_/g')"; done
```

It works fine under /home/<username> but under /media/... it returns "Permission denied" error. If I prepend sudo, it returns ```
bash: syntax error near unexpected token `do'
```

What's wrong?

---

### Post by sisco311 on 2013-10-01
You have to run the mv command as root:

```
for f in *\ *; do sudo mv -- "$f" "${f// /_}"; done
```

BTW, your command will try to rename files that don't have a space in their name and will throw a `no such file or directory' error if the current working directory is empty. ;)

---

### Post by ajgreeny on 2013-10-01
Do you have any disks attached by USB and therefore showing in /media?

If so it may not be possible to change their names, as those folders will be automatically produced by the system according to various partition naming syntax, ie, it may be the UUID of the partition, or could be the Label given either by you or by the drive maker.

There are usually no folders in /media by default nowadays, so what do you have under /media on your machine?

---

### Post by uh-huh on 2013-10-01
Like I said, it works fine under /home. Yes, it gives errors for files without spaces, but ignores them. I cd'd to the dir in question which is not empty. Your example doesn't work.

---

### Post by uh-huh on 2013-10-01
I wrote /media... The dots represent the drive/dir: /media/abaa08f5-0640-49b2-b0e2-64ca78cf9d3a/music$

---

### Post by drmrgd on 2013-10-01
Do you need the loop and all?  Looks like you just want to replace spaces in the file names (if they exist) with underscores, right?  If so, maybe it's easier to just use the 'rename' command:

```

rename -n 's/ /_/g' /media/abaa08f5-0640-49b2-b0e2-64ca78cf9d3a/music/* #or whatever the appropriate path is

```

The '-n' option allows for a dry run to make sure you're naming things the way you want.  When you're satisfied, you can just run the command without that option.  

Also, you may not need 'sudo' for this, unless the music files you want to change are in a directory for which you do not have permissions.

---

### Post by uh-huh on 2013-10-02
Thanks! That works. I didn't know there was a "rename" command :)

---

