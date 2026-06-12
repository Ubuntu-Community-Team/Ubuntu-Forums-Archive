---
title: "can not run a file from the terminal using ./"
date: 2017-02-06
forum: General Help
---

### Post by aliole4731 on 2017-02-06
hi,so I'm learning to compile and run c files using the terminal.I made a c file on gedit and saved it as a.c
1.i used gcc -c a.c -o a
2. i then use ./a to run but i get this error " bash: ./a: Permission denied".
3.okay so i  google a bit and learn that i have to change the permission  so i use chmod +x a and run ./a then i get this error :"bash: ./a: cannot execute binary file: Exec format error".
4. someone suggested i change to root user but i read its risky and not a good practice.
5.I was a bit curious so made a text file say,b.txt and ran it using ./b.txt and you guessed it i again got the error:" bash: ./a: Permission denied"
6.but when i repeated step 4 with this file it ran:p
so,can anyone tell me what to do?should i change to root user?is there any other way to run the c file?

---

### Post by The Cog on 2017-02-06
From **man gcc** :       >  When you invoke GCC, it normally does preprocessing, compilation, assembly and linking.  The "overall options" allow you to stop this process at an intermediate stage.  For example, the -c option says not to run the linker.  Then the output consists of object files output by the assembler.
Try compiling without the -c option.

---

### Post by TheFu on 2017-02-06
Another thing to consider ....

Don't use non-Linux file systems when doing development work.  The tools expect Unix/Linux permissions.

---

### Post by steeldriver on 2017-02-06
> **The Cog said:**
> From **man gcc** :       
Try compiling without the -c option.

This

The -c option causes gcc to stop at the object code stage - without linking the standard libraries necessary to run as an independent binary executable

---

### Post by aliole4731 on 2017-02-07
> **TheFu said:**
> Another thing to consider ....

Don't use non-Linux file systems when doing development work.  The tools expect Unix/Linux permissions.
what do you mean by non-linux file system?I'm sorry but I'm new to this.How else can i compile a c code then?

---

### Post by aliole4731 on 2017-02-07
> **The Cog said:**
> From **man gcc** :       
Try compiling without the -c option.
yes thank you.now it works!

---

### Post by The Cog on 2017-02-07
> **aliole4731 said:**
> what do you mean by non-linux file system?I'm sorry but I'm new to this.How else can i compile a c code then?

He means do it on a proper *nix filesystem like ext2/3/4 etc. Not on a FAT or NTFS drive, because those MS filesystems cannot store unix file ownership and permission properties.

You can mark the thread fixed from the Thread Tools pull-down menu at the top right of the page.

---

