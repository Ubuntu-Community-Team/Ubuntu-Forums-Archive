---
title: "New to Linux"
date: 2021-12-20
forum: General Help
---

### Post by russrspencer on 2021-12-20
Hello, just getting my feet wet with Linux so I am not well versed in it at all.  I installed a program called atbswp and only way I have to launch it is to use the following command in the terminal:

python3 atbswp/atbswp.py

I was wondering if there is a way to create a shortcut on my desktop to execute this command/script when I need it, instead of having to type in the command in terminal every time.

Thank You!

---

### Post by ActionParsnip on 2021-12-20
Is the full path to the folder:
```

/home/username/atbswp

```

If so, then you can make a .desktop launcher as below:

```

[Desktop Entry]
Version=1.0
Name=ProgramName
Comment=This is my comment
Exec=python3 /home/username/atbswp/atbswp.py
Icon=/path/to/someicon.svg
Path=/home/username/atbswp
Terminal=false
Type=Application
Categories=Utility;Application;


```

Obviously change "username" to your actual username. Set an actual icon too (Hopefully one exists in /home/username/atbswp somewhere).

Should do it. If you test the file as OK then you can copy it to /usr/share/applications and it'll show when you search applications

---

