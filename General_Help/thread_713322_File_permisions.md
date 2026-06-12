---
title: "File permisions"
date: 2008-03-02
forum: General Help
---

### Post by carlo bolzonello on 2008-03-02
Hi All,

I have installed Ubuntu now and am installing a program, however i have to modify a file, which is fine i find it and ty and edit it, however ti says the following " cant open file to write". i have added my user to the root group and rebooted and still i get a issue with trying to edit the file. Can any one help please.

---

### Post by kdarkentity on 2008-03-02
Open a terminal and type gksu to get root access.

But also your going to want to gksu and type the name of the program you want to use to edit the file also. So to open a text file use.

"gksu gedit"

Also you need to specify where the file is loacted so the complete command would be something like

Gksu gedi /home/yourname/fileyouwanttoedit.txt

good luck.

---

### Post by The Cog on 2008-03-02
As well as **gksu gedit <filename>** you can do **gksu nautilus** to launch a file explorer with full rights. Using **sudo** (for command-line apps) and **gksu** (for GUI apps) launches them with full priviledge. You are effectively borrowing the keys when you do this.

Please undo adding yourself to the root group. It is a security risk. You should use sudo/gksu to launch priviledged programs only when that priviledge is actually needed. 

Try to mentally separate the roles of user and administrator. As the owner of the machine, you will inevitably perform both roles, but they are two distinct roles all the same. And users should not routinely carry the keys to the vault.

---

### Post by carlo bolzonello on 2008-03-03
Guy,

thank you very much it works like a charm. its hard when you come from a windows enviroment. Thank you very much

---

