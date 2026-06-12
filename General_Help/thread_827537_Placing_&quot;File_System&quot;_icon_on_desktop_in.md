---
title: "Placing &quot;File System&quot; icon on desktop in UbuntuStudio 8.04"
date: 2008-06-12
forum: General Help
---

### Post by notesetter on 2008-06-12
Hello,

In previous versions of UbuntuStudio, the "File System" icon was placed on the desktop by default. Also, when I inserted a CD or Flash Drive, icons to access those media automatically appeared on the desktop. How may I reinstate this convenient feature in UbuntuStudio 8.04?

Thanks,

Dave

---

### Post by sdennie on 2008-06-12
You should be able to do this by hitting Alt-F2 and running gconf-editor.  Go to /apps/nautilus/desktop and see if any of those options suit your needs.

---

### Post by notesetter on 2008-06-13
I didn't know about gconf-editor. That will keep me busy for days.:)

---

### Post by sdennie on 2008-06-13
gconf-editor is a fun tool.  Before you start really messing around with it, I would recommend making a backup of the config files first:

```

cd
tar cvf gconf_backup.tar .gconf

```

That way, in the unlikely event you do something that is hard to reverse, you can untar your backup and be back to normal.

---

