---
title: "Can't use terminal"
date: 2012-11-02
forum: General Help
---

### Post by Dhelms on 2012-11-02
I am running Ubuntu 12.04. If I open a terminal session I do not have a cursor, nor does it show my pwd. it is basically useless. I am set up as an administrator in my user account. I suspect that is a permissions issue but I am not sure how it happened. Also in my settings rather than the icons I have a circle with a slash. Anyone have any ideas?

---

### Post by ibjsb4 on 2012-11-02
Go to console and enter:

sudo apt-get purge gnome-terminal && sudo apt-get install gnome-terminal

[http://www.ubuntugeek.com/how-to-switch-to-console-mode-from-gui-mode-in-gnome.html](http://www.ubuntugeek.com/how-to-switch-to-console-mode-from-gui-mode-in-gnome.html)

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by Dhelms on 2012-11-02
Thanks, I will give it a try.

---

### Post by angry_johnnie on 2012-11-02
If you can use the terminal as another user, you may also try deleting your .bashrc file.  It is in your home directory.

---

### Post by Dhelms on 2012-11-03
reinstalling the terminal didn't do it.

---

### Post by Dhelms on 2012-11-03
[ibjsb4]("http://ubuntuforums.org/member.php?u=1729120"), I was unable to run the command you suggested from the console, however it would run from another user terminal, so I installed the Guake terminal and can run it from my user account, now maybe I can figure out what is going on without switching between accounts, thanks.

---

### Post by ibjsb4 on 2012-11-03
> **Dhelms said:**
> reinstalling the terminal didn't do it.


Try opening gnome-terminal with Guake.

sudo gnome-terminal

Get any errors?

Edit:  make that just

gnome-terminal

No sudo

---

