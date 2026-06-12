---
title: "[SOLVED] scp and  file names with spaces"
date: 2008-06-28
forum: General Help
---

### Post by joris1977 on 2008-06-28
I read this wiki at [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
and it says:
quote: scp "New Document.odw" joe@laptop:"/home/joe/Summer 2005"

It seems to me i could use scp to move files  with empty spaces when i use " "

but when i do this i get:

joris@ubuntu:~$ scp [email]joris@noob.no-ip.org[/email]:"/home/joris/Waco Brothers - ... To the last dead cowboy.tar.gz" . 
[email]joris@noob.no-ip.org[/email]'s password: 
scp: /home/joris/seeding/Waco: No such file or directory
scp: Brothers: No such file or directory
scp: -: No such file or directory
scp: ...: No such file or directory
scp: To: No such file or directory
scp: the: No such file or directory
scp: last: No such file or directory
scp: dead: No such file or directory
scp: cowboy.tar.gz: No such file or directory

So clearly " " didn't help. Of course i can rename the .tar.gz file and then move the files. Or i can grab the files with nautilus, but both are a little extra work. So maybe someone has a solution to this small problem?

---

### Post by jpkotta on 2008-06-28
Maybe try more quotes:

```
scp user@host:"'filename with spaces'" destination
```

---

### Post by joris1977 on 2008-06-28
Yes!!! more quotes works

jpkotta thank you very much for your fast and well informed reply. :)
  
The ubuntu forums rock!

---

