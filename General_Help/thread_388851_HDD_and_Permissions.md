---
title: "HDD and Permissions"
date: 2007-03-20
forum: General Help
---

### Post by Imsati on 2007-03-20
I'm trying to delete a folder that was accidentally installed to my Desktop. When I try to Trash it, a popup says I don't have permission to do so. How do I go about removing it from the Desktop?

Also, When I open 'Storage Media' from the Panel, all I can see are my XP drives (OS, Software, and my personal folder) listed as sda1, 5, and 6 --my Root and Home drives are not shown. I would like to: first, see my Kubuntu drives; and secondly rename everything to my personal tastes. I looked around at all the logical places under system settings and played with Administrator Mode, but to no avail.

Thanks!

--Jay

---

### Post by Imsati on 2007-03-20
One bump, then I'll post up in the Beginner's section tomorrow.
Thanks in advance!
--Jay

---

### Post by Mr. C. on 2007-03-21
Open a Terminal window.

Type :

```
cd Desktop
ls -l

```
and you will see a list of your files and folders on your Desktop.  To remove the folder:
```

rm -rf '*FILENAME*'
```

Change *FILENAME* above with the exact filename you want to delete.  Keep the single quotes as I have them, so that you don't accidentally delete other files.

MrC

---

