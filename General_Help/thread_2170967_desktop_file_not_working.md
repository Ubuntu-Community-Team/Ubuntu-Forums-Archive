---
title: "desktop file not working"
date: 2013-08-28
forum: General Help
---

### Post by 3wais on 2013-08-28
I have created this desktop file for a commercial program.
```
[Desktop Entry]
Name=modelsim
Comment=ModelSim Simulation
Exec=vsim
Icon=/usr/share/applications/ModelSim.ico
Terminal=false
Type=Application
Encoding=UTF-8
Categories=Developer;
```

but it does not work. I tried changing the Exec= field to another command and it works fine. 
vsim is an executable in $PATH. Is this the reason why the file is not working properly? how should I fix it?

---

### Post by deadflowr on 2013-08-28
Do you know the whole path to the command?
Something like /usr/bin/vsim.

And is it a command line program or does it have a graphical interface?
If command line, then you'll need to mark the terminal= as true.

---

