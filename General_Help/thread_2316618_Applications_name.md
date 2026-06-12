---
title: "Applications name"
date: 2016-03-09
forum: General Help
---

### Post by messiah2 on 2016-03-09
Where can I find application name for uninstall ?

---

### Post by slickymaster on 2016-03-09
Open Ubuntu Software Center, click the Installed button. All installed Apps will be shown in a categorized list. Select the one you wish to uninstall, and hit the Remove button.

---

### Post by messiah2 on 2016-03-09
Nop there is no applications on that list. I have installed applications by terminal.

---

### Post by howefield on 2016-03-09
Try searching your bash history - open a terminal and use the "up" arrow to find the command that you used to install.

Alternatively use Ctrl + r and start typing sudo apt-get ect, ect or simply open up ~./bash_history.

You'd probably also find some clues in /var/log/apt.

---

### Post by slickymaster on 2016-03-10
> **howefield said:**
> Try searching your bash history - open a terminal and use the "up" arrow to find the command that you used to install.

Alternatively use Ctrl + r and start typing sudo apt-get ect, ect or simply open up ~./bash_history.

You'd probably also find some clues in /var/log/apt.

This ^^

In **/var/log/apt** you'll find two log files **history.log** and **term.log**. Check thrm both

---

