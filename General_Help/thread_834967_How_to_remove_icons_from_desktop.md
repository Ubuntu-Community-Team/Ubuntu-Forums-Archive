---
title: "How to remove icons from desktop"
date: 2008-06-20
forum: General Help
---

### Post by HandsofGod on 2008-06-20
I installed Ubuntu 8.04 with a separate /home partition, once it's done, everything is fine but all folders in my /home appear in desktop too. These folders are not shortcuts, when i tried to delete one, this folder was actually deleted from my /home!. Could anyone please tell me how can i remove these folders from my desktop, since i want just a clean desktop. By the way, the Places (left panel) in nautilus is abnormal too, there's no "panu" (my user) folder there. Help me..

---

### Post by iaculallad on 2008-06-20
Press Alt+F2 and input "gconf-editor" (w/o quote) and press Enter.
Navigate to apps->nautilus->desktop and try to uncheck the checked values on the right pane of the Configuration Editor window.

---

### Post by ad_267 on 2008-06-20
You might need to edit the file ~/.config/user-dirs.dirs and change this line here:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

Edit: From someone elses post:
> Ok, now I'm at home, so I found it:

Go to Applications->System Tools->Configuration Editor

Go to apps, then nautilus, and click on the preferences folder.

Scroll down on the right side until you see the desktop_is_home_dir key and uncheck the box. (Make sure to make a Desktop folder in your home directory before you do this so Nautilus doesn't complain.)

Enjoy.

---

### Post by HandsofGod on 2008-06-20
Thank you very much man, it's fixed!!

---

