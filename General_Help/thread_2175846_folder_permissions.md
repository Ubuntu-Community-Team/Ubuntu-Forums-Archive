---
title: "folder permissions"
date: 2013-09-21
forum: General Help
---

### Post by refishman567 on 2013-09-21
dear sirs
I have a folder I created and now want to delete it, the problem is it has root permissions and won't let me delete it how can I delete this folder and contents, it is using about 13 gb and I want the space back:(

---

### Post by deadflowr on 2013-09-21
It would seem you created with sudo, so remove it with sudo.
Or change ownership.
Either
```
sudo rm -rf folder-name-here
```
or
```
sudo chown -R you:you folder-name-here
```

It would be important to note that you should use the full path of the folder, so as to not accidentally cause confusion and delete the wrong part.

Added, if making yourself a folder or file, no need to use sudo command.

---

### Post by ibjsb4 on 2013-09-21
You can also use the GUI way.  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
gksudo nautilus
```

This will open Nautilus file manager in "sudo" mode.  You can then navagiate to your file and delete it.  You can also change owner of a file by right clicking on it and going to properies.

---

### Post by Impavidus on 2013-09-21
Changing ownership of the directory you want to delete doesn't help you deleting it. For deleting you need write permission on the parent directory. **sudo rm -r <path>** is the way to go if you're sure you want to delete all contents of that directory.

---

