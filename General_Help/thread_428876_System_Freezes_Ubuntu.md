---
title: "System Freezes Ubuntu"
date: 2007-04-30
forum: General Help
---

### Post by NakortValles on 2007-04-30
Hi guys, i installed ubuntu today on my computer, i am dual booting with windows vista. The problem is that when i run ubuntu, after about 5 min of viewing web pages or doing whatever the system freezes and i have to reboot my computer, it is not system overheating, and vista runs perfect. What could be the problem?

---

### Post by NakortValles on 2007-04-30
I went to errors in the system log, and everytime the computer crashed there was a message that said **creating missing directory "  /var/run/cups/certs  "**:confused:

---

### Post by bobbybobington on 2007-05-01
/var/run/cups  Sounds like it may have something to do with your printer.

---

### Post by jimbob on 2007-05-01
So go ahead and create that directory if it is not there, reboot  and see what happens.  Notice that it is owned by cupsys and is in the lpadmin group.
Here is mine:

  drwx--x--x  2 cupsys lpadmin  60 2007-05-01 17:22 certs
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jpatton on 2007-05-01
really? you mean the printer will cause the computer to freeze up? does that even sound logical?

---

