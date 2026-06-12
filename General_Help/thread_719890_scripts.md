---
title: "scripts"
date: 2008-03-09
forum: General Help
---

### Post by anv on 2008-03-09
I have *.sh ending scripts like the one which should install flash plugin or another which should launch one another software. After double clicking nothing happens and no ability to run in terminal. those execution rights is there, so it is not that. I think I accidently changed those files once to react differently, but I don't have a clue how to set them as they should be, like after double click it would ask:"..run in terminal?"

---

### Post by mc4man on 2008-03-09
I had that once and not knowing alot about scripts I just opened it with text editor and changed first line to  #!/bin/bash - and then it worked

---

### Post by forrestcupp on 2008-03-09
The way you make them executable is:
```
chmod +x /path/to/file/filename
```
Change '/path/to/file' to whatever the path is to that file, and change 'filename' to the actual filename.

Or the graphical way to do it is to find the file in Nautilus, right click the file and choose properties.   Then click the Permissions tab and check the box that says 'Allow executing the file as a program.'

Then, assuming the script actually works, you should be able to double click the file or run it from a terminal.

---

### Post by Oldsoldier2003 on 2008-03-09
> **mc4man said:**
> I had that once and not knowing alot about scripts I just opened it with text editor and changed first line to  #!/bin/bash - and then it worked
 
doing that ensures the shell knows where to find the interpreter... its standard coding practice

---

### Post by anv on 2008-03-10
no those steps I knew. something else, not file layer problem, more like operative system setting to handle those files?

---

### Post by justleen on 2008-03-10
if the file had execute permissions, you should get the popup asking you what to do with the file, run/display/run in terminal.

make sure the file has the right permissions

---

### Post by anv on 2008-03-10
both chmod and permission in thunar,rightclick, properties, permission granted. but even so scripts wont start.

---

### Post by justleen on 2008-03-10
is it something the shell can actually understand??

can you post the script?

---

### Post by anv on 2008-03-10
ok forexample this flash script: [http://home.comcast.net/~ubuntume/oldflash-0.1.5-1.tar.gz](http://home.comcast.net/~ubuntume/oldflash-0.1.5-1.tar.gz) , but as this as other scripts in my system now are more likely working and good work, but somehow my system wont give option to open these scripts in terminal, it opens them if those are normal programs like, Nexuiz(game), Blender(software), in those cases the command is working by double clicking, but it wont, as told before, give the terminal option in the beginning of software startup. and it is not a bug, I made some adjustment (accidently) of opening those certain files some months ago, and after that I haven't had need to run under terminal, exept now in this case with the flash plugin and one another software.

---

### Post by Muzer on 2008-03-10
Try running them from a terminal with ./script_name or sh script name

---

### Post by anv on 2008-03-10
that works

---

