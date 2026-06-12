---
title: "Confusion about root permission and common folder tasks"
date: 2007-08-23
forum: General Help
---

### Post by youji on 2007-08-23
Hello. I'm rather new to Xubuntu and Linux and general. So far, I really enjoy using Xubuntu, but am having problem performing common folder tasks such as moving, renaming or deleting files. This is because the default permissions requires me to have root access. I'm not entirely sure how to set this privilege within my normal user account. I tried opening a terminal and using the "su" command, but this doesn't seem to affect anything.

What I basically want to do is delete a folder from /usr/share and add another file there. (for a program dependency) However, the options for paste, delete, etc. are grayed-out.

---

### Post by WiseElben on 2007-08-23
Hi, this is because you don't have permission to edit files and folders that is not inside your home folder (/home/your_name/). You have two options:

1. Use the command line using sudo. So deleting the folder would be: sudo rm -r /usr/share/folder
2. Use your file manager (I assume Thunar since you are using XFCE) as root. You can do this by starting Thunar in the terminal with sudo in front: sudo thunar

---

### Post by tszanon on 2007-08-23
> **youji said:**
> Hello. I'm rather new to Xubuntu and Linux and general. So far, I really enjoy using Xubuntu, but am having problem performing common folder tasks such as moving, renaming or deleting files. This is because the default permissions requires me to have root access. I'm not entirely sure how to set this privilege within my normal user account. I tried opening a terminal and using the "su" command, but this doesn't seem to affect anything.

What I basically want to do is delete a folder from /usr/share and add another file there. (for a program dependency) However, the options for paste, delete, etc. are grayed-out.
Ubuntu uses sudo to give normal users administrative rights. All you have to do is run any program you want preceeded by gksu (in Gnome) or su (in the terminal). For example, to run Nautilus, this is enough:
Alt+F2 (to open the Run Application dialog box)
```
gksu nautilus
```

It will ask for your password. The same applies in the terminal. If you try this:
```
rmdir /usr/share/some_dir
```
you know it won't work, because you don't have permission to do it. But if you do this:
```
sudo rmdir /usr/share/some_dir
```
the folder is gone.

---

### Post by youji on 2007-08-23
> **WiseElben said:**
> Hi, this is because you don't have permission to edit files and folders that is not inside your home folder (/home/your_name/). You have two options:

1. Use the command line using sudo. So deleting the folder would be: sudo rm -r /usr/share/folder
2. Use your file manager (I assume Thunar since you are using XFCE) as root. You can do this by starting Thunar in the terminal with sudo in front: sudo thunar

Thanks! Works like a charm.

---

### Post by aysiu on 2007-08-23
**Bad** ```
sudo thunar
``` **Good** ```
gksudo thunar
``` **Read more**
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by tszanon on 2007-08-24
Sorry, I didn't pay enough attention and didn't notice you are using Xubuntu. I never used Xubuntu, but I believe Nautilus isn't available.

---

### Post by WiseElben on 2007-08-24
> **aysiu said:**
> **Bad** ```
sudo thunar
``` **Good** ```
gksudo thunar
``` **Read more**
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Oh yes, I forgot. Thanks for the reminder.

---

