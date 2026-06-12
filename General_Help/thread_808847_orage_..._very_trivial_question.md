---
title: "orage ... very trivial question"
date: 2008-05-26
forum: General Help
---

### Post by Yaymeq on 2008-05-26
Hello, I've only just moved from windows to xubuntu and it came with a nifty little calendar called orage. The thing is, whenever I restart, the calendar AND the preferences windows both pop up. I've checked through the preferences and nothing there will help me, I've checked my auto started aps and it's not there, I've also turned off Auto saving sessions. I uninstall/reinstalled it a few times. Anyone got any thing that will help?

Thanks
~Yaymeq

---

### Post by pvincent on 2008-08-27
Hi, I think you have saved your session previously with these two windows opened.
I had the same trouble.
Basically, from the terminal, I ran : 
  **pgrep orage -l**
in order to detect if some hidden orage program still running
if so, 
  **pkill -9 orage**

---

