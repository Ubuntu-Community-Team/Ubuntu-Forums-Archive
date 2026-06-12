---
title: "file names ending with &quot;~&quot;?"
date: 2008-04-15
forum: General Help
---

### Post by ddh33 on 2008-04-15
There are a lot of text files ending with "~" and they are annoying when I do ls or work in Eclipse. Sometimes I delete files and the ~ versions are left behind.

What are they? How do I prevent them from being created?

---

### Post by sekinto on 2008-04-16
I don't know how to stop them, but they are backups when you overwrite a file. They might be deleted on shutdown. but I'm not sure.

---

### Post by Diabolis on 2008-04-16
They are not deleted, they stay there forever unless you delete them manually.

I think those files are made by gedit. When I create/edit files with nano the ~ files are not created.

---

### Post by sekinto on 2008-04-16
Edit>Preferences>Editor
Uncheck "Create a backup copy before saving"

---

### Post by Diabolis on 2008-04-16
oh cool, good to know thank you. I knew it was gedit.

---

### Post by ddh33 on 2008-04-16
Thanks, that takes care of it :D

---

