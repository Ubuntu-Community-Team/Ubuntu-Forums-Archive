---
title: "how run a python program by clicking its icon?"
date: 2008-03-21
forum: General Help
---

### Post by jto on 2008-03-21
I'm new to Ubuntu, and I'd like to run a Python program by clicking its icon, as I did in Windows XL.

The program is just hello.py, which contains one line: print "hello".

When I double click the icon and then click run, nothing happens.

When I right click on it and select open with python, nothing happens.

When I right click it and select properties and then the tab  open with, I can't select python as the application with which to open hello.py.

Finally, when I  right click it and select properties and then permissions, I can't change the execute box to allow executing. It changes from a minus sign to a check sign but then automatically changes back again.

Thanks in advance for your help.

PS. The same thing happens when I try to run a more complex program, which opens a GUI using Tkinter. The programs work from the command line, but not by clicking the icon.

---

### Post by sajro on 2008-03-21
make the icon link to: ```
gnome-terminal -e python hello.py
```

I think that'll work. Can't test, though...using Arch with urxvt not Gnome-Terminal.

---

### Post by jto on 2008-03-21
Thanks for the prompt reply. I'm not sure I get how this works. When hello.py is on the hard disk and I right click on hello.py and then click Make link, that creates an icon called Link to hello.py, I don't see how to insert the code. (I tried selecting Make link on an icon on a usb key and found that the operation is not permitted, which seems reasonable, since the key's probably not always going to be  inserted).

And when I entered the code on the command line in the directory in which the program is located, I got the error message: Invalid argument "hello.py".

---

### Post by dcroxton on 2008-03-21
Open Nautilus and navigate to your script.  Right click, select "Properties," and choose the "Open with" tab.  Select custom command, and type in "/usr/bin/python."  It (and other .py files) should open in Python thereafter.

You can also make it always run in Python by adding the following line to the top of your script:

```
#!/usr/bin/python
```

I don't know if that will cause the GUI to work properly or not.

Sincerely,
Derek

---

### Post by jto on 2008-03-21
That did it! It worked both for the simple program and the python/tkinter one.

Thanks so much for such a prompt and helpful reply.

---

### Post by forrestcupp on 2008-03-21
> **dcroxton said:**
> Open Nautilus and navigate to your script.  Right click, select "Properties," and choose the "Open with" tab.  Select custom command, and type in "/usr/bin/python."  It (and other .py files) should open in Python thereafter.

You can also make it always run in Python by adding the following line to the top of your script:

```
#!/usr/bin/python
```

I don't know if that will cause the GUI to work properly or not.

Sincerely,
Derek

The custom command thing will do the trick.

About the #!/usr/bin/python part, this is important but you still need to make it executable.  Any file you want to just double click and run needs to be made executable first.  In a terminal, change to the directory where the python file is and type:
```
chmod +x filename.py
```
substituting the real filename.

But the nautilus thing will work even if the file isn't set to be executable.

---

### Post by jto on 2008-03-21
Thanks so much. It did work with the gui.

---

