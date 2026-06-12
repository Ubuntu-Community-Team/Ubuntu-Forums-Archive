---
title: "cannot create new folder or transfer file"
date: 2008-05-10
forum: General Help
---

### Post by VgForce on 2008-05-10
Does anyone know why i cant make new folder or transfer file from or into file system directory. And how do i overide this??? thanks alot.

---

### Post by ghost_ryder35 on 2008-05-10
what directory are you trying to make this folder in?
/
/root
/home
/usr
/bin
/var
etc...

---

### Post by TeoBigusGeekus on 2008-05-10
You need to have root permissions to alter your file system.
You can do this manually preceding every command with sudo (SuperUserDO)

```
sudo mkdir /path/to/folder/foldername
```

to create a directory,

```
sudo cp /initial/location/filename.extension /final/location/
```

to copy a file and

```
sudo cp -r /initial/location/foldername /final/location/
```

to copy a folder.

---

### Post by VgForce on 2008-05-10
awsome :) thanks alot for helping. But Is there another way to implement this in the right click like what ubuntu have?

---

### Post by TeoBigusGeekus on 2008-05-10
```
gksudo nautilus
```
But be careful as you will be using nautilus as root - you could easily screw up your system.

---

### Post by VgForce on 2008-05-12
I ran the command but it still wont allow me to create new folder or modity file in main system :confused:

---

### Post by VgForce on 2008-05-12
i believe it something has to do with root setting but im just not sure how to do it, i tried logg on to root but no change.

---

### Post by lswest on 2008-05-12
where are you trying to create the folder?

also - hit alt+F2 and type "gksudo nautilus" without the quotes, it should prompt you for a password.  Then you should be able to modify anything in your system.

---

### Post by VgForce on 2008-05-13
Doesn't work, thanks for trying though

---

