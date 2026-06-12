---
title: "python.  cant run code ?"
date: 2013-09-12
forum: General Help
---

### Post by pretty_whistle on 2013-09-12
I've installed python 2.7.4 shell but all I can do with it is type in code and debug it.  How do I run it?

I hope I'm using the correct terminology here but I want to run a program I've written code for.  This "shell" cant do it so how do I do it?  Is there something else I need to install?  I'm lost.....

---

### Post by btindie on 2013-09-12
Create a file test.py with
```

#!/usr/bin/env python

print "Hello World"

```

type "chmod +x test.py" to make the file executable

then type "./test.py" to run the python script.

The hash-bang (#!) line at the top tells the shell what to use to execute the script with.

If you've installed python from the repositories then that will work. If not, you'll have to modify that line to point it to the correct python binary.

---

### Post by pretty_whistle on 2013-09-12
I tried that.  It says no such file or directory.  Also as an fyi, I did install [COLOR=#000000]python from the repositories.[/COLOR]

---

### Post by The Cog on 2013-09-12
Is test.py in your current directory? This command should show it:
```
ls -l test.py
```


Also, be aware that linux is case sensitive - test.py and Test.py are different files.

---

### Post by pretty_whistle on 2013-09-12
It still says no such file or directory.

---

### Post by The Cog on 2013-09-12
Then the either the file you are trying to run is in a different directory, or has a different name. So some questions:
1: What is the name of the file you want to run?
2: What directory is it in?
3: How are you trying to run it?

---

### Post by pretty_whistle on 2013-09-12
> **The Cog said:**
> Then the either the file you are trying to run is in a different directory, or has a different name. So some questions:
1: What is the name of the file you want to run?
2: What directory is it in?
3: How are you trying to run it?

The file name is test.py.

I have it sitting on my desktop.

How am I trying to run it?  I dont know how to run it, thats the problem I posted about.

---

### Post by zacktu on 2013-09-12
As an alternative to making the source file executable you can 
1) Be certain you're in the same directory as your Python program, say *test.py*
2) Type *python test.py*

You can also start Python by typing *python* in the command line.

---

### Post by The Cog on 2013-09-13
To run the file, you need to open a terminal - a command prompt window. In Ubuntu, you probably have to F2 and enter the command **gnome-terminal**. This puts you into a command prompt in your home directory.

If your python file is sitting on your desktop, then it is in a directory called **Desktop** immediately under your home directory. So you can refer to the file as Desktop/test.py like this:
[B][FONT=Courier New]ls -l Desktop/test.py
python Desktop.py[/FONT][/B]
but I suggest that you change your command prompt's "current directory", into your Desktop directory with the command
**[FONT=Courier New]cd Desktop[/FONT]**
Then you can run the file simply by typing the command
**[FONT=Courier New]python test.py[/FONT]**

You can make the file executable in its own right if you like, by doing two things. 
Firstly, make the **first** line of the file point to the interpreter that can run the file for you. For a python file, the first line should look like this:
```
#! /usr/bin/python
```
Secondly, you have to mark the file as executable. This is a property of the file and can be set with the command
**[FONT=Courier New]chmod +x test.py[/FONT]**
or can be set by editing the file properties in your file manager GUI. Once the file is executable, it can be run simply by entering the name of the file in a command prompt or script. From the command prompt, use the command
**[FONT=Courier New]./test.py[/FONT]**
You always need the "./" (meaning "this directory") in front if the file is in your current directory because the command prompt doesn't automatically search your current directory for executable programs.

Hope this helps.

---

