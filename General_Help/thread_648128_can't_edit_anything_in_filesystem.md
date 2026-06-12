---
title: "can't edit anything in filesystem"
date: 2007-12-23
forum: General Help
---

### Post by m0p on 2007-12-23
i need to edit my /etc/network/interfaces 
to solve some wireless issues 

whenever i try to edit the file it says that i can't because i dont have permission to.
the user im logged in is in the root group but i still cant edit anything in the filesystem 

thanks alot

---

### Post by Craigus on 2007-12-23
Does it work if you do > gksu gedit /etc/network/interfaces

It should.

---

### Post by m0p on 2007-12-30
thanks craigus
 it works for editing that file

 but im still having trouble copying files into the filesystem 

i need to copy plugins for amsn to /usr/share/amsn/plugins

i tries 
sudo cp
 but it give me permission denied errors

---

### Post by taurus on 2007-12-30
You mean it won't let you do something like this?

```
sudo cp filename /usr/share/amsn/plugins
```
Or you can use nautilus filemanager.

```
gksudo nautilus
```

---

### Post by m0p on 2007-12-30
it works great 
the nautilus manager solved this problem 
im am very thankful for your help

---

