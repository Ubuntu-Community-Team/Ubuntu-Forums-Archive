---
title: "How do i write to /etc/ ?"
date: 2006-10-30
forum: General Help
---

### Post by Melhisedek on 2006-10-30
Hi there folks, well fooling around and would like to write/copy things to /etc or /usr or /bin. 
So far I've tried with sudo and even with sudo -i to give me root access, but no go :/ 

Any ideas on what I'm doing wrong or perhaps is such writing disabled in Ubuntu?

---

### Post by Arby on 2006-10-30
that's slightly odd. What commands are you trying to run, show an example? sudo should give you write access to system directories. So for example some thing like ```
sudo cp myfile /etc/X11
``` Should allow you to copy a file to /etc/X11. If it isn't then something unusual is happening. Show us what you are trying to run.

---

### Post by steve.horsley on 2006-10-30
Arby is right - a copy of the commands you tried adn the results would be useful.

Note that only the first user, the one whose name was given to the installer, is allowed to use sudo. If you want to give others that right, you have to make them members of the **admin** group, but only the first user can do that because only the first user can use sudo.

---

### Post by bsussman on 2006-10-30
/etc is a system directory with standards for what belongs.

You are free to put whatever wherever but if what you want to put there doesn't belong, there can be unintended consequences someday.

---

