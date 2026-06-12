---
title: "Gaim and security"
date: 2006-12-17
forum: General Help
---

### Post by rudlavibizon on 2006-12-17
I just did a system reinstall and copied backed-up  .gaim folder to the my freshly installed home folder. I was curios to find out it's contents and opened accounts.xml only to find my login password for gmail account written plainly. Now I'm certainly not an expert on this but from my point of view this looks like a serious security flaw. 
Am I right on this or am i being too paranoid?

---

### Post by tkjacobsen on 2006-12-18
I think it is a BIG security issue. I filed a bug. Maybe if more people points the flaw out, they'll correct it...

Anyway the file is only readable to the user and any user who can use sudo... So if you are the only administrator it shouldn't be a big problem.

---

### Post by tkjacobsen on 2006-12-18
This is what thay think about the subject:

[http://gaim.sourceforge.net/plaintextpasswords.php](http://gaim.sourceforge.net/plaintextpasswords.php)

---

