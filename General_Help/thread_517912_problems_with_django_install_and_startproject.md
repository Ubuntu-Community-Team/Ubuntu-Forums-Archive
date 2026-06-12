---
title: "problems with django install and startproject"
date: 2007-08-05
forum: General Help
---

### Post by goneskiing on 2007-08-05
I cannot seem to get a django project created.  I installed python2.5 via synaptic.  I then installed django 0.96 by downloading the tar file, extracting in /usr/local and then running sudo python setup.py install.  This correctly (I think) created the django files in the site-packages folder under python2.5.

If I type python - I see it's python2.5.  if i import django and run django.VERSION,  I get the correct django version.  I then created a symlink "sudo ln -s /usr/lib/pthon2.5/site-packages/django/bin/django-admin.py  /usr/local/bin/django-admin.py"  The symlink appears okay.  

But when I go to a home directory and try to run >>> django-admin.py startproject myproject , I keep getting syntax errors  - any help ?

---

### Post by goneskiing on 2007-08-06
I got this running with the help of the django google group list.  It appears some execute permissions are messed up with the Ubuntu package (as well as the same files in multiple folders).  Version 0.96 is available for Feisty in the backports repository.    Easiest way to get "startproject" to run is to run it at the command line without the ".py" extension.

---

