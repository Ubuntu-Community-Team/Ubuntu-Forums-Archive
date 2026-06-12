---
title: "Editing a file owned by root"
date: 2007-02-19
forum: General Help
---

### Post by mistypotato on 2007-02-19
I have opened a file for editing that I cannot save.

I used sudo gedit to open the file and that goes well.

But after editing I get the following error when I attempt to save....


You are trying to save the file on a read-only disk. Please, check that you typed the location correctly and try again.

The folder owner is root and file group is root

permessions are owner read write execute

Text View drwx------
Number view 700

The file is SETUP in the INBOUND folder for firestarter

Thanks

---

### Post by dcstar on 2007-02-19
> **mistypotato said:**
> I have opened a file for editing that I cannot save.

I used sudo gedit to open the file and that goes well.

But after editing I get the following error when I attempt to save....


You are trying to save the file **on a read-only disk**. Please, check that you typed the location correctly and try again.

The folder owner is root and file group is root

permessions are owner read write execute

Text View drwx------
Number view 700

The file is SETUP in the INBOUND folder for firestarter

Thanks

The message implies that the disk has been mounted Read Only, if it is your main disk then reboot and try again, if it is another drive then it must be mounted with Read/Write access.

---

### Post by 23meg on 2007-02-20
[QUOTE=mistypotato]I used sudo gedit to open the file and that goes well.[/QUOTE]You should use *gksudo* instead of *sudo* with graphical apps such as Gedit.

---

### Post by ardchoille42 on 2007-02-20
Also, never use sudo for GUI apps like gedit, sudo is for command line apps only.
The proper way to launch a root enabled GUI app is:

```

gksudo appname

```
 
For an explanation of the dangers of using sudo with gui apps, have a look at [this]("http://www.psychocats.net/ubuntu/graphicalsudo").

EDIT: 23meg beat me to it :)

---

### Post by cb474 on 2007-02-21
I'm trying to open a text file that has root permissions to edit it using:

sudo gedit

and

gksudo gedit

But every time I do it, the files opens as read only. Why is this?

[Edit: Nevermind. It's because the file is on an NTFS volume.]

---

### Post by drivel on 2007-02-21
You can chmod to 777,or sudo gedit XXXX

---

