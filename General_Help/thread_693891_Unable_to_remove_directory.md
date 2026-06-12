---
title: "Unable to remove directory"
date: 2008-02-11
forum: General Help
---

### Post by Aeph on 2008-02-11
I installed something to my desktop by accident, then reinstalled it where I wanted it to go. Unfortunately, the directory is still on my desktop and I can't delete it. It has the little lock emblem next to it. Being new to Linux, I don't know what code, if any, to use to get rid of it.

---

### Post by hyperandy on 2008-02-11
If it's just the icon left and you already removed the program. You can just go into terminal (applications --> accessories--> terminal) then type cd Desktop then type ls (this will list all the files on your desktop) then just type sudo rm file or sudo rm -f file  File being the file you are trying to remove. 

Just use your root password when it ask.

hope that helps

remember CAPS and lowercase are important


sorry sudo rm -r dir and sudo rm -rf dir
I just read your not removing a file but a directory. sorry replace dir with the directory your removing

it sounds like you just don't have permissions to that file using sudo will temporarily give you root access and you can remove it!


the -f means force remove and should only be used as a last resort

---

### Post by lotus49 on 2008-02-11
> **Aeph said:**
> I installed something to my desktop by accident, then reinstalled it where I wanted it to go. Unfortunately, the directory is still on my desktop and I can't delete it. It has the little lock emblem next to it. Being new to Linux, I don't know what code, if any, to use to get rid of it.

It's probably just a permissions problem.

Type:
$ sudo rm -rf <insert file name here>

you will be asked for your password, type it in and all should be well.

NOTE be careful what you type, if, for example you typed

$ sudo rm -rf /

all the files on your machine would be deleted.

---

### Post by Aeph on 2008-02-11
Thanks, that worked perfectly.

---

### Post by harold4 on 2008-02-11
Normally, you don't want to execute "sudo rm -rf" when you don't know why.  Keep that in mind for next time ;)

---

