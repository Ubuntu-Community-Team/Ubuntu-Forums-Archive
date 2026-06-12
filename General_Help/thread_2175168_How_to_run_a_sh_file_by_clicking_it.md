---
title: "How to run a sh file by clicking it?"
date: 2013-09-17
forum: General Help
---

### Post by hamiltino on 2013-09-17
hi there,

I have already put chmod 777 and chmod +x on it but it still opens to gedit and doesnt run.

Can anyone tell me what to do.

My sh file:

```

#!/bin/bash
#Open reaper program

cd "/home/developer/reaper/.wine/drive_c/Program Files (x86)/REAPER"

./reaper.exe




```

---

### Post by Dennis N on 2013-09-17
You have a Windows program, and the command to run it requires wine. Something similar to:

wine "c:\program files\cribbage\CRIB.EXE"

which is an example from my machine. Use quotes around the path if there are spaces in it.

---

### Post by hamiltino on 2013-09-17
> **Dennis N said:**
> You have a Windows program, and the command to run it requires wine. Something similar to:

wine "c:\program files\cribbage\CRIB.EXE"

which is an example from my machine. Use quotes around the path if there are spaces in it.

yeah either script works the same. Even using your method, my sh file still opens to gedit and doesnt run the program.

---

### Post by whitesmith on 2013-09-17
Yes, the line would have to start with wine. The double-click issue is solved by:
 
Right clicking on the file in Nautilus
Open With
Open With other application
Use a custom command
Browse
Select "gnome-terminal" in /usr/bin/
Add
Close

That should do it. This is from memory and an earlier Ubuntu version.

---

### Post by Dennis N on 2013-09-17
Your command ./reaper.exe will only work for a Linux program which this is not. The command itself must start wine, which in turn loads the Windows program from somewhere in its C:\ directory. The C:\ directory is mapped to **~/.wine/drive_c** on your Linux system. Also be sure to use \ and not / in the Windows path.

---

### Post by hamiltino on 2013-09-17
> **whitesmith said:**
> Yes, the line would have to start with wine. The double-click issue is solved by:
 
Right clicking on the file in Nautilus
Open With
Open With other application
Use a custom command
Browse
Select "gnome-terminal" in /usr/bin/
Add
Close

That should do it. This is from memory and an earlier Ubuntu version.

Hi there,

I followed what you said but i can't find the the use custom command option. I've got related applications, other application, find applications online. (Using ubuntu 13.04)

---

### Post by whitesmith on 2013-09-17
I think my instructions go too far back. Try this. Make a directory called /home/bin. All executables (including scripts) really belong there, anyway. Now get /home/bin into your path. Put your script there. Logout and back in. This procedure should work on any version.

---

### Post by Dennis N on 2013-09-17
The path probably should be **/home/<username>/bin**

---

### Post by stinkeye on 2013-09-17
Do other scripts run when clicked?
Have you set the executable text file behaviour in nautilus preferences?
Clicking in the dash will always open in gedit no matter the nautilus setting.
You would need to create a .desktop file for the dash.

---

### Post by Dennis N on 2013-09-18
> **hamiltino said:**
> yeah either script works the same. Even using your method, my sh file still opens to gedit and doesnt run the program.

You should post your command (using wine) so we can have a look at it and maybe see why it fails.

But,

You really don't need a script or even the terminal to start Windows programs installed by Wine. In Ubuntu, you can search for the Windows program name in the Dash and click on it. The Wine desktop will open with your program. In Xubuntu or Lubuntu, Wine with all programs you installed with Wine can be accessed from the main menu under the Wine category.

---

### Post by hamiltino on 2013-09-18
> **stinkeye said:**
> Do other scripts run when clicked?
Have you set the executable text file behaviour in nautilus preferences?
Clicking in the dash will always open in gedit no matter the nautilus setting.
You would need to create a .desktop file for the dash.

aha!

Thank you! changing the text file preferences did the trick.

:P

---

