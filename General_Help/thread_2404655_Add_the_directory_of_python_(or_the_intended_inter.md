---
title: "Add the directory of python (or the intended interpreter) to PATH"
date: 2018-10-26
forum: General Help
---

### Post by j.compean on 2018-10-26
Hello i am newbie, i have the next trouble, well i am working with the text editor ATOM because i am learning Python, i have installed the next package python-run-terminalnx, is a package for run the file .py in a terminal, but it does not work, it shows an error in the terminal, the main problem is that i need Add the directory of python (or the intended interpreter) to PATH (it is a prerequisite of the pack) and i don't know how do it, 

thanks for the help and i am sorry for my english but it is not my language.

---

### Post by Holger_Gehrke on 2018-10-26
If you're using the python interpreter that came with your Ubuntu, than you don't need to add anything to the PATH because it is installed in /usr/bin/ and that's in the path. To check enter 'python' in a terminal. If you get something like this
```

Python 2.7.15rc1 (default, Apr 15 2018, 21:51:34) 
[GCC 7.3.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```
than python is ready to use (hit ctrl-d or type 'quit()' to exit from the python interpreter). The problem has to be something else. If you showed us the error it gives you, we might be able to understand why it does not work.

Holger

---

### Post by dragonfly41 on 2018-10-26
In Atom I have experimented with these packages which in various styles offer shell terminals 
atom-shell-commands
platform-ide-terminal
process-palette
script

I do not use python-run-terminalnx

I just run the command python3 hello.py in the popup shell.

I like process-palette but you can use the command line to install these packages and try them

apm install <package>

---

### Post by j.compean on 2018-10-29
thanks for your replies, i have solved my problem modifying the file run_python_code.sh, in line 16 i wrote python3 instead of python and it works

---

