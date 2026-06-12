---
title: "&quot;You have mail' at terminal"
date: 2007-05-07
forum: General Help
---

### Post by Underpants on 2007-05-07
When I login via ssh, i see "You have mail" 

How do I check that?

---

### Post by hal8000 on 2007-05-07
You would normally type "mail" with the quotes then list. You will see a number of messages, type the number to read the mail, d to delete, h back for mail headers and q for quit.

---

### Post by Underpants on 2007-05-07
> **hal8000 said:**
> You would normally type "mail" with the quotes then list. You will see a number of messages, type the number to read the mail, d to delete, h back for mail headers and q for quit.


Cool. I'm getting it figured out. It's stuff from cron jobs. Is there any way to check that mail in a GUI application?

---

### Post by sandman55 on 2007-05-07
try typing startx

---

### Post by bashologist on 2007-05-07
gedit /var/mail/$USER

---

### Post by Underpants on 2007-05-07
Umm. I meant like reading it in evolution or mozilla..

---

### Post by bashologist on 2007-05-07
> **Underpants said:**
> Umm. I meant like reading it in evolution or mozilla..
Hehe. How about this then? n_n
firefox /var/mail/$USER

---

