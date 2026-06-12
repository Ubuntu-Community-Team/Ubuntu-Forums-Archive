---
title: "amaroK won't build collection"
date: 2006-11-06
forum: General Help
---

### Post by deleopario on 2006-11-06
Hi, I just installed Ubuntu and I'm trying to get amaroK to load my music, but even though I've told it to synch with my music folder, it won't build a collection. It will play my music if I load it manually. Also, sometimes it says something about not being able to communicate with klauncher.

---

### Post by adamkane on 2006-11-06
You need to install mysql or sqlite, and enable it in amarok.

Most people use sqlite. If you have a monster collection, and want to keep the data backed up, then go with mysql. I can get you up and running with mysql, if you need it.

---

### Post by deleopario on 2006-11-08
Well, I went and installed sqlite, and I at least have the mysql libs that are required by amaroK. After installing sqlite though it still did the same thing, and I think the problem is more severe than just the database. It seems to be getting worse, it constantly harrasses me about not being able to communicate with "klauncher," it can't even show my file structure when I try to change the collection settings or open a file manually, it takes forever to load, and for some strange reason, after running amaroK my quit button stops working and the only way I can shutdown or log-off is through the terminal (or possibly with a hotkey, but I don't know any of those for Linux).

Should I just go ahead and install KDE? It would be a waste of space for the most part since I have no interest in using KDE, but amaroK is one of the major reasons why I use Linux, so it would be worth it if I have to.

---

### Post by mahendra on 2006-11-09
Removing all my .ra / .rm files solved the problem for me !

---

### Post by koshari on 2006-11-10
there are known issues with scanning a library mounted from a samba/cifs share.

---

### Post by haaskaa on 2006-11-15
mahendra's solution also solved this exact problem for me. Amarok crashed when scanning my /home/music folder and left the Collection empty, but removing my *.rm files (luckily only had a few) solved the problem.

From the screenshots that people put up of the error message from Amarok always shows *.rm files being among the "problem" files.

---

### Post by adamkane on 2006-11-17
Not sure if this is still an issue, but you need at least taglib 1.4 installed.

---

