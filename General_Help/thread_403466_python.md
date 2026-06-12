---
title: "python"
date: 2007-04-07
forum: General Help
---

### Post by ali780 on 2007-04-07
Hello every body
How can I write my program in python in a file and implement it?
thank you

---

### Post by raja on 2007-04-07
Use any text editor, write your program, then run it python.
For example, if this is hello.py```
#says hello!
print "Hello"
```
Then from the terminal, ```
python hello.py
``` will do it.

---

### Post by ali780 on 2007-04-07
thank you

---

### Post by alkat on 2007-04-07
> **ali780 said:**
> Hello every body
How can I write my program in python in a file and implement it?
thank you


I'm not sure I understand what you're asking, but if you want to know how to run a python script/program, you just need to write the script with a good text editor (Gedit could do) save it with the extension .py and run it from the terminal with the command:

$ python script_name.py

You could also specify in the header of the file that it is a python script, in that case you don't need to call the interpreter - something like this should work:

```

#! /bin/python
#

your script here

```

I think you could also just assign execute rights to the file and then double click on it to run it. I've never tried it, though.

$ chmod a+x script_name.py

---

### Post by ali780 on 2007-04-07
Yes it is true. Thanks

---

