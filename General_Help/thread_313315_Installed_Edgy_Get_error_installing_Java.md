---
title: "Installed Edgy Get error installing Java"
date: 2006-12-05
forum: General Help
---

### Post by Derspankster on 2006-12-05
I just did a fresh install of Edgy (not upgrade). I used Automatix to install a variety of things but Java install failed. I also tried to install Java using Add/Remove and I get the following error. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I have no idea what that means - help!

---

### Post by groggyboy on 2006-12-05
try typing "sudo dpkg --configure -a" in a terminal.

this error occurs because you need to agree to a disclaimer, which is terminal-based.  this happens whenever you try to install java via a graphical application.

---

### Post by Derspankster on 2006-12-05
RESOLVED - Thank you very much for your quick reply. I learn something new every day. I installed Java manually when I configured Dapper. Thanks again.

---

