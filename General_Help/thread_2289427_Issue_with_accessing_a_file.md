---
title: "Issue with accessing a file"
date: 2015-08-04
forum: General Help
---

### Post by sagarddd on 2015-08-04
[COLOR=#505050][FONT=monospace]
Hi,

I would like to access below file to change some the parameters,
"~/.ipython/profile_pyspark/ipython_notebook_config.py"

however when i am trying to do so , it am getting below warning :

"[/FONT][/COLOR]bash: /home/hduser/.ipython/profile_pyspark/ipython_notebook_config.py: Permission denied"

Could you please help me to resolve this, I am new to Ubuntu, any pointer would be appreciated.

---

### Post by dino99 on 2015-08-04
that file is not owned by you, so use 'sudo' or 'gksu' to be able to make changes

---

