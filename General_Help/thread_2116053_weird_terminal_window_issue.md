---
title: "weird terminal window issue"
date: 2013-02-14
forum: General Help
---

### Post by LinuxFanBoi on 2013-02-14
After a clean install of 12.04 32 bit desktop,  I press ctrl+alt+T to open a terminal window.  the window opens but the prompt doesnt appear unless I ^C...  

any ideas?

---

### Post by cjhabs on 2013-02-14
There is likely something in one of your login files that is accessing an unavailable resource - check ~/.bash*

---

### Post by LinuxFanBoi on 2013-02-14
okay... took a look at ~/.bashrc

No idea what I'm looking for though

---

