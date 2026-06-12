---
title: "How do I install FASM at the end of file name"
date: 2012-11-24
forum: General Help
---

### Post by andreamillspaugh on 2012-11-24
Hi, how do I install FASM at the end of the file name says fasm-1.70.03.tgz but when I extract it has an exe file in it even thought it says linux at the fasm website
[http://flatassembler.net/download.php](http://flatassembler.net/download.php) I clicked on linux, is there something im doing wrong, please help thanks:)

---

### Post by zombifier25 on 2012-11-24
Weird. I downloaded the Linux version and got the correct package (with a Linux executable). Try redownloading.
(note: I don't know what FASM is)

---

### Post by andreamillspaugh on 2012-11-24
I downloaded both linux unix and the unix one i get a file like this fasm.o is that the file I open and if it is how do I do that, And the linux one file i get is fasm and when i double click it dose not open, and so i went to properties and it says its a executable (application/x-executable) how do I open it if this is the right file, I realy new to ubuntu so im just understanding how everything works but what fasm is called Flat Assembler, please help me.

---

### Post by zombifier25 on 2012-11-24
You need to launch the "fasm" executable in the terminal. Open a terminal:
```
cd /path/to/file
./fasm
```
(change /path/to/file to the folder where the executable sits. For convenience, put it in your home folder so you don't have to cd)

---

### Post by andreamillspaugh on 2012-11-24
```
andrea@millspaughdixon:~$ cd /home/andrea/Downloads/fasm
andrea@millspaughdixon:~/Downloads/fasm$ ./fasm
flat assembler  version 1.70.03
usage: fasm <source> [output]
optional settings:
 -m <limit>    set the limit in kilobytes for the available memory
 -p <limit>    set the maximum allowed number of passes
 -s <file>     dump symbolic information for debugging
andrea@millspaughdixon:~/Downloads/fasm$ 


```

sorry to ask this but what do I do from here?

---

### Post by zombifier25 on 2012-11-25
Like what I said, I don't know how to use it. You're doing it correctly though, just feed the program some parameters, like it said:
```
./fasm <source> [output]
```

---

