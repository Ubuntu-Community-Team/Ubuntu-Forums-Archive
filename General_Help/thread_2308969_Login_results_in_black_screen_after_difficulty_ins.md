---
title: "Login results in black screen after difficulty installing virtualenv+virtualenvwrappe"
date: 2016-01-06
forum: General Help
---

### Post by alex488 on 2016-01-06
I was attempting to install virtualenv and virtualenvwrapper and I came up against some problems. I am currently in the guest account. I can CTRL+ALT+F1 into the account in which the problem occurred - i.e. enter text mode. I think the last thing I was trying to do was run a script called virtualenvwrapper.sh and the system says there is a problem running the initialization hooks. The details of this are on my tty1 on the other account which I can switch to via this account. If I could copy and paste the details here it would help but I'm not sure how to....

---

### Post by sergio53 on 2016-01-07
Ok I don't get your problem completelly.
try changing desktops or tty's by CRT+ALT+F1.. CRT+ALT+F2.. CRT+ALT+F7.. F7 is normally GUI that might help.
try to use sudo before the script 
check if the script is executable by using $ chmod + x virtualwrapper.sh
check if you need any other services to run the script

---

### Post by alex488 on 2016-01-18
The following is what the terminal is showing on the account which I cannot access via the Ubuntu login screen. I accessed the account via CTRl+ALT+F4(or some other number).

/home/alex/.pythonbrew/pythons/Python-2.7.5/bin/python no module named virtualenvwrapper
virtualenvwrapper.sh: there was a problem running the initialization hooks.

If Python could not import the module virtualenvwrapper.hook-loader,
check that virtualenvwrapper has been installed for
VIRTUALENVWRAPPER_PYTHON=/home/alex/ .pyenv/shims/python and that PATH is 
set properly.
/home/alex/.pythonbrew/pythons/python-2.7.5/bin/python: no module named virtualenvwrapper
virtualenvwrapper.sh: there was a problem running the initialization hooks.

If python could not load the module virtualenvwrapper.hook_loader,
check that virtualenvwarpper has been installed for
VIRTUALENVWRAPPER_PYTHON=/home/alex/.pyenv/shims/python and
that PATH is set properly


I cannot execute commands. I can type them but when I press enter the cursor moves to the next line and nothing else happens.

---

