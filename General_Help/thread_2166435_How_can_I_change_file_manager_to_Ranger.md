---
title: "How can I change file manager to Ranger?"
date: 2013-08-09
forum: General Help
---

### Post by mQYrEfH on 2013-08-09
I used exo-preferred-applications and typed in ranger for the file manager but when I try to open a directory with it I get an I/O error. I came to realize this was because it is a terminal applications. I can use any GUI application just fine. I assume that I need to open a terminal then run ranger inside it for it to work. How can I get ranger to work like nautilus and other GUI file managers?

---

### Post by mQYrEfH on 2013-08-09
bump?

---

### Post by bapoumba on 2013-08-09
Please wait 24h before bumping your thread : [http://ubuntuforums.org/showthread.php?t=2158945](http://ubuntuforums.org/showthread.php?t=2158945)

[http://ranger.nongnu.org/documentation.html](http://ranger.nongnu.org/documentation.html)
Looks it has curses interface, will work from the terminal.

---

### Post by mQYrEfH on 2013-08-09
How do I automatically open a terminal and run it? Again I want to use it as my default file manager. For example, if I click "Open containing folder" in my web browser I want it to open a terminal with Ranger running inside on that folder.

---

### Post by mQYrEfH on 2013-08-09
Alright, I randomly figured out the solution: gnome-terminal --tab -e 'ranger "%s"'

---

### Post by bapoumba on 2013-08-10
Thanks for posting the solution. I'll mark your thread as solved as I am here. For future threads > Thread Tools > Mark this thread as solved :)

---

