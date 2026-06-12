---
title: "Backup troubles"
date: 2008-05-16
forum: General Help
---

### Post by hey2222 on 2008-05-16
Well as the title says I'm having troubles backing up my Document folder.
My problem is i dont want to back up a folder called "Hey There" out of all the other folders in my Documents DIR so this is what I type.

tar cvpzf backup.tgz --exclude=(press tab and instead of Hey There/ i get )Hey\ There/ --exclude=backup.tgz *

The only thing that seems to work is --no-recursive but i have other folders i want to backup. So how do i exclude the file Hey There/, but with tab its Hey\ There/ without renaming the folder if possible.

---

### Post by eldragon on 2008-05-16
you are gzipping them for any particular reason?

do you want the backup automated?


there is a great backup script that uses rsync to do just that.
its called rsnapshot.

you can add excludes, schedule it with cron, and its incremental, and if you are backing up in the same file system, it just doesnt waste extra space (just the different versions of files ocupy extra space).

try it out :D

---

### Post by talz13 on 2008-05-16
> **hey2222 said:**
> Well as the title says I'm having troubles backing up my Document folder.
My problem is i dont want to back up a folder called "Hey There" out of all the other folders in my Documents DIR so this is what I type.

tar cvpzf backup.tgz --exclude=([color=red]press tab and instead of Hey There/ i get )Hey\ There/[/color] --exclude=backup.tgz *

The only thing that seems to work is --no-recursive but i have other folders i want to backup. So how do i exclude the file Hey There/, but with tab its Hey\ There/ without renaming the folder if possible.

That's what "Hey There" is.  It has to escape the space with a '\' so that it knows it's not separate entries.  Did you try running it with "Hey\ There"?  Did it not actually exclude that folder?

---

### Post by hey2222 on 2008-05-16
> **talz13 said:**
> That's what "Hey There" is.  It has to escape the space with a '\' so that it knows it's not separate entries.  Did you try running it with "Hey\ There"?  Did it not actually exclude that folder?

Wow it worked thanks. Learned something new today too.

---

