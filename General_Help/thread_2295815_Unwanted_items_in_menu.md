---
title: "Unwanted items in menu"
date: 2015-09-21
forum: General Help
---

### Post by philo565 on 2015-09-21
Although I am not new to Linux until recently I had been using Ubuntu 12.04

I upgraded to 15.04 and am very happy ...it works faster and smoother than ever...but I have one problem I cannot solve.

I uninstalled some unneeded wine-apps but they remain in the menu, If I go to "activities"..."show application" all the icons are still there for the non-existent applications.

I spent some time on Google and about the only thing I saw was to use "Main Menu" and uncheck or delete the unwanted items. 

I did that...logged out and back in...even rebooted but the items remain. 

Could someone please tell me how to get rid of them? I have no problem using the command line if necessary.

Thanks

---

### Post by deadflowr on 2015-09-21
Removing apps will remove the apps, but not clear out whatever files are stored in the user's home folder.
You might look to see if those wine apps are inside a folder called ~/.local/share/applications.
(it is hidden in the files program, but you can set it to show hidden files by pressing ctrl + h)
This is your own folder so you can simply delete any item you don't want that might be in there (no sudo required)
See if that helps.

---

### Post by philo565 on 2015-09-21
That did the trick!   Thanks for the fast and /correct/ answer!!!

I looked all over and gave up.


Really appreciate the help.

---

