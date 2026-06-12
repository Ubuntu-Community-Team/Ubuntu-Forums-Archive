---
title: "Make commdnd line into luanch icon"
date: 2007-04-22
forum: General Help
---

### Post by beachreader on 2007-04-22
does anyone know how to make a commend line :
wine ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe

inot a luanch icon or something woth out having to remember that long command line. 
many thinks!

---

### Post by sdide on 2007-04-22
edit your ~/.bashrc (assuming you use bash)
and add the line:
alias winstuff='wine ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe'

now you should be able to - when openening a new shell - do just do 
~$ winstuff

or you can write into  the file ~/bin/winstuff

#!/bin/sh
wine ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe

and then just do 
~$ winstuff
assuming ~/bin is in your path. (echo $PATH to check)

regards

---

### Post by adam_kimber on 2007-04-22
To make any program or executable into a launch icon just do the following: 

1a) If you want the launcher on the Desktop, right click then click  "Create Launcher"

1b) If you want the launcher on a Panel, right click blank part of panel and click "Add to Panel", then click "Custom Application Launcher" at top of page. 

2) Fill in the Command section with your command, as below with the double quotes after wine

```
wine "~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe"
```

3) Fiii in name, click the no icon and select an icon    

Double click the launcher if on desktop or single click in on panel

---

### Post by Weevil on 2007-04-22
I have a similar question about **dgen**, with which one can open .smd files. I can create a launcher using the commandline **dgen /folder/file.smd**.

What I would like is an icon onto which I can drop .smd files to open them with **dgen**. Does anyone know whether this is possible? I am using the **Xubuntu** xfce desktop btw.

---

### Post by Weevil on 2007-04-24
I've found the answer to my previous post; the trick is to create a launcher icon with the commando;

**dgen /folder-of-my-segaroms/%n**

where %n automatically is replaced with the file I drop onto the launcher icon!

---

