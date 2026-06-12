---
title: "no delete confirmation"
date: 2007-05-20
forum: General Help
---

### Post by dachinster on 2007-05-20
hi, 
when i want to delete a file, i do not get a prompt asking if i am sure i want to delete this file
how do i get a prompt?

fyi
i am logged on as a regular user and i am using the gui

---

### Post by taurus on 2007-05-20
Do it from a terminal.

```
rm filename
```

If you are using nautilus to delete file, you are basically moved it to your trash bin so if you want to recovery that space, you need to empty your trash first.

---

### Post by dachinster on 2007-05-20
so in nautilus, there is no prompt asking for confirmation before you delete a file?

---

### Post by Klargodut on 2007-05-20
If you do shift+del (remove permanently), you will get a prompt. If you simply press delete, the file will be moved to trash (it is not deleted) without any prompt.

---

### Post by Henry Rayker on 2007-05-20
> **taurus said:**
> Do it from a terminal.

```
rm filename
```

If you are using nautilus to delete file, you are basically moved it to your trash bin so if you want to recovery that space, you need to empty your trash first.

I'm afraid taurus might have misunderstood. The OP wants a confirmation message. Using the rm command will permanently delete any file you have adequate permissions to delete. USE WITH CAUTION.

As far as giving a confirmation message prior to deleting in nautilus, why? It just moves the file to the trash-bin...

---

### Post by fearpi on 2007-05-22
In a terminal, type ```
gconf-editor
``` and find /apps/nautilus/preferences/confirm_trash. Make sure it is checked.

---

