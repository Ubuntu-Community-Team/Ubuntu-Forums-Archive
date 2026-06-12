---
title: "Can't find how to configure the Geany compiler"
date: 2017-01-20
forum: General Help
---

### Post by ronjjjg8885 on 2017-01-20
Hi

I'm trying to set the Geany editor to work with Python 3 but can't find "Build>Set
Build Commands" buttons. I need it to start learning Python. I've both Python 2 and 3 installed.

I've tried to find these buttons but seems something is different in my version compared to how it should look.

This is how to should look: (see the image by scrolling)
[https://wiki.geany.org/howtos/configurebuildmenu](https://wiki.geany.org/howtos/configurebuildmenu)

It doesn't allow me to upload another image... so I can't show you a screenshot of the problem.

---

### Post by TheFu on 2017-01-20
Python isn't compiled or "built" - it is a scripting language.  So I don't really understand what you expect.
I'm running 1.27 - pulled up a python script here and had the option to change those options.

Wild guess here - are you running on Linux storage? Sometimes using non-Linux storage doesn't work for software development.

---

### Post by The Cog on 2017-01-20
As TheFu says, you don't compile python - just run it.
For python2, the execute command is```
 python "%f"
``` and for python3 it is ```
python3 "%f"
```.

---

### Post by oldfred on 2017-01-20
What version of Ubuntu & Geany?

In 16.04 with Geany 1.27 in Build at bottom "Set Build Commands" are commands to set which version of python to use.

Mine is, not sure now it that is new default as old versions you had to modify a config file to change version of python to use:
python3 "%f"

Then you can run python3 from within geany.

---

### Post by ronjjjg8885 on 2017-01-21
Sorry if i wasn't clear...
I've a book for Python... "Python Crash Course".
It says i need to tell Geany which engine to use.. i need it to be verstion 3 of python.

but the problem is that there is no such button in my geany that give the options and settings of geany.

i've the latest ubuntu and geany (they were downloaded yesterday)

---

### Post by Olav on 2017-01-21
Open a .py file in Geany.
Go to the **Build** menu, choose **Set Build Commands**.
In the dialog that appears, edit the command after the **Execute** button to read **python3 "%f"** instead of **python "%f"**. Click **OK**.
Now you can run your Python 3 program from within Geany by pressing F5 or clicking the toolbar button or whatever.

Notice that Geany is quite intelligent/adaptive about this. For instance if you open a .c file the Set Build Commands dialog would give you the options to compile, make, run a C program. If no file is open in the editor, the build commands remain empty.

---

### Post by ronjjjg8885 on 2017-01-21
thank you
that was helpful for me

i thought i should see a designated button and not a drop down one...

---

