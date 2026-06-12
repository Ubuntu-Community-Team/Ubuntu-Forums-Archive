---
title: "Searching inside tar.gz zip and rar archives"
date: 2006-11-14
forum: General Help
---

### Post by dehuszar on 2006-11-14
I'm looking for one file which I've backed up *somewhere*, but it could be in a number of archived files.  Doing a standard find / -iname <file> doesn't seem to do the trick.  

Is there any wizardry that would allow me to run a find-like search which searches inside archives?  I would need to search inside of rar files, zip files and tar.gz (+ .bz2 & regular tar too I suppose) files.  I realise that such a search could take a LOOONG time, specially on a backup drive...  but hey, what's a backup drive if you can't get your backups?

Don't know if it matters, but I'm running edgy, I have a few external drives, and a samba share or two.

If anyone has any ideas I would be greatly in your debt.

Thanks in advance,
Sam

---

### Post by skymt on 2006-11-14
Try this for .tar.gz:```
find / -iname "*.tar.gz" -exec tar t -f '{}' \; | grep file-you're-looking-for
```

For zip, that would be:```
find / -iname "*.zip" -exec unzip -l '{}' \; | grep file-you're-looking-for
```

For rar:```
find / -iname "*.rar" -exec unrar l '{}' \; | grep file-you're-looking-for
```

grep is handy. ;)


EDIT: All in one go:```
search-in-archives () {
find / -iname "*.tar.gz" -exec tar t -f '{}' \; | grep $1
find / -iname "*.zip" -exec unzip -l '{}' \; | grep $1
find / -iname "*.rar" -exec unrar l '{}' \; | grep $1
}
search-in-archives file-you're-looking-for
```

---

