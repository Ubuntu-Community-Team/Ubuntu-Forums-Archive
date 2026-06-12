---
title: "how can i create folders in file browser"
date: 2008-07-06
forum: General Help
---

### Post by masoud23 on 2008-07-06
I am new to ubuntu, how can i create folders in file browser? The alternative is not active in my browser but i do have administration rights!

PS: i want crate folders and copy file under folders in file system. do i have to use terminal?

---

### Post by rossdub on 2008-07-06
Ctrl + Shift + N will create a new folder in the file browser (called Nautilus if you're using Ubuntu). Alternatively, you can use the File Menu, Create Folder (Alt + F, then F).

From the command line, ```
mkdir foldername
``` will make a folder in your current directory (home by default-use the cd command to change to a different directory).  Hope that helps.

---

### Post by masoud23 on 2008-07-06
Tanks but I dont want to crate folder in my home dir. That works okej but  i want crate folders and copy file under folders in file system. There Create folder in file menu is not active.

---

### Post by masoud23 on 2008-07-06
Hi

How can I crate folder and copy files in File System from File browser? The crate file is not active when i am in file systems. i do have administration right on my computer.

Tanks in advance

---

### Post by cubeist on 2008-07-06
Only root can create (and delete) folders outside of your home directory.  sudo will allow you to do this.
```
sudo mkdir filename
```
then enter your password when prompted.  If your new to Ubuntu, I would advise caution moving things around outside of your home directory!

---

### Post by pieroxy on 2008-07-06
In nautilus, just right click on a folder (in the tree - the left part). You will be able to create a new folder inside the directory you clicked on.

Alternatively, you can also right click on an empty area on the right hand side. For folders containing lots of files, there may not be any blank area ...

Hope that helps

---

### Post by ladr0n on 2008-07-06
To create a folder in the filesystem where your regular user doesn't have write access, you need to open the file browser as root.  Type Alt + F2 or open a terminal, and enter ```

gksudo nautilus
```
You will be prompted for your password, and then the file browser will open and you will be able to create folders and move files wherever you want.  Be careful though, if you move the wrong thing it might break something.

---

### Post by tukuyomi on 2008-07-06
You can't create a file/folder outside your home as a normal user, as it is not recommanded to do such a thing.
Learn how to use sudo and its derivatives gksu and gksudo and be careful not do delete/alter something important in the system
```
(from a terminal (Applications -> Accessories))
$ sudo nautilus
(or)
$ gksudo nautilus
```

---

### Post by masoud23 on 2008-07-06
I am useing XAMPP (a packag with Mysql, Apache and php) files that runs in localhost as far as i now (from installation in xp) most be at htdocs folder which is installed at File system/opt/lampp/htdocs. is there another way to do this? not being able to crate folder and copy file directly from file browser when one has to seems unpractical in Linux i think!

---

### Post by masoud23 on 2008-07-06
tanks it worked!

---

### Post by nick_h on 2008-07-06
You will only have write permission for folders under your home directory.

To gain administrator access to the rest of the filesystem you will need to use the *sudo* or *gksudo* commands.

If you want administrator privilege in nautilus either run:
```
gksudo nautilus
```

or install the *naultius-gksu* package.

---

### Post by p_quarles on 2008-07-06
Duplicate threads merged.

---

