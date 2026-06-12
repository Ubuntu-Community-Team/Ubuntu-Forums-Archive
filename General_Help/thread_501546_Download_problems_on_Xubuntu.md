---
title: "Download problems on Xubuntu"
date: 2007-07-15
forum: General Help
---

### Post by RedStar1916 on 2007-07-15
Okay, I installed Xubuntu Feisty Fawn 7.04 on my laptop and wanted to download some stuff through the add/remove programs thing. Some downloads, such as PyChess, downloaded and installed without a problem but when I tried to install some others, such as Tomboy Notes, I get a message asking me to insert "Xubuntu 7.04 _Feisty Fawn_ -Release i386 (20070415)" into drive /cdrom/. The only relevant CD I have is the CD I used to install Xubuntu, but when I insert that CD and click OK the message just comes straight back up again. The only reason I can think of is that I used the alternate install rather than the live install CD, but I really don't want to have to download the live CD ISO and reinstall the OS. Can anyone offer any advice?

---

### Post by rjfioravanti on 2007-07-15
can you do 
```

cat /etc/apt/sources.list

```
in a terminal?

It looks like it is looking for software from your CD, whereas you can get all software from the online repos

---

### Post by RedStar1916 on 2007-07-15
Yup got it, thanks! Just had to tell the system to ignore the line asking for the CD. Thanks for the help.

---

