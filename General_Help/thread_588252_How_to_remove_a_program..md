---
title: "How to remove a program."
date: 2007-10-23
forum: General Help
---

### Post by eXeCuTeR+ on 2007-10-23
How do I delete the 'licq' folder in usr/local/share?
I downloaded Licq and now I wanna delete it with all it's components.
I can't remove it to trash and I can't find it on Add/Remove Programs.
I just wanna delete this folder.
Please help ASAP! Thanks.

---

### Post by marcantonio on 2007-10-23
sudo rm -rf /usr/local/share/licq

---

### Post by karth on 2007-10-23
If you installed it from a repository, you could use aptitude to uninstall it
```
aptitude remove licq
```

or if you manually compiled and "make install"-ed it, and if by chance there is an uninstall target in the source package
Go to the source code directory and then
```
make uninstall
```

But this is unlikely to work...

The last chance is```
 rm -rf /usr/local/share/licq
```

---

### Post by eXeCuTeR+ on 2007-10-23
Sweet, thanks.
what does aptitude remove do?
I did it with rm -rf /usr/local/share/licq :)

---

### Post by karth on 2007-10-23
aptitude is a console frontend to apt-get, which does the same work, plus better dependencies management.
This means you have to have root permissions to use it succesfully, i.e. via sudo

try ```
sudo aptitude
```

---

### Post by eXeCuTeR+ on 2007-10-23
Oh the file has been moved to the usr/local/lib.
How do I delete it from there and what is that folder?
I tried rm -rf /usr/local/lib/licq but it doesn't work, it says: Premission denied.

Help!

---

### Post by Maestro23 on 2007-10-23
> **eXeCuTeR+ said:**
> Oh the file has been moved to the usr/local/lib.
How do I delete it from there and what is that folder?
I tried rm -rf /usr/local/lib/licq but it doesn't work, it says: Premission denied.

Help!

The folder is owned by** root**.  You need **sudo** in front of your command.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Installing Software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Linux File Structure (LinuxCommand.org): [http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

---

### Post by marcantonio on 2007-10-23
Make sure sudo is in front of it, e.i.:

```
sudo rm -rf /usr/local/lib/licq
```

---

