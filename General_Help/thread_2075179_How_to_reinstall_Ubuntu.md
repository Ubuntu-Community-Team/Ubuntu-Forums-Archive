---
title: "How to reinstall Ubuntu"
date: 2012-10-23
forum: General Help
---

### Post by StevenHodges92 on 2012-10-23
I'm having SO many issues installing wine so I just want to uninstall Ubuntu, and then reinstall it.  When I boot my computer up, I have Windows as well, so I can uninstall Ubuntu, go into windows and then install it from windows.

But how do I go about uninstalling Ubuntu?

---

### Post by dino99 on 2012-10-23
[HTML]But how do I go about uninstalling Ubuntu?[/HTML]

all depend how and where it is installed. Usually it is installed on its own partition, so start a formating tool to see where it is installed, then format that partition. But if it is installed via wubi inside windows, then it is installed inside a windows folder like a program; again erase that folder to uninstalled ubuntu (dirty way) or use the "uninstall" windows command.

here is how i do ubuntu (linux) installation:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

note: the "alternative" iso is dropped now on recent release (12.10), so its replaced by the feature "select something else" or so, which mean "manual" installation.

about installing wine, thats easy, open a terminal to run:
```
sudo apt-get install wine1.5
```
it will create a hidden .wine folder (ctrl+h to unhide it)

---

### Post by Ace..... on 2012-10-23
> **StevenHodges92 said:**
> I'm having SO many issues installing wine so I just want to uninstall Ubuntu, and then reinstall it.  When I boot my computer up, I have Windows as well, so I can uninstall Ubuntu, go into windows and then install it from windows.

But how do I go about uninstalling Ubuntu?

Try this method - it's a step by step guide.

[FONT=Comic Sans MS][SIZE=1][I][[COLOR=Blue]_Re-install Ubuntu keeping your data & settings_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2057342") "re-install rather than fix"

[/I][/SIZE][/FONT]It also contains links to the key info docs on boot back up and yannbuntu's doc on the subject.[FONT=Comic Sans MS][SIZE=1][/SIZE][/FONT]

---

