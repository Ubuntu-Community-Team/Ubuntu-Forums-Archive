---
title: "How to copy multiple files with the shell"
date: 2007-04-02
forum: General Help
---

### Post by gammaknife on 2007-04-02
Hi there! My question isn't ubuntu-specific. 
I'm trying more and more to do everything I can with the shell, but there is one problem  I still cannot deal with. I can't find any way to copy multiple files *contained* in a folder and moving them to a different directory WITHOUT moving the original directory they were in. 

I hope someone can help me do that!

Also I'm wondering if there are some good bash guides for beginners. I've found some on  LDP but the info there was a little too "scattered" to be of much use.

Thanks in advance, 
gammaknife

---

### Post by stephan0h on 2007-04-02
How about this:

cp youroldfolder/* yournewfolder

regs,
stephan

---

### Post by coxy on 2007-04-02
You could try:

> 
cp -r /dir/tobecopied /dir/whereyouwantyourdata


the -r switch completes the command recursively, which should include all sub directorys and files.

[http://www.ss64.com/bash/index.html](http://www.ss64.com/bash/index.html) gives some basic information on the bash commands but nothing to in depth.

---

### Post by gammaknife on 2007-04-02
Working fine thx!

Before I made it work by making small changes to directory names, it said something like "omitting" directory... I'm wondering why that appeared

---

### Post by gammaknife on 2007-04-02
> **coxy said:**
> You could try:



the -r switch completes the command recursively, which should include all sub directorys and files.

[http://www.ss64.com/bash/index.html](http://www.ss64.com/bash/index.html) gives some basic information on the bash commands but nothing to in depth.

Won't the recursive option also include the original directory name? (Wondering about the meaning of "recursive" in computer sciences...)

---

### Post by coxy on 2007-04-03
Sorry, I mis-read. You should be able to cd into the directory and issue the command. You would have to use -r if there were sub-directorys within the folder. If not then just use:

```

cp * /destination/folder

```

---

### Post by buckeyered80 on 2008-03-01
I'm a little late on this reply, but thanks for the advice.  It worked for me too.

---

