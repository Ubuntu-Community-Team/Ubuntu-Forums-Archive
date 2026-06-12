---
title: "Shell scripting doubt"
date: 2008-05-11
forum: General Help
---

### Post by 7raTEYdCql on 2008-05-11
I had a doubt in shell scripting and thought that i'd ask here.

What does "./" do actually when present in a script.

I have used it a couple of times and havent actually found what it acrually does.

---

### Post by geraldm on 2008-05-11
It is a path specification, which means "start looking for this file in the current directory"

Gerald

---

### Post by Zorael on 2008-05-11
When you normally enter a command, it doesn't look for executables in your current dir, but rather in the paths referred to in the PATH variable.
```
zorael@sunspire:~$ env | grep PATH
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
Much like a double dot means *your previous directory*, a single dot means *your current directory*.

So if you run [FONT="Courier New"]./lala[/FONT], you're executing the [FONT="Courier New"]lala[/FONT] file that's in your current dir.
And if you run [FONT="Courier New"]../lala[/FONT], you're running the [FONT="Courier New"]lala[/FONT] file that's in your previous dir.

---

### Post by gug@fnal.gov on 2008-05-11
do you mean './myscript.sh' for example? If so, then it is telling the interpreter to use the version of myscript.sh found in the directory specified by './'. This can be important in an environment where there are multiple versions of a program installed on the operating system. Also, as a security measure it is dangerous to have "./" in your PATH (the PATH is an ordered listing of directories for the interpreter to look in for the program you request). Consider the case of python. If you just type 'python' at the command line, the interpreter will likely find it in /usr/bin and call /usr/bin/python (try the 'which' or 'type' commands and see 'type python'). Now maybe I need to rebuild python for a special project. Now there are two versions of python that can be used. If I am sitting where the new python executable is located and type 'python', the /usr/bin/python will be used and not the local python. But $PWD/python or ./python however will get me what I want.

---

