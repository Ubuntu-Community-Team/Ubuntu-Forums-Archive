---
title: "How to delete following folders:"
date: 2007-01-04
forum: General Help
---

### Post by Zlatan on 2007-01-04
/New Folder/
and
/media/windows/
?

I've already made right chmod for them (changed ownerships to my user), but access is denied nevertheless.

thank you

---

### Post by tszanon on 2007-01-04
chmod changes permissions (Read, Write, eXecute). To change ownership, you have to use chown:

```
chown <username>:<group> files
chown Zlatan:Zlatan /New\ Folder
```

OR you can do it the easy way:
```
sudo rmdir /New\ Folder
sudo rmdir /media/windows
```

Is this what you want?

---

### Post by energiya on 2007-01-04
if you want to remove a folder and all its contents use
```
sudo rm -R /media/windows
```
this way you can avoid the "Directory not empty" message... but be very carefull when using recursive delete, becouse it completly removes ALL files in the selected directory

---

### Post by majoridiot on 2007-01-04
> **energiya said:**
> if you want to remove a folder and all its contents use
```
sudo rm -R /media/windows
```
this way you can avoid the "Directory not empty" message... but be very carefull when using recursive delete, becouse it completly removes ALL files in the selected directory

close... add the "f" option to force without errors:

```
sudo rm -rf <directory>
```

---

### Post by strabes on 2007-01-04
gotta love the -f

gets me out of trouble a lot

---

### Post by tszanon on 2007-01-04
Never use sudo rm -rf <dir>, unless you're really sure of what you're about to do.
No mistakes allowed. If you specify the wrong directory, it's gone. If you specify / as the directory, it's ALL gone.

It's very useful, but it can be heart-stopping :)

---

