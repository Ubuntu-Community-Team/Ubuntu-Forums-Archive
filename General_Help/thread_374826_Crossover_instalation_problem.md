---
title: "Crossover instalation problem"
date: 2007-03-03
forum: General Help
---

### Post by rabidrabbit on 2007-03-03
When i try to install the deb package for crossover i get a message saying there is a conflict with a previously installed package crossover-pro. I never installed it though. I looked through my packages, orphaned ones everything i could think of. After the failed installation i went and deleted the crossover folder in /opt and /usr/share but it still won't work.

---

### Post by Gerard Barberi on 2007-03-03
Go to your home folder and press "control + h" to see hidden files.

Look for .cxoffice folder.  This is the Fake drive and config directory.

But you if you never installed it, I don't know why it would be there.

---

### Post by darkmaster on 2007-03-03
> **rabidrabbit said:**
> When i try to install the deb package for crossover i get a message saying there is a conflict with a previously installed package crossover-pro. I never installed it though. I looked through my packages, orphaned ones everything i could think of. After the failed installation i went and deleted the crossover folder in /opt and /usr/share but it still won't work.

I once had a similar problem. Don't download the .deb file, download instead the generic executable installation file, valid for any distro. Open a terminal in the folder where you downloaded the file and run it with

sh nameoffile.extension

nameoffile is the name of the file and extension is, of course, the file extension :) I don't remember if it is a .run or a .sh
Don't use sudo! Just use the normal sh command, otherwise it will complain for the folder not being yours. Good luck! 

[The Darkmaster]("http://thedarkmaster.wordpress.com")

---

### Post by rabidrabbit on 2007-03-03
thanks the normal linux installer worked fine, it was a .sh btw. Why wouldn't the .deb have worked though? that kinda peeves me...

---

### Post by darkmaster on 2007-03-03
> **rabidrabbit said:**
> thanks the normal linux installer worked fine, it was a .sh btw. Why wouldn't the .deb have worked though? that kinda peeves me...

Sorry, I really don't know. Maybe it has been packes badly, dunno... Aniway, I'm glad that the sh worked fine :)  :D

---

