---
title: "Emergency!! need to add a crontab task"
date: 2005-08-25
forum: General Help
---

### Post by nortoncillo on 2005-08-25
i need to ejecute a command each 1 min.  with root privilegies..
can anyone show me how!

---

### Post by nad on 2005-08-25
From a root terminal, type the command: crontab -e  to edit the superusers crontab.

Add the line: 0-59  *  *  *  *  /path/command_you_wish_to_run .

Don't forget to put a blank liine at the end. man crontab , man crontab -e 5 .

---

