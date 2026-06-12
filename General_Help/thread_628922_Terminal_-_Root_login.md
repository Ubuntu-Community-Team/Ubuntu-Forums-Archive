---
title: "Terminal - Root login"
date: 2007-12-01
forum: General Help
---

### Post by money2themax on 2007-12-01
ok i found out how to get to a file that will allow me to login as root if i can change it but the problem is i can't change it without being in root now i've gotten as far as getting to the folder that the file is it [btw the file path is /etc/gdm and the file is gdm.conf the line is allowroot=false] i need to know how to change that lilne of text in that file to read allowroot=true can you guys help me?

---

### Post by merlinus on 2007-12-01
You can try this from a terminal:

gksudo gedit /etc/gdm/gdm.conf

---

### Post by money2themax on 2007-12-01
thank you very much also what are some good books on learning terminal of ubuntu 7.10?

---

### Post by WarMonkey on 2007-12-01
I don't know any books, but you can use this site:

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

