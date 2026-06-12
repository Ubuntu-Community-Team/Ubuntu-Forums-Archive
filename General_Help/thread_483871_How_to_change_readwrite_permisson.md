---
title: "How to change read/write permisson ??"
date: 2007-06-25
forum: General Help
---

### Post by GoranI on 2007-06-25
I installed Ubuntu 7.04 with wubi installer. It is installed on second partition of my hd - it is vfat. How to change permision to write on this disk (it is mounted).When I open some text file, I make some change, and when I try to save it on this disk it says that i don`t have permission. I checked and "root" is owner of this disk. I logged as root but I don`t know how to change ownership for other account for example for user account.
I tried to do this with Nautilus, but I can`t do anything from there.

Thanx for helping !!

---

### Post by moore.bryan on 2007-06-25
[I]use the chmod command in a terminal.. for example, if you're looking to change the file permissions for /media/usbdisk, then type
```
sudo chmod a=rwx /media/usbdisk
```
what you've done is tell linux to change the ownership (chmod) of /media/usbdisk for anyone (a) to read, write, and execute (rwx).  if you're concerned about security because other people use your computer and you don't want to give them access to /media/usbdisk, you can change the "a" to more specific users.
check out [this tutorial]("http://catcode.com/teachmod/"), the [wikipedia page]("http://en.wikipedia.org/wiki/Chmod") on chmod (which is pretty good), or the [chmod man page]("http://www.ss64.com/bash/chmod.html").
[/I]

---

### Post by Golyadkin on 2007-06-25
> **moore.bryan said:**
> 
what you've done is tell linux to change the ownership (chmod) of /media/usbdisk for anyone (a) to read, write, and execute (rwx). 

This is not quite correct, **chmod** does not change ownership but it changes permissions. You can change ownership of a file or directory with **chown**. Example: 

> 
chown fyodor:fyodor filename


changes the owner of the file "filename" to the user fyodor in the group fyodor.

---

### Post by GoranI on 2007-06-25
Logged as root I created a folder on mounted vfat partition, but again I can`t for example copy some file from my home folder to the mounted vfat disk.

---

### Post by GoranI on 2007-06-25
> **GoranI said:**
> Logged as root I created a folder on mounted vfat partition, but again I can`t for example copy some file from my home folder to the mounted vfat disk.

O.K. I copied file to mounted vfat disk. But how to do that without using root terminal. Is there a possibility to "make" for example gedit to save on mounted vfat disk, or some other application to do that through save as dialog.

---

### Post by Sjovan on 2007-06-25
I think the most easy way for a n00b changeing permisions is installing the KDE program called konqueror (apt-catche search konqueror).

Go to the terminal
```

su
konqueror
```

Go to the desierd folder and rightclick it. properties and fix the permisions. The reason you should use konqueror in stead of nautilus is because nautilus don't have the apply changes to all subfolder option.

---

### Post by moore.bryan on 2007-06-27
> **Golyadkin said:**
> This is not quite correct, **chmod** does not change ownership but it changes permissions. You can change ownership of a file or directory with **chown**. Example: 



changes the owner of the file "filename" to the user fyodor in the group fyodor.
*very true... i should have chosen my words more carefully. :-)*

---

### Post by Qu4k3R on 2007-06-27
You can also change something more (than you would with chown and chmod) with nautilus, or konqueror.
In properties, the permission tab might easily help you.

to use chown you might do

> 
chown <user>:<group> <file>


Have you solved it?

---

