---
title: "Problems installing Nicotine+ from source"
date: 2008-05-12
forum: General Help
---

### Post by ChildOfMana on 2008-05-12
Apologies if this thread is in the wrong place - wasn't sure where to put it!!

I'm trying to install Nicotine+ from source (not because I need to - I know it's in the repositories - but just because I want to have a go at installing something from source).

I've extraced the tar.gz to ~/ and read the INSTALL.txt inside the directory. The instructions state:

> To install nicotine+ from the source tree run: python setup.py install --prefix=<dir>

However, when I type this into the Terminal (using either ~/ or ~/nicotine+-1.2.9 as the <dir>) I get the following error message:

> bash: syntax error near unexpected token `newline'

What is going wrong? I know it'll be something really obvious but I'm very new at this (but always willing to dive in at the deep end!).

Oh, I should probably point out I'm using 8.04 (32bit) and I have the gcc compiler package installed.

Thanks.

---

### Post by ChildOfMana on 2008-05-13
Anybody? :confused:

---

### Post by seanhogge on 2008-05-13
Since it's a bash error, my first guess would be the directory you're specifying.

Try specifying the full path of a directory, and don't use special characters.  Create yourself a special testing directory wouldn't hurt, too.

$ python setup.py install --prefix=/home/[username]/nicotine

It's a first step, at least.

---

### Post by ChildOfMana on 2008-05-14
Duh - I was enclosing the directory in < >

Told you it'd be something obvious! Thanks.

Tried it your way and it worked but now I have another problem. According to the INSTALL.txt file, to get the program up and running I have to type:

> python ./nicotine  from the source tree (which I assume is the directory to which I installed it?)

However, I get the following error message:

> python: can't open file './nicotine': [Errno 2] No such file or directory

which is fairly self-explanatory... but why does the file not exist?

---

