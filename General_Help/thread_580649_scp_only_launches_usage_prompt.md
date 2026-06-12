---
title: "scp only launches usage prompt"
date: 2007-10-18
forum: General Help
---

### Post by lwnexgen2 on 2007-10-18
Hey  Guys,

I'm having an exceedingly strange problem. Whenever I try to use scp, the only thing that will come up is the usage prompt for scp, even if I have the syntax perfectly right.

for instance:

sam@sam-desktop:~$ scp [email]sgardner@best-emperor.cs.wisc.edu[/email]:~cs368-1/public/html/assignments/A2/linux/studentDB.o

brings up:

usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 [...] [[user@]host2:]file2

That's all that will come up for scp, no matter what I put in, and no matter what shell i use to run the command.

Any ideas?

---

### Post by bodhi.zazen on 2007-10-18
scp <file_to_copy> <destination>

so 

> scp foo [email]sgardner@best-emperor.cs.wisc.edu[/email]:~cs368-1/public/html/assignments/A2/linux/studentDB.o

copies the file foo to the server ...

> scp [email]sgardner@best-emperor.cs.wisc.edu[/email]:~cs368-1/public/html/assignments/A2/linux/studentDB.o/foo .

copies foo from the server to the current directory

---

### Post by lwnexgen2 on 2007-10-19
> **bodhi.zazen said:**
> scp <file_to_copy> <destination>

so 



copies the file foo to the server ...

hmm, are you saying my syntax is all wrong for copying a file *from* the server?

---

### Post by anubhavrocks on 2007-10-19
i think this is what you want
```
sam@sam-desktop:~$ scp sgardner@best-emperor.cs.wisc.edu:~cs368-1/public/html/assignments/A2/linux/studentDB.o   ./ 
```

this will copy studentDB.o to present directory,you missed the DESTINATION part in your command.

---

### Post by lwnexgen2 on 2007-10-19
> **anubhavrocks said:**
> i think this is what you want
```
sam@sam-desktop:~$ scp sgardner@best-emperor.cs.wisc.edu:~cs368-1/public/html/assignments/A2/linux/studentDB.o   ./ 
```

this will copy studentDB.o to present directory,you missed the DESTINATION part in your command.

hehe. completely missed that. Thanks!

---

