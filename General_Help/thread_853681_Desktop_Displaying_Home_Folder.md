---
title: "Desktop Displaying Home Folder"
date: 2008-07-08
forum: General Help
---

### Post by Nimaran on 2008-07-08
Somehow I accidentally changed a setting that makes my home folder my desktop. I don't want it that way, I want a separate desktop folder and home folder, how do I switch this back? Running Hardy... if that helps.

Thank you in advance.

---

### Post by iaculallad on 2008-07-08
Press Alt+F2, input "gconf-editor" (w/o quotes), and browse through Apps->Nautilus->Preferences. There should be an option named "desktop_is_home_dir", uncheck it.

---

### Post by Nimaran on 2008-07-09
It was unchecked, so I rechecked it logged out, logged in, unchecked it, logged out, logged in, no difference. Now, I did have a program installed called gtweakui, I had played with it a while ago, and I think that is when the problem started. I uninstalled it but to no avail...

---

### Post by Nimaran on 2008-07-10
bump

---

### Post by iaculallad on 2008-07-10
A fix for Home Folder being displayed on Desktop:

```
gedit ~/.config/user-dirs.dirs 
```

Find the string and **XDG_DESKTOP_DIR=""**  and replace it with **XDG_DESKTOP_DIR="$HOME/Desktop"**

Save and Close the file. Press Alt+F2 to access "Run Application" window, input "gconf-editor" (w/o quotations) and navigate to Apps->Nautilus->Preferences->desktop_is_home_dir setting. CHECK then UNCHECK the "Value".

Apps->Nautilus->Preferences->show_desktop should be CHECK.

---

### Post by Nimaran on 2008-07-11
Thank you very much, it worked like a charm. Not sure how it got that way, but back to my good old desktop. Thank you again.

---

