---
title: "Help with Adding custom launcher to Ubuntu unity sidebar"
date: 2013-02-15
forum: General Help
---

### Post by Dodeca on 2013-02-15
Hello all ...

I have used this web page ...
---
[http://www.youtube.com/watch?v=ncWUFEc3WXY](http://www.youtube.com/watch?v=ncWUFEc3WXY)
---

and this process ...

---
gksudo gedit /usr/share/applications/name.desktop

paste into gedit :

[Desktop Entry]
Name=the name you want shown
Comment=
Exec=command to run
Icon=icon name
Terminal=false
Type=Application
StartupNotify=true

and save file.
---

But the process fails if the exec path contains a SPACE ( ascii 32 ) in the line

...

any help on getting the exec path to work when the command line is ...

/home/user/.wine/drive_c/Program Files/anyprogram.exe

thx

---

### Post by Steeperton on 2013-02-15
Precede the space with "\", thus:

/home/user/.wine/drive_c/Program\ Files/anyprogram.exe

---

### Post by Dodeca on 2013-02-15
> **Steeperton said:**
> Precede the space with "\", thus:

/home/user/.wine/drive_c/Program\ Files/anyprogram.exe


Well .. thanks ... it seems right ... yet fails .... and the path IS CORRECT ... now what?

below is a cut-n-paste of the error message.

Details: Failed to execute child process "/home/user/.wine/drive_c/Program Files/Microsoft Visual Studio/VB98/vb6.exe" (No such file or directory)

---

### Post by deadflowr on 2013-02-15
First off, running a command needs to execute a program, so try adding 
```
wine /path-to-file
```

Secondly, there is no need to use root, as you can throw the desktop file in your home directory in the home/user/.local/share/applications folder. It'll be easier to manipulate and fix as you can just open gedit and fix without needing to run as root.

---

### Post by Dodeca on 2013-02-15
> **deadflowr said:**
> First off, running a command needs to execute a program, so try adding 
```
wine /path-to-file
```Secondly, there is no need to use root, as you can throw the desktop file in your home directory in the home/user/.local/share/applications folder. It'll be easier to manipulate and fix as you can just open gedit and fix without needing to run as root.


Thanks ... adding wine to the beginning of the line works!

---

### Post by deadflowr on 2013-02-15
Good to see.

For further information, because the Exec command is a command that can executed in the terminal, I always try running the command first in a terminal, so if any problems arise I can quickly figure it out.

It's good practice, so I can see if the path is right or the command needs adjustments.

---

