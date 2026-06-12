---
title: "Diagnostics with ubuntu vs solaris"
date: 2006-10-24
forum: General Help
---

### Post by thrust on 2006-10-24
i work for sun microsystems technical support, and with solaris there is a number of diagnostic commands that i can run to indicate hardware failure (ex: iostat -En, prtdiag -v, /var/adm/messages (file) etc.) i already know the substitute for /var/adm/messages(file) which is var/log/messages. but does anybody know a linux eqivilant to these commands. your response will be greatly appriciated

---

### Post by mssever on 2006-10-25
I've never used Solaris before, so I don't know those commands. If you tell me what they do, maybe I can help.

I use lshw and lspci for hardware info and /var/log/* which you already know about (there are a whole bunch of useful logfiles in there).

---

### Post by thrust on 2006-10-25
well the iostat -En 

basically shows all the drives on the systems (hard disks, CD/DVDrom drives) and if they have errors on them.

the prtdiag -v

shows all the mainboard devices on the system and the status of each

---

### Post by mssever on 2006-10-25
```
sudo lshw | less
```lists all kinds on information about the system devices, but it doesn't give diagnostic info. Anybody else know of a way to do this in Linux? It'd be really handy.

Actually, I wonder how difficult it would be to port those programs to Linux from OpenSolaris.

---

