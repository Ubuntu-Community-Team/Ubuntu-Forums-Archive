---
title: "user rights and gui commands"
date: 2007-12-06
forum: General Help
---

### Post by ziphyre on 2007-12-06
Hi,

There is two issue which I do not understand completely but seems related to me. So if you can clarify me on he subject, I would be grateful.

1) On a terminal window, I create an empty file, change owner to root with sudo, than I'm able to delete it with my ordinary user.
```
ziphyre@neptune:~$ touch foo.txt
ziphyre@neptune:~$ sudo chown root:root foo.txt 
ziphyre@neptune:~$ ls -l foo.txt 
-rw-r--r-- 1 root root 0 2007-12-06 11:40 foo.txt
ziphyre@neptune:~$ rm foo.txt 
rm: remove write-protected regular empty file `foo.txt'? y
ziphyre@neptune:~$ ls -l foot.txt
ls: foot.txt: No such file or directory
ziphyre@neptune:~$ 

```

I was excepting a "sudo rm". Even if ziphyre has admin rights, how can he delete root's file?

2) Again, on a terminal, as user ziphyre, I can't give "shutdown -r now"  command, permission denied, it needs "sudo shutdown -r now". But on the gui, with the log out button, I can shutdown or restart the system as I like. 

How the system manages not to ask a password for a gui command that normally is a front end to the shutdown command?


Thanks

---

### Post by Jussi Kukkonen on 2007-12-06
> On a terminal window, I create an empty file, change owner to root with sudo, than I'm able to delete it with my ordinary user
 ...
I was excepting a "sudo rm". Even if ziphyre has admin rights, how can he delete root's file?
Deleting is possible if you have write (and execute) permissions on the *folder*, even if you do not have the rights on the actual file.

> 

2) Again, on a terminal, as user ziphyre, I can't give "shutdown -r now"  command, permission denied, it needs "sudo shutdown -r now". But on the gui, with the log out button, I can shutdown or restart the system as I like. 

How the system manages not to ask a password for a gui command that normally is a front end to the shutdown command?
The program giving the shutdown command is actually running as root (gdm and X both run as root)

---

### Post by ziphyre on 2007-12-06
Thanks...

---

