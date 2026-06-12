---
title: "Can somebody help me ?"
date: 2008-03-31
forum: General Help
---

### Post by JoeThaDogg on 2008-03-31
hi i'm newbie on ubuntu can somebody help me ?
every time i try to install Azureus then It says 
```
joethadogg@joethadogg-desktop:~$ cd Desktop
joethadogg@joethadogg-desktop:~/Desktop$ sudo tar jxvf Azureus_3_0_linux.tar.bz2 C /opt/
tar: Azureus_3_0_linux.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: C: Not found in archive
tar: /opt: Not found in archive
tar: Error exit delayed from previous errors
```
**[SIZE="5"]or[/SIZE]**
```
joethadogg@joethadogg-desktop:~$ sudo apt-get install azureus
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

And then i don't konw what i sould do can somebody help me please

---

### Post by stefangr1 on 2008-03-31
To unpack that folder you should first use:

bunzip2 archive.tar.bz2

and then to extract the tar archive:

tar -xvvf archive.tar



Regarding the other error message: have you tried running 

sudo dpkg --configure -a     as the message suggested?


EDIT: it is not needed to use sudo to unpack files, and you should put a '-' sign for tar options. Also, when you don't know how something works, it is sometimes helpful to look in the man pages of a program.
You can get to the man pages of tar really easy with the command:  man tar

---

### Post by kellemes on 2008-03-31
> **stefangr1 said:**
> To unpack that folder you should first use:

bunzip2 archive.tar.bz2

and then to extract the tar archive:

tar -xvvf archive.tar
r

or combine like so..
```
tar -xvjf archive.tar.bz2 -C /opt/
```

---

### Post by JoeThaDogg on 2008-03-31
thanks very mush :)

---

### Post by Slushdoot on 2008-03-31
> **JoeThaDogg said:**
> hi i'm newbie on ubuntu can somebody help me ?
every time i try to install Azureus...Hi Joe, it looks like the others sorted your problem, but all things considered it might be better to install Azureus from the repositories.  That way it gets updated with the system and you don't have to worry about un-tarring anything yourself. :)

IIRC,
```
sudo apt-get install azureus
```
should work nicely if you have the gutsy-backports repository enabled.

---

### Post by JoeThaDogg on 2008-03-31
> **Slushdoot said:**
> Hi Joe, it looks like the others sorted your problem, but all things considered it might be better to install Azureus from the repositories.  That way it gets updated with the system and you don't have to worry about un-tarring anything yourself. :)

IIRC,
```
sudo apt-get install azureus
```
should work nicely if you have the gutsy-backports repository enabled.

hi I don't know if i have gutsy-backports or what it is

---

