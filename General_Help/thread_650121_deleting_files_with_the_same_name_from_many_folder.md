---
title: "deleting files with the same name from many folders?"
date: 2007-12-25
forum: General Help
---

### Post by QwUo173Hy on 2007-12-25
There is a file called desktop.ini in many of my folders. How can I delete these?

I ran a search in nautilus but that doesn't allow deletion.

I tried rm -ir *.ini but that prompts me to delete mp3s for some reason.

I've read the man page for rm and I still can't solve this.

---

### Post by Super TWiT on 2007-12-25
You can run a search in tracker and delete them that way.

---

### Post by QwUo173Hy on 2007-12-25
I tried that using both *.ini and .ini as arguments (via the deskbar applet) but it returned no results.

---

### Post by capink on 2007-12-26
if you want to delete those files only in your home directory tree:

```
find /path/to/home/dir -iname 'desktop.ini' -exec rm {} \;
```

if you want to delete the files from all folders in your pc:

```
sudo find / -iname 'desktop.ini' -exec rm {} \;
```

---

