---
title: "cannot execute in current directory"
date: 2006-11-14
forum: General Help
---

### Post by vob on 2006-11-14
Hi there,

this is kubuntu 6.06 on Intel686.
I have problems executing files in my current directory. I have

```
$ ls -al
total 3268
drwxr-xr-x 2 volker volker    4096 1998-05-14 19:00 .
drwxr-xr-x 4 volker volker    4096 1998-05-14 18:59 ..
-rwx------ 1 volker volker   52412 1998-05-14 19:00 grconvert
-rwx------ 1 volker volker 1099084 1998-05-14 18:54 xmgr-dynamic
-rwx------ 1 volker volker 2168388 1998-05-14 18:54 xmgr-semistatic
```

which looks quite well. However, when I try to execute one of the programs I get

```
$ ./xmgr-dynamic
bash: ./xmgr-dynamic: No such file or directory

```

The parent directories also have execute permissions set. A similar error command ("command not found") occurs when I try the same under the tcsh. I also tried to copy the files to a directory (~/bin) where other scripts and programs have already been executed, but this gives the same error. 

Any ideas what might be the reason? 
Thanks in advance

---

### Post by taurus on 2006-11-14
Is xmgr-dynamic happened to be a script file or something?  What does it say when you run this command from a terminal?

```
file xmgr-dynamic
```

---

### Post by vob on 2006-11-14
It's a binary executable:

```
$ file xmgr-dynamic
xmgr-dynamic: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
```

However, I have the very same problem with a bourne shell script in another directory (but also under /usr/local) where I used chmod u+x to make it executable.

---

### Post by taurus on 2006-11-14
Then, what's the output of this command?

```
ldd xmgr-dynamic
```

---

### Post by vob on 2006-11-14
As one might have expected :-(

```
$ ldd xmgr-dynamic
/usr/bin/ldd: line 117: ./xmgr-dynamic: No such file or directory

```

---

### Post by taurus on 2006-11-14
There is something wrong with that file!  What happens if you run those two commands with the other file, xmgr-semistatic?

---

### Post by streeto on 2006-11-14
Please don't feel offended by my question, but, are you 'volker'? I mean, are you allowed to chmod 777 the files and execute them?

---

### Post by vob on 2006-11-14
> **taurus said:**
> There is something wrong with that file!  What happens if you run those two commands with the other file, xmgr-semistatic?

Seems like you are right: I just checked that other script in emacs and it turned out that it started like this 
```
#! /bin/sh^M
^M

```

And indeed, running bash on this file tells me
```
$ ant~ --help
bash: ./ant~: /bin/sh^M: bad interpreter: No such file or directory
```

These ^M control sequences indicate carriage return/line feeds that have not been properly converted to linux's linefeeds. For the shell script it's easy to remove them, but for the binary file I have no idea. Do you think something like this might have occurred here. They came out of a tar.gz archive downloaded from an ftp-server using fierfox... I already tried downloading it again using binary mode in plain ftp session, but no success :-(

Oh, as for the other two files it's exactly the same problem

---

### Post by taurus on 2006-11-14
You need to use dos2unix to strip off those ^Ms at the end of each line!!!  Also, you have to replace #!/bin/sh with #!/bin/bash...

---

### Post by vob on 2006-11-14
> **streeto said:**
> Please don't feel offended by my question, but, are you 'volker'? I mean, are you allowed to chmod 777 the files and execute them?

Yes I am, forgot to mention that, sorry. But chmod 777 on these files doesn't help either.

---

### Post by vob on 2006-11-14
> **taurus said:**
> You need to use dos2unix to strip off those ^Ms at the end of each line!!!  Also, you have to replace #!/bin/sh with #!/bin/bash...

Yeah, that is one way to do that. But that won't help me with the other (binary) file :-(

---

### Post by streeto on 2006-11-14
> **taurus said:**
> You need to use dos2unix to strip off those ^Ms at the end of each line!!!  Also, you have to replace #!/bin/sh with #!/bin/bash...

last time I checked (long time ago, ubuntu 5.10), dos2unix did not come by default with the distribution. I use todos/fromdos commands for converting to and from dos files. dos2unix and unix2dos are symlinks to these commands. If they are not installed by default, try

sudo aptitude install tofrodos

---

### Post by vob on 2006-11-14
Well, the problem seem solved insofar as, after figuring out how to build the program from source (it turned out that there have been a number of lesstif libraries missing on my system) I now have the program up and running. Seems like these missing libs did not allow me to run the program, even though the "semistatic" version should not require them (but that may be true for only part of the libs). Still I wish that the shells might be a little bit more verbose about the rason for the failure, but at this point I don't mind too much.

Anyway, thanks for your replies and suggestions, which helped me to overcome the deadlock in which I had ended up this afternoon.

---

