---
title: "how do you get a desktop app to run multiple commands in the terminal?"
date: 2016-04-12
forum: General Help
---

### Post by lamda0shotgun on 2016-04-12
I want it to run 3 commands in series, but have no idea how to do it!

---

### Post by deadflowr on 2016-04-12
Does
```
first-command && second-command && third-command
```
work for you?

---

### Post by lamda0shotgun on 2016-04-12
No! And I don't think it is the commands, as I tested it with some random ones. 

Here it is anyway:

```
[Desktop Entry]
Version=1
Name=LOIC
Exec=cd /home/terran/Downloads/LOICf && mdtool build && mono LOICf.exe 
Type=Application
Terminal=true
Icon=/home/terran/Pictures/loicicon.png
```

---

### Post by lamda0shotgun on 2016-04-12
Haha!" sh -c " before the commands and with the command series ins speech marks worked!

---

