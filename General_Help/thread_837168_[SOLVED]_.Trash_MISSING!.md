---
title: "[SOLVED] .Trash MISSING!"
date: 2008-06-22
forum: General Help
---

### Post by rykel on 2008-06-22
Hi all,

I am trying to empty my Trash, which contains a folder owned by Root.

However, no matter where I looked, I cannot find /home/USER/.Trash, so I cannot even do a forceful "sudo rm -rf ~/.Trash".

Where is the location for the Trash in Hardy? Has it changed, or is my system corrupted?

Thanks for helping.

---

### Post by drs305 on 2008-06-22
> **rykel said:**
> Hi all,

I am trying to empty my Trash, which contains a folder owned by Root.

However, no matter where I looked, I cannot find /home/USER/.Trash, so I cannot even do a forceful "sudo rm -rf ~/.Trash".

Where is the location for the Trash in Hardy? Has it changed, or is my system corrupted?

Thanks for helping.

In Hardy, trash is located in /home/username/.local/share/Trash
The actual deleted files are in subfolder *files*

A safer way to remove root trash from your user trash:
```

sudo chown -R username:username ~/
rm -r ~/.local/share/Trash/files

```

Please mark thread solved if this answers your question.

---

### Post by rykel on 2008-06-22
Hi,

Thanks!! It works.

However, trying to sudo chown username:username hung for about 30 seconds and gave me a Permission Denied error for gnome.vfs so I aborted the process.

Instead, I went straight for the kill by commanding:

[INDENT]**sudo rm -r ~/.local/share/Trash/***[/INDENT]

This thread shall be marked SOLVED.   :guitar:

---

