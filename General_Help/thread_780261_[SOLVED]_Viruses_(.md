---
title: "[SOLVED] Viruses :("
date: 2008-05-03
forum: General Help
---

### Post by vikasmk on 2008-05-03
i think my usb drive is infected with viruses. i tried rm command on them but they get deleted and reappear again how do i get rid of them....??vikasmk@ubuntu:/media/VIKIDRIVE$ rm *.exe

```
vikasmk@ubuntu:/media/VIKIDRIVE$ ls
adventure games.exe  latest songs.exe   New Folder(9).exe  softwares.exe
DarkReign2           models             New Folder.exe     Ubuntu 8.04
documents.exe        New Folder(2).exe  pics.exe
file.exe             New folder(3).exe  secrets.exe
vikasmk@ubuntu:/media/VIKIDRIVE$ rm *.exe
vikasmk@ubuntu:/media/VIKIDRIVE$ ls
DarkReign2  models  Ubuntu 8.04
vikasmk@ubuntu:/media/VIKIDRIVE$ ls
DarkReign2  models  Ubuntu 8.04
vikasmk@ubuntu:/media/VIKIDRIVE$ ls
adventure games.exe  latest songs.exe   New Folder(9).exe  softwares.exe
DarkReign2           models             New Folder.exe     Ubuntu 8.04
documents.exe        New Folder(2).exe  pics.exe
file.exe             New folder(3).exe  secrets.exe
```

---

### Post by lynxus on 2008-05-03
Make sure you UNmount the drive correctly before removing it.

Also try a ls -a ( to see any hidden files )


If you dont un-mount it may not write the changes to the drive and the files will stay.

-G

---

### Post by vikasmk on 2008-05-03
```
vikasmk@ubuntu:/media$ umount V*
/sbin/umount.hal: VIKIDRIVE is not recognized by hal

```
 name of the drive is VIKIDRIVE , its not umounting.

---

### Post by lynxus on 2008-05-03
Might be  a bit extreme, I dont know much about mounting and unmounting :( so cant help there.

However, ( As i said a bit extreme )
Maybe:
- delete the files
- ls -a ( to confirm they gone )
- Shutdown the computer.
- removed drive
- power up
- plug drive in and confirm they have gone?

Maybe the system shutting down will somehow unmount the drive safely?

---

### Post by Bruno Barrera on 2008-05-03
Try 

```

sudo umount -i V*

```

---

### Post by thisiam on 2008-05-03
If you are sure those are viruses you should use gparted and format the drive clean, quickest way to solve this.

---

### Post by JerMe on 2008-05-03
> **thisiam said:**
> If you are sure those are viruses you should use gparted and format the drive clean, quickest way to solve this.

^^^ ++.  If you don't trust 'em, nuke 'em.

---

