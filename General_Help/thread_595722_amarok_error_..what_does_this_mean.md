---
title: "amarok error ..what does this mean??"
date: 2007-10-29
forum: General Help
---

### Post by thousandpimps on 2007-10-29
i installed amarok from synaptic and when i opened it it gave me a error saying "there was an error setting up inter-process communications for KDE. The message returned by the system was: could not open network socket please check that the "dcopserver" program is running!

the the next dialog box appears saying

will not save configuration and more stuff ...

any suggestions./??

---

### Post by scrivener on 2007-10-30
I had the same problem with KMyMoney and other KDE apps.  I fixed it by deleting the files in my home folder that start with .dcopserver.  There were two of them.  They were hidden so you'll have to use the show hidden files option in Nautilus.  (I didn't delete them right away, I moved them to another folder first, then deleted them when I had verified that everything was okay.)

As an FYI, I found out that the .docpserver file was the problem by running kmymoney from the command line and reading the output after the program crashed.

---

