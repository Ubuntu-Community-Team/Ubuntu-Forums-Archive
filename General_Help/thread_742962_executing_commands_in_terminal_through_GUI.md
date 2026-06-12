---
title: "executing commands in terminal through GUI"
date: 2008-04-02
forum: General Help
---

### Post by divparth on 2008-04-02
i have made GUI using PYGTK.....the GUI has 2 buttons---'SUBMIT' and 'BACK'. and a text area where i have written a command...say--'ls'....and other text area for displaying output.

what  want is ...on clicking the 'SUBMIT' button, the command 'ls' should automatically get executed on the terminal and the output should get displayed in the text area of my GUI...................

Is this possible?????  if not, then is there any work around..........

plzzz help:KS

---

### Post by luisromangz on 2008-04-02
I would use the popen function, read this:

[http://docs.python.org/lib/os-newstreams.html#os-newstreams](http://docs.python.org/lib/os-newstreams.html#os-newstreams)

---

### Post by gsmanners on 2008-04-02
If you have connected the "clicked" signal to your function/method, then all it needs to do is something like:

os.system("ls > temp-file")

Then read the temp file into the text area. This is all a lot simpler if you install devhelp and the proper python manuals.

---

### Post by luisromangz on 2008-04-02
Using os.system, and reading the output from an auxiliary file is a bit hackish. Fisrtly it is not necessary, and it also have problems such as "where do i put that file so I have permissions?", "have I to delete the file when the program is done?" , etc.

---

### Post by divparth on 2008-04-04
thnx 4 t help!!!!

---

