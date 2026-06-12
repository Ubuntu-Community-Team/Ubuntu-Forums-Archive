---
title: "Nautilus does not ask for confirmation when moving to trash"
date: 2007-03-05
forum: General Help
---

### Post by pandu.rs on 2007-03-05
I am using ubuntu edgy. The problem is that nautilus does not ask for confirmation when moving files/folders to trash. 

This is OK for me with local files because i can recover it from trash... but definitely a problem for NFS mounted files. I just press delete and the file is gone without any easy way to recover it!

In gconf-editor 
apps->nautilus->preferences->confirm_trash is set to 1 (it was the default)

Even then nautilus does not ask for confirmation

thanks in advance for your help

---

### Post by skug on 2007-03-06
You should check File Management Preferences under Behavior and the topic Trash, there you should find two checkboxes one for the trash confirmation and the other for a separate delete button in the right-click menu. ie. Places>Home Folder>Edit>Preferences>Behavior. 

--skug--

---

### Post by pandu.rs on 2007-03-06
Thanks for the reply, it already checked for me . This only affects nautilus behaviour when deleting items from the trash.

What i require is nautilus to ask for confirmation when deleting from folders other than trash

---

### Post by cronholio on 2007-03-06
I think this is the standard Nautilus behavior and it cannot be changed. The reason is that there is no problem if you move something to Trash accidentally, you can always recover it.

---

### Post by pandu.rs on 2007-03-07
> **cronholio said:**
> The reason is that there is no problem if you move something to Trash accidentally, you can always recover it.

For local files this is absolutely true..

But i have just figured out that for NFS mounted files or usb flash disks nautilus creates a folder
'.Trash-<username>' at the root of mounted file system and moves the deleted files there. That solves my problem.

Thanks for the help.

---

