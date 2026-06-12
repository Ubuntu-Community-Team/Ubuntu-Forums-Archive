---
title: "file permissions"
date: 2008-06-23
forum: General Help
---

### Post by border.reaver on 2008-06-23
Hi,  I am new to this forum and relatively new to Ubuntu.  I am running v8.04 and have managed to put some files in the trash that won't delete, giving an 'access denied'.  The file permissions of these files say that my account owns them, but has 'read only' privileges.  I am unable to change to read/write while in the trash, and can't move them out of the trash.  Any suggestions would be appreciated.

---

### Post by dracayr on 2008-06-23
```
sudo rm ~/.local/share/Trash/files/*
```

dracayr

---

### Post by rampageoberon on 2008-06-23
```
sudo rm -f ~/.local/share/Trash/*
```

Hope that helps

---

### Post by sisco311 on 2008-06-23
Open your file browser as root and delete the files.
Press Alt+F2 and type:
```
gksu nautilus ~/.local/share/Trash/files/
```
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://ubuntuforums.org/showthread.php?p=5048176](http://ubuntuforums.org/showthread.php?p=5048176)

---

### Post by dracayr on 2008-06-23
> **rampageoberon said:**
> ```
sudo rm -f ~/.local/share/Trash/*
```

Hope that helps

my trash is in ~/.local/share/Trash/files/, not in ~/.local/share/Trash/

But I'm using e17, could be that the trash is managed differently there...

dracayr

---

### Post by sisco311 on 2008-06-23
~/.local/share/Trash contains two directories:
1.)files - deleted files
2.)info - files with restore information (path and deletion date)

---

### Post by border.reaver on 2008-06-23
Thanks to all for the responses!

I will try these when I get home to the Ubuntu machine.

---

