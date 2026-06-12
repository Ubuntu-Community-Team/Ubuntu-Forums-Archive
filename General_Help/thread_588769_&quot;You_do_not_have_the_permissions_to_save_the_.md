---
title: "&quot;You do not have the permissions to save the file&quot;"
date: 2007-10-23
forum: General Help
---

### Post by ScrewdriverClock on 2007-10-23
Hello, I am new to Ubuntu, and I enjoy it so far, but  I have a few problems. I figured out how to fix my tablet configuration, but when i go to edit it, i get this:
[IMG]http://i175.photobucket.com/albums/w126/WiiLock/Screenshot-2.png[/IMG]
I can't figure out how to gain a higher access than admin, I really need my tablet to work. Could anyone help? My aim is ScrewdriverClock, and any assistance would be nice.

---

### Post by kebes on 2007-10-23
To edit a system file (like "/etc/X11/xorg.conf") you need to use administrator privilege. On the commandline, you would do this by using the "sudo" command, like:
```
cd /etc/X11/
sudo nano xorg.conf
```
You will be asked for your password, and then the file will be opened in a simple text editor.

If you want to do it the GUI way, you would type this (either in a terminal or in the "Run..." dialog that you can open by pressing ALT+F2):
```
gksudo gedit /etc/X11/xorg.conf
```
Again, you will have to enter your password to confirm that you have administrator access.


As a general rule, you can put "gksudo" in front of any program name to open that program in "admin mode."

Hope that helps.

---

### Post by Tekno_Cowboy on 2007-10-23
1. Open a terminal
2. Type: sudo gedit /etc/X11/xorg.conf
3. Modify your file
4. Save your file
5. Do a victory dance :guitar:

---

### Post by Maestro23 on 2007-10-23
Need admine privileges with gedit. Open the file with the following commands.

> gksudo gedit ...

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kebes on 2007-10-23
> **Tekno_Cowboy said:**
> 1. Open a terminal
2. Type: sudo gedit /etc/X11/xorg.conf
3. Modify your file
4. Save your file
5. Do a victory dance :guitar:

By the way, you should use "gksudo" not "sudo" if you are opening a graphical program. (Using sudo can mess up the ownership/permissions of various graphical-environment settings/files that get updated.)

---

### Post by ScrewdriverClock on 2007-10-23
Thanks you guys, this was quite a bit of help :D

---

### Post by por100pre1 on 2007-10-23
It is a good idea to backup a system file before editing it:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

