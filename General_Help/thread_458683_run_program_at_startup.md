---
title: "run program at startup"
date: 2007-05-29
forum: General Help
---

### Post by okos on 2007-05-29
I installed dellfand on my dell laptop to stop overheating.

The command line to run dellfand is:
dellfand 1 7 40 44 49

1 no verbos
7 checks temp every 7 seconds
40c fan off
44c fan low
49c fan high

How do I run this at startup?

---

### Post by blackened on 2007-05-29
System -> Preferences -> Sessions

On the "Startup Programs" tab, press the "New" button on the right side of the dialog.

Give it a name in the "Name" box and insert your command into the "Command" box.

---

### Post by cmost on 2007-05-29
You can also create a little script and then run it whenever you log into your Gnome session.  To do this, simply fire up gedit and add the following lines:

code:
#!/bin/bash
dellfand 1 7 40 44 49

Save the file as dellfan
right-click the file and select properties
click the permissions tab
tick the box next to 'allow executing file as program'

Next, go to System -> Preferences -> Sessions
Click the tab for startup programs
Click 'new' or 'add'
Write 'dellfan' for the name
Write /path/to/dellfan for the command

Enjoy!

---

### Post by okos on 2007-05-30
> **cmost said:**
> 

Save the file as dellfan
right-click the file and select properties
click the permissions tab
tick the box next to 'allow executing file as program'
!

I right clicked the file and under permissions I do not have a box to allow executing file.

I only have owner, group, permissions, and special flags- set userid,goupid and sticky.

How do you allow executing file as program?

---

### Post by hellmet on 2007-05-30
How does one add programs to startup via CLI?

---

### Post by blackened on 2007-06-03
> **hellmet said:**
> How does one add programs to startup via CLI?

[http://ubuntuforums.org/showthread.php?t=462195]("http://ubuntuforums.org/showthread.php?t=462195")

The video linked in post #3 is especially informative.

---

