---
title: "Where to set LD_LIBRARY_PATH"
date: 2005-04-16
forum: General Help
---

### Post by mrmaple on 2005-04-16
Hi, I'm trying to set up my environment with a path to some debug libraries that I don't want to completely install.  I've got a two day old Hoary.  I am not using a shell, so .bash_profile and .bashrc aren't working.  I'm opening up an editor (IDE) and trying to run some python from there, but I need the LD_LIBRARY_PATH to point to my fresh wxPython wxWidgets libraries.

the command is:
  export LD_LIBRARY_PATH=/opt/wx/2.5/lib

I've tried putting it in:    result

  /etc/environment         not set in a shell or my editor
  /etc/profile                   "
  /etc/X11/gdm/PostLogin/Default  no effect
  ~/.xsession                 X cannot start
  
Could anyone help me please?  
-Jim

---

### Post by soul_rebel on 2005-04-16
try ~/.bashrc

---

### Post by mrmaple on 2005-04-16
Thanks!  that did it.
-Jim

---

### Post by mrmaple on 2005-04-23
Oops... .bashrc worked for running the python script from my text editor, but I still can't run my python script by opening it from Nautilus.  I need the environment variables to be set for my entire X session, even when bash is not involved.

Where can I set LD_LIBRARY_PATH so that I can run python scripts from Nautilus?

Thanks again,
-Jim

---

### Post by tread on 2005-04-23
Try /etc/bash.bashrc ?

---

### Post by soce_32 on 2005-04-23
Try ~/.login

---

