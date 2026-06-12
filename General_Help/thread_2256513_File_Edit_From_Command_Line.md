---
title: "File Edit From Command Line"
date: 2014-12-13
forum: General Help
---

### Post by rbscairns on 2014-12-13
I made a change (obviously wrong) in my 50-ubunutu.conf file (Ubuntu 14.04) and upon rebooting I cannot log in using the normal log-in screen. I used Ctrl+Alt+F1 to log in to the command line. Now I need to edit my /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf file.

I tried

```
sudo gedit  /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
```

however as the 50-ubuntu.conf file is faulty, that does not work.

How do I edit my 50-ubuntu.conf file using the command line (no GUI available)?

---

### Post by CantankRus on 2014-12-13
[COLOR="#FF0000"]**Edit:**[/COLOR] you added to your post. Just use the nano command in a tty(ctrl+alt+F1) if that's easier.
Prefix with **sudo** though as you wont be in a root shell.
-----------------------

Boot up in recovery mode and select the "drop to root shell" option.
The file system is in read only mode so need to mount as read/write.
```
mount -o remount,rw /
```

Use nano to edit your file....
```
nano /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
```
ctrl+o then Enter to save changes.
ctl+x to exit.

Type in "exit" to exit root shell and return to menu where you can resume normal boot.

---

### Post by rbscairns on 2014-12-13
Thank you CantankRus. All is now well. I have edited my 50-ubuntu.conf file back to its original state and all is working.

---

