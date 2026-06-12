---
title: "Im Ready now"
date: 2008-02-13
forum: General Help
---

### Post by AuToFiRE on 2008-02-13
I have been on Ubuntu since September and I absolutely love it, but now i have a question because i want to get a lot more advanced

question 1.  what is the purpose of each folder in root( / )

question 2. where are the main executables for programs installed located

---

### Post by kesman on 2008-02-13
[http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/](http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/)

for applications, you could try with
```

locate packagename
whereis packagename
dpkg -l packagename

```

---

### Post by MONODA on 2008-02-13
try visiting :
[www.linuxcommand.org](www.linuxcommand.org)
learn lots about linux and how to use the terminal and how to write scripts to do repetitive tasks.

---

### Post by mojoman on 2008-02-13
> **AuToFiRE said:**
> I have been on Ubuntu since September and I absolutely love it, but now i have a question because i want to get a lot more advanced

question 1.  what is the purpose of each folder in root( / )

question 2. where are the main executables for programs installed located

1) You can figure out a lot of what they contain by looking at what they are called or by peeking inside them. bin contains programs, sbin contains programs used by the superuser (root), tmp contains temporary files, proc contains running processes, dev contains drives  (proc and dev doesn't really contain files), var contains logs, boot is the boot files (sometimes put on a separate partition), root is roots home directory, usr contains programs for users, lib contains libraries (I think akin to dll files or something?) and etc contains a lot of configuration. There are a lot of exceptions and I probably missed a lot but I think that's the gist of it. 

2) use the command ```
whereis foo
``` It will tell you the path to the binary used to execute the program.

---

### Post by AuToFiRE on 2008-02-13
Thank you very much you guys are awsome

---

### Post by MONODA on 2008-02-13
also check out:
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)
pretty cool website
btw trust me read through some of linuxcommand.org its great I leanred how to write lots of scripts that help me a LOT with my work. I was even able to write a script to automatically compile a tarball :)

---

