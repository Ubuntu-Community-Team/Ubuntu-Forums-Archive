---
title: "apt-get error"
date: 2007-04-02
forum: General Help
---

### Post by KWierso on 2007-04-02
I was trying to add a repository to the sources.list file. I typed in the additional lines, but the text editor didn't allow me to save the changes. So I closed the editor.

Now, whenever I try to use Synaptic or apt-get, it prints out the following error:

E: Malformed line 34 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory

In sources.list, this is line 34:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty


What do I need to do to get apt-get to work again?

---

### Post by bruenig on 2007-04-02
If you are not actually using feisty, do not add feisty repositories. It will break your system. With that said, you need to actually put something after the "feisty" for it to work.

So something like
```
deb http://archive.ubuntu.com/ubuntu/ feisty main
```
for the main repository. Or you can put universe, multiverse, or restricted.

---

### Post by KWierso on 2007-04-02
Thanks for the tip. I added 'main' to the end of that line, and it now works, although fails to load that repository. But at least I can run synaptic again. :)

---

### Post by ayoli on 2007-04-02
the line should be :
```
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
```
or:
```
deb http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse
```

btw, the editor won't let you save the file while editing it as user you should run your editor as root with gksudo ike that:
```
gksudo gedit /etc/apt/sources.list
```

---

