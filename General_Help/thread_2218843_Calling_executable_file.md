---
title: "Calling executable file"
date: 2014-04-22
forum: General Help
---

### Post by sitro on 2014-04-22
hello,

I m in trouble since I cannot launch a command from a file that exists on my files system but when I start the file the shell says that the file is missing.

So the file is  :
# ls -al /usr/local/lexmark/printer_utility/jre/bin/java
-rwxrwxr-x 1 noel noel 47308 mai    2  2012 /usr/local/lexmark/printer_utility/jre/bin/java

when I launch the executable file I get :

# /usr/local/lexmark/printer_utility/jre/bin/java
bash: /usr/local/lexmark/printer_utility/jre/bin/java: Aucun fichier ou dossier de ce type
(no file or directory)

How is it possible ?
thanks for help

---

### Post by Yellow Pasque on 2014-04-22
EDIT: NVM
I misunderstood the code snippet.

---

### Post by TheFu on 2014-04-22
Don't run as root!!!!!!

Does "/usr/local/lexmark/printer_utility/jre/bin/java" exist? Is it really the java executable?  No disrespect towards other replies, but if the full path to the program is specified, there is NO NEED to use ./ to run anything. 1 is full path and the other is relative path - both should work.

Java normally requires a JAVA_HOME environment variable to locate support files. Is that set correctly?  Since this is likely for a printer driver, I'd ask if you followed the detailed installation steps.  Just installing the package is usually not enough.

---

### Post by sitro on 2014-04-22
thank's for the answers.
That's right, this program (java) is need to install a printer driver (the lexmark S305 printer that I downloaded from the lexmark site) I have installed it on my few ubuntu computers, I had never problem with it)  the java program is embeded with the printer driver package (JRE) so it is why the java program is in this directory.
the detailed installation steps are very easy : dpkg -i <the package> !!!
But when i installed the package on this computer, I got an error (file or directory java is missing)
So I tried manually to access the java program in the directory and I got the error that I show in the first message even if the file java is really there in the right directory.
Even If I go throught the directory  (#cd [COLOR=#000000]/usr/local/lexmark/printer_utility/jre/bin/java) [/COLOR]and launch the program with the relative path ( ./java) I got the same error.

The just particularity of this computer is a macbook 3.1 white 13" bought in 2007-2008. The computer is in dual boot with MacOS and Ubuntu.
The memory has been upgraded from 1Go to 1,5Go and the hard disk has been changed twice for the purchase. the ubuntu is almost a fresh install after the recently change of the hard disk.

therefore  I return to my original question: how is it possible that executable file on the file system is displayed missing ?

---

### Post by 3rdalbum on 2014-04-22
What is the output of:

file /usr/local/lexmark/printer_utility/jre/bin/java

---

### Post by sitro on 2014-04-23
this is the friend's pc  that I wanted to install the driver. For now I don't have the Pc near me. I leave unanswered, I shall resume when I have the pc.


But from memory I launched this command "file" and it showed the standard result, something like :
"ELF 32-bit LSB  executable, Intel 80386,..."

---

### Post by TheFu on 2014-04-23
Set JAVA_HOME correctly for the system.  If java is NOT installed (smart from a security perspective), then install it.

---

### Post by spjackson on 2014-04-23
> **sitro said:**
> this is the friend's pc  that I wanted to install the driver. For now I don't have the Pc near me. I leave unanswered, I shall resume when I have the pc.


But from memory I launched this command "file" and it showed the standard result, something like :
"ELF 32-bit LSB  executable, Intel 80386,..."
I'd suggest 2 things to check.
1. Is the java executable of the right type for the architecture it is running on? i.e. does "file" report similar information as "file /bin/ls" for example?
2. Sometimes the lack of a library dependency can surprisingly result in "[COLOR=#000000]no such file or directory". See for example[/COLOR] [http://ubuntuforums.org/showthread.php?t=2031679](http://ubuntuforums.org/showthread.php?t=2031679) . Therefore what is the output of "ldd [COLOR=#000000]/usr/local/lexmark/printer_utility/jre/bin/java"?[/COLOR]

---

### Post by sitro on 2014-04-23
thank you for the suggestion that I will check next time when I have the PC.
an other things to say :
to this problem, I launched the original java programm in /usr/bin/java (it is the java-7-openjdk via alternatives)
I got a normal answer :
> $ whereis java
java: /usr/bin/java /etc/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz
noel@britanicus:~$ file /usr/bin/java 
/usr/bin/java: symbolic link to `/etc/alternatives/java' 
noel@britanicus:~$ ls -al /etc/alternatives/java
lrwxrwxrwx 1 root root 45 août  12  2013 /etc/alternatives/java -> /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
noel@britanicus:~$ java
Syntaxe : java [-options] class [args...]
           (pour l'exécution d'une classe)
   ou  java [-options] -jar jarfile [args...]
           (pour l'exécution d'un fichier JAR)
.....


---

### Post by sitro on 2014-04-30
I found the problem : idiot.
the system is in 64b and the program in 32b

 ```

noel@MacBook:~$ file /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java
/usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x49fe1f4d463ec8b3a3404bf5b21b88b6ad792188, stripped
noel@MacBook:~$ uname -a
Linux MacBook 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
noel@MacBook:~$ 


noel@MacBook:~$ file /usr/local/lexmark/printer_utility/jre/bin/java
/usr/local/lexmark/printer_utility/jre/bin/java: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, not stripped
noel@MacBook:~$ 


noel@MacBook:~$ ldd /usr/local/lexmark/printer_utility/jre/bin/java
    not a dynamic executable
noel@MacBook:~$ 

```
so when Iget the 64b version it's correct :
```
noel@MacBook:~$ file /usr/local/lexmark/printer_utility/jre/bin/java
/usr/local/lexmark/printer_utility/jre/bin/java: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.4.0, not stripped
noel@MacBook:~$ ldd /usr/local/lexmark/printer_utility/jre/bin/java
    linux-vdso.so.1 =>  (0x00007fff8f538000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f0cd7a31000)
    libjli.so => /usr/local/lexmark/printer_utility/jre/bin/../lib/amd64/jli/libjli.so (0x00007f0cd7926000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f0cd7722000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f0cd735a000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f0cd7c6a000)
noel@MacBook:~$
```

---

