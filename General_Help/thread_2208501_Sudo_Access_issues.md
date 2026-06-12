---
title: "Sudo Access issues"
date: 2014-02-28
forum: General Help
---

### Post by jacob23 on 2014-02-28
Hello All,

So just today I received my new laptop in the post and proceeded to put ubuntu 12.04 on it.

On my old Laptop I did a lot of C++ coding using the g++ compiler.

It seems that on my new laptop, I need to add "sudo" to just about every command I type into the terminal, where as I didn't on my old laptop.

I need to type:

sudo gedit filename.cpp  just to be able to open a gedit file that I have permission to save (didn't need that on my old machine)

sudo g++ -Wall -W -Werror filename.cpp -o FilenameCPP  to be able to compile (didn't need that either)

If this is something that can't be fixed, I certainly can deal with having to type an extra word in my terminal, but as it wasn't required on my old machine, I have to imagine there's a way for it to be fixed.

any insight would be greatly appreciated!

I'm very happy to have found this forum :)

---

### Post by Dave_L on 2014-02-28
In which directory is filename.cpp? You shouldn't need to use sudo to edit a file in your /home directory.

---

### Post by jacob23 on 2014-02-28
I created a directory to store all of my practice C++ files.  ~/CCPP

---

### Post by grahammechanical on 2014-02-28
I have been using Ubuntu since 7.04 and it has always required the use of sudo with certain commands. So, I do not understand why you say it was not required in an earlier version of Ubuntu.

Mind you, in the past some of us here were very quick to provide information about working around the need to prefix some commands with sudo. It was deemed dangerous to those users who lacked detailed information about Linux. So, we have been instructed to point users like you to

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you want to take the risk it is up to you.

Regards.

---

### Post by Dave_L on 2014-02-28
> **jacob23 said:**
> I created a directory to store all of my practice C++ files.  ~/CCPP

Is that directory and its contents owned by your normal user account?

```
stat ~/CCPP
ls -l  ~/CCPP
```

---

### Post by jacob23 on 2014-02-28
No no, not a previous version of ubuntu, simply my original laptop.

The machine changed, the OS did not.  That's why this is so puzzling to me.

---

### Post by jacob23 on 2014-02-28
yes, it is owned by my one and only user account

---

### Post by Dave_L on 2014-02-28
That's odd.  Are you able to access (create/read/write) files in the remainder of your home directory, without using sudo?

---

### Post by jacob23 on 2014-02-28
yes I am.  I don't know if this is a substantial detail, but in my GUI.. when I go into my home directory, the icon for /CCPP has a lock icon on it.

---

### Post by Dave_L on 2014-02-28
Can you post the output from these commands?
```
stat ~/CCPP
ls -al  ~/CCPP
```

---

### Post by jacob23 on 2014-02-28
```
 
stat ~/CCPP/CPP  (the actual directory is /CCPP/CPP

File: `/home/jaibhavaya/CCPP/CPP'  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d	Inode: 4195690     Links: 2
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2014-02-28 15:55:44.117401161 -0500
Modify: 2014-02-28 15:47:54.733418150 -0500
Change: 2014-02-28 15:47:54.733418150 -0500
 Birth: -



 
```


```
l -ls ~/CCPP/CPPtotal 60
 4 -rw-r--r-- 1 root root 1037 Feb 28 15:47 constpointer.cpp
 4 -rw-r--r-- 1 root root 1035 Feb 28 15:46 constpointer.cpp~
12 -rwxr-xr-x 1 root root 9325 Feb 28 15:47 ConstpointerCPP*
 4 -rw-r--r-- 1 root root  136 Feb 28 15:11 counter.cpp
 4 -rw-r--r-- 1 root root  135 Feb 28 15:10 counter.cpp~
12 -rwxr-xr-x 1 root root 9024 Feb 28 15:12 CounterCPP*
 4 -rw-r--r-- 1 root root   69 Feb 28 14:46 test.cpp
 4 -rw-r--r-- 1 root root   68 Feb 28 14:45 test.cpp~
12 -rwxr-xr-x 1 root root 8931 Feb 28 14:53 TestCPP*



```

---

### Post by Dave_L on 2014-02-28
The directory and its contents are own by root, not by your user account. To fix that:

```
sudo chown -R jaibhavaya:jaibhavaya /home/jaibhavaya/CCPP
```

Be careful with "chown -R".  Make sure you specify the correct path.

---

### Post by jacob23 on 2014-02-28
fixed!  thank you so much!

---

