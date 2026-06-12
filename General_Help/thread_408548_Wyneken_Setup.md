---
title: "Wyneken Setup"
date: 2007-04-13
forum: General Help
---

### Post by Afkpuz on 2007-04-13
I recently installed Wyneken and went through the First time user setup.  However, when I get to the end and click apply, nothing happens.  I cannot actually get into the program itself.  Any ideas?

---

### Post by karl1 on 2007-04-17
This has happened on Ubuntu a few times. Here's the quote I put together for the Website:

"On clicking Apply at the end of the first run wizard, it becomes unresponsive and needs to be quit with Cancel. The terminal output indicates that ~/wyneken/config is not accessible and a directory listing states that the directory is owned by root....Trying it again still has the same error until I deleted the ~/wyneken directory."

So, if you simply remove your ~/wyneken directory and try again, you should be in good shape. If not, run Wyneken from the command line, and then send me all of the stuff that it spits out up to the point where you're getting stuck.

Regards,
Karl J. Abbott
Wyneken Developer

---

### Post by Afkpuz on 2007-04-18
It seems that Wyneken will only run when excecuted as root.  How can I set permission so it can be run by anyone?

*Edit* Forget this last post.  It seems that only the initial setup must be run in root.  The program itself runs fine now.

---

