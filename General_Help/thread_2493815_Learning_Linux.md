---
title: "Learning Linux"
date: 2023-12-26
forum: General Help
---

### Post by daniell59 on 2023-12-26
I would appreciate it if somebody could recommend how I can learn Linux. I don 't plan a career. More like a hobby. And perhaps one day, I can be of help to members on this forum who have been so generous with their time.

---

### Post by Rubi1200 on 2023-12-26
I am slightly confused. You joined in 2008 and have over 1,000 posts.

To me, asking how can I learn Linux is like asking how can I learn history.

Well, it depends on where you want to start..

From the beginning, from a certain time period? You get the analogy I hope.

Most experienced users here recommend starting with learning how to use the command line.

This is the place to start:
[https://linuxcommand.org/tlcl.php](https://linuxcommand.org/tlcl.php)

Download the PDF and work through it at your own pace.

Enjoy!

---

### Post by MAFoElffen on 2023-12-26
Please explain(?) More Information Needed.

---

### Post by dragonfly41 on 2023-12-26
[Perhaps start here from a historical perspective]("https://web.archive.org/web/20230000000000*/linux")

---

### Post by daniell59 on 2023-12-26
I still know very little. For example, I cannot understand anything when I look at the logs.

---

### Post by dragonfly41 on 2023-12-26
Who does?  I treat them as hieroglyphics and use text analytics tools such as [petit]("https://crunchtools.com/software/petit/").

---

### Post by dragonfly41 on 2023-12-27
Further tips learned

Install log editor glogg and search for keywords.

Also to compare log files use meld in command line mode to compare two log files looking for differences. 

I happen to use Krusader and you can diff log files located  in each of the dual panels. Similar dual panel editors include Midnight Commander, Tux Commander, Dual Commander.
i created a user action in Krusader to meld two files (such as two time separated log files).

meld %lCurrent% %rCurrent%  

A mix of these methods should allow you to master log files forensics.

glogg is easy to use.

---

### Post by ActionParsnip on 2023-12-27
Did you use Windows before Ubuntu? If so....how did you learn that?

---

### Post by MAFoElffen on 2023-12-27
Or... Just begin to learn what the Linux system log files are, what is logged where, and how those relate (now) with journalctl in SystemD... For me, I do better if I understand how it works, and what it uses. Once I understand that, then what to look for when something is wrong. Then what the different log files track. Different log files, track different things. 

That is a lot more productive that wandering around log files blindly, not understanding what you are looking at, or where to find what, right?

Here is a good start with that: 
[https://linuxhandbook.com/syslog-guide/](https://linuxhandbook.com/syslog-guide/)

---

