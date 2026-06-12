---
title: "Root Files App Name in 19.10"
date: 2020-04-03
forum: General Help
---

### Post by bionic3epl on 2020-04-03
I'm using 18.04.4 LTS. What's the Name of the Files App in 19.10 that will allow changes to be made in the root files?

---

### Post by TheFu on 2020-04-03
**sudoedit** is the program you should use to carefully modify system files.  
Always, make a backup of every file BEFORE you modify it.  if something bad happens, be ready to put things back.

For more about sudoedit, there is a manpage.  Any editor can be used with sudoedit. The manpage explains how.

There are a few system files that have their own editing programs which also validate the file is correct.  visudo and crontab -e.  sudoedit is for all others.

---

### Post by bionic3epl on 2020-04-03
Is that the one in 19.10?

---

### Post by grahammechanical on 2020-04-03
Excuse me, but what do you mean by root files?

Do you mean system files? What do you want to do and to what do you want to do it? There may be a GUI application that will let you do what you want. And as far as I can remember the Files app is still called Files in 19.10 and 20.04. Its developer name is nautilus. Do you want to launch nautilus with root permissions?

Regards.

---

### Post by TheFu on 2020-04-03
> **bionic3epl said:**
> Is that the one in 19.10?

**sudoedit** is part of the sudo package which is the same on all releases.  it is THE safest way to edit system files, period.
i don't know what a "root file" is.  Not a term used.

---

### Post by vanadium on 2020-04-04
A build-in supported way in standard Ubuntu to perform operations with root permissions, is using the admin:// URL.

To open the file manager in the root folder "/": ```
nautilus admin:///
```

To open a system file, e.g. /etc/fstab, as root: ```
gedit admin:///etc/fstab
```

You can issue these commands from the terminal or from the Alt+F2 run dialog.

---

### Post by deadflowr on 2020-04-04
To get the right click *open as administrator* option (as well as the *edit as administrator* option),
install the package nautilus-admin
```
sudo apt install nautilus-admin
```
requires reloading nautilus to take affect.

---

