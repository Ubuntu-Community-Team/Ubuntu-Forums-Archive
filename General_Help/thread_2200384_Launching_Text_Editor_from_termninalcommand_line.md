---
title: "Launching Text Editor from termninal/command line"
date: 2014-01-19
forum: General Help
---

### Post by t.williams.im on 2014-01-19
Hello,

I have learned that you can launch an application by typing its name intothe command line.

However, when I try this with Text Editor, the error message says that Text is not a command. How do I resolve this?

Also, how do you delete/uninstall an application from the command line or otherwise?

Thanks,

Tim

---

### Post by QIII on 2014-01-19
Hello!

I assume you are typing 

```
text editor
```

or similar.

The application you see called "Text Editor" is gedit.  You can start it by doing

```
gedit
```

---

### Post by steeldriver on 2014-01-19
You can also invoke it as 

```
gnome-text-editor
```

which points to the current default GUI editor, based on the update-alternatives system (so for example that should still work even if you have installed a different default GUI editor)

```

$ update-alternatives --list gnome-text-editor
/usr/bin/gedit
/usr/bin/leafpad

```

---

### Post by oldos2er on 2014-01-19
> **t.williams.im said:**
> Also, how do you delete/uninstall an application from the command line or otherwise?


```
sudo apt-get remove <package name>
``` 

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

[https://help.ubuntu.com/12.04/serverguide/apt-get.html](https://help.ubuntu.com/12.04/serverguide/apt-get.html)

---

### Post by ibjsb4 on 2014-01-19
Apt-get is first choice, but at times dpkg is needed.

[http://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php](http://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php)

---

### Post by deadflowr on 2014-01-19
Once in a while I use the xdg-open command, which will open whatever application is the default for whatever file I want to look at.
```
xdg-open filenamehere
```

---

