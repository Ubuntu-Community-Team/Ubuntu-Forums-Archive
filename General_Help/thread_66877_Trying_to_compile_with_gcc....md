---
title: "Trying to compile with gcc..."
date: 2005-09-18
forum: General Help
---

### Post by martinimnetz on 2005-09-18
Hello everybody,

this is my first posting! I'm new to Linux, having finally installed Ubuntu as the second OS on my machine. I was planning on that for quite a while, so here I am. I searched this forum extensively, came across a number of threads dealing with compilation problems, but didn't find any of those of help for my problem.

I got myself gcc (I can't remember if it was via Synaptic or apt-get). Synaptic lists gcc, gcc-3.3, gcc-3.3-base, gcc-3.4-base, gcc-4.0-base and libgcc1 as installed. Then I tried to compile, but it seems I didn't get the syntax right. On a mate's advice, I tried to cd to the folder where the files I want to compile are located and typed "./configure". However, that only netted me an error message. Following the advice given in one of the threads here, I used apt-get to get build-essential. Then I tried "./configure" again, but all I got translates like this "./configure: File or folder not found." (I'm using the German language version of Ubuntu/Gnome).

Can anybody advise me what to do? Thank you!
Glad being part of this community,
Cheers,
Martin

---

### Post by professor_chaos on 2005-09-18
Glad to have you a part of the communtiy.
Although I am unsure of an answer to your question, I would suggest you might ask this in the programming section of the forum, as you might grab the eyes of users knowledgable in this area.

---

### Post by taimo on 2005-09-19
The problem seems to be not in gcc, but configure... looks like the binary file "configure" just isn't there in the directory where you are. Type: ls -l
... and you can see.

---

### Post by DeadEyes on 2005-09-19
There are a few things to try
If there is a Make.in file
```

# ./configure
# make all

```
If there is an imake file try
```

# xmkmf -a
# make all

```
and If there is a make file try
```

# make all

```

but first look for an install or readme file.

And now a warning I've messed up my system loads of times by firing off commands out of frustration trying to get things to work, so think twice before hitting enter.

---

### Post by martinimnetz on 2005-09-20
Thanks guys for your help! I'll try posting in another forum later, but it's a great idea.

For now, I wasn't aware that "./configure" requires a file named 'configure' in the directory. I assumed that this is a system command that does its job in the current directory. But fair enough. There is no file named 'configure', no file 'make.in', no 'imake'. But there is a 'makefile'. However, I will also remember the advice to be careful and think twice, so I'll first doublecheck that the c++ source code may be compiled for Linux.

Cheers,
Martin

---

