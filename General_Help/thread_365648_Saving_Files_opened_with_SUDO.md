---
title: "Saving Files opened with SUDO ????"
date: 2007-02-19
forum: General Help
---

### Post by mistypotato on 2007-02-19
I have opened a file for editing that I cannot save.

I used sudo gedit  to open the file and that goes well.

But after editing I get the following error when I attempt to save....


**[COLOR="Red"][SIZE="3"]You are trying to save the file on a read-only disk. Please, check that you typed the location correctly and try again.[/SIZE][/COLOR]**

The folder owner is root and file group is root

permessions are owner read write execute

Text View  drwx------
Number view 700

The file is SETUP in the INBOUND folder for firestarter

Thanks

---

### Post by yabbadabbadont on 2007-02-19
Did you literally type that?  The correct command would be: sudo gedit filename

Linux is case sensitive.  :)

---

### Post by highneko on 2007-02-19
> You are trying to save the file on a read-only disk.
I don't know but it sounds to me like maybe a partition was mounted read only?

---

### Post by mistypotato on 2007-02-19
The entire disk is one partition.

---

