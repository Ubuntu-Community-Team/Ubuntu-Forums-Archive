---
title: "&quot;Disappearing&quot; files after chmod"
date: 2012-11-21
forum: General Help
---

### Post by macmil on 2012-11-21
Hello,

I'm new to Ubuntu and rather new to Linux as a whole, so please be patient, I'll do my best.

Ubuntu 12.04 I believe, that's what I've got.

I've downloaded a .rar, unzipped it to a certain folder. Went to this folder.
I'm trying to run a program from this .rar, that's basically what happens:

```

... ./program
No permissions
... chmod 777 program
... ./program
File not found
```

I'm sure it IS there. Since I can see it.
Any help appreciated.

Thanks in advance

---

### Post by steeldriver on 2012-11-21
Hello and welcome

1. what filesystem is the file located on (native Linux e.g. ext2/3/4, FAT, NTFS or whatever)?

2. what architecture was the program compiled for and what is your system architecture (you can use the 'uname -a' command to find out if you are not sure)

---

### Post by jlangvand on 2012-11-21
If you type "ls", do you see the file "program" listed? Remember that Linux i case-sensitive. "Program", "program" and "ProGram" are three entirely different files. Also, make sure the file actually is a program :)

---

### Post by macmil on 2012-11-21
> **steeldriver said:**
> Hello and welcome

1. what filesystem is the file located on (native Linux e.g. ext2/3/4, FAT, NTFS or whatever)?

2. what architecture was the program compiled for and what is your system architecture (you can use the 'uname -a' command to find out if you are not sure)

1. FAT32

2. It was compiled for 32-bit, and it looks like I accidentally installed 64-bit ubuntu (x86_64). Damn.

> 
If you type "ls", do you see the file "program" listed? Remember that Linux i case-sensitive. "Program", "program" and "ProGram" are three entirely different files. Also, make sure the file actually is a program 


It is a program for sure, and yes, it is listed. I was very careful about case sensitivity ;)

Ok so now I'm gonna try running it somehow and post results when I get some. Thanks so far

---

### Post by steeldriver on 2012-11-21
OK so you have at least 2 issues there (1) FAT probably doesn't understand Linux execute permissions and (2) you cannot directly run 32-bit binaries on a 64-bit system (it might work with ia32-libs - I don't know for sure)

---

### Post by macmil on 2012-11-21
Alright, worked with the **ia32-libs**
Problem solved. Thank you for very fast and accurate reply

Is there any type of "Beer" system on this forum? (I mean, thanks-button) :D

---

### Post by steeldriver on 2012-11-21
Happy to help - as far as 'beer' is concerned "what goes around, comes around" :)

---

