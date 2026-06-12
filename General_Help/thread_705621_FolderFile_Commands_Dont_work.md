---
title: "Folder/File Commands Dont work"
date: 2008-02-23
forum: General Help
---

### Post by chris.tkd on 2008-02-23
Hello, I have a question about every command i run which opens/creates a file.

An example is this if i want to edit the sources.list file,

i type in the terminal sudo gedit /ect/apt/sources.list

and a blank sources.list file opens. I suspect this is being created.

If i paste the exact same command from a website sudo gedit /ect/apt/sources.list, it opens the sources.list up for editing.

Another example of this is:
if i want to create a new file, sudo vi /ect/synergy.conf  --> A new DIRECTORY has been created.
if i paste this command from the website --> a new FILE has been created.

This is a problem i had in 7.04 aswell as 7.10(which im running now). Im typing the commands exactly as they are shown on the website. The only things i can think may be causing this is either its some werid font im using (which i havent changed from the default) or my KVM is some how affecting it. 

Any thoughts?

---

### Post by taurus on 2008-02-23
Check your spelling.  It's /**[COLOR="Blue"]etc[/COLOR]**, not /ect.  And besides, you should use gksudo when you want to use gedit text editing.

```
gksudo gedit /etc/apt/sources.list
```

---

