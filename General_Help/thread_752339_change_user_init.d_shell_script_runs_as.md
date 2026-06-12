---
title: "change user init.d shell script runs as"
date: 2008-04-11
forum: General Help
---

### Post by skunkwerk on 2008-04-11
I've got a script in my /etc/init.d folder that I need to run as a user, not root.  How can I do this?  Do I just chown the script to that user, or do I do some setuid thing?

thanks

---

### Post by brian_p on 2008-04-11
> **skunkwerk said:**
> I've got a script in my /etc/init.d folder that I need to run as a user, not root.  How can I do this?  Do I just chown the script to that user, or do I do some setuid thing?

thanks

It would be far, far better if you described what it is you want to achieve. No script in /etc/init.d should br run as a user.

---

### Post by skunkwerk on 2008-04-11
the script is calling a python program that runs a C program that needs an x server to display to.  I have setup gnome to auto-login on startup to a user ('root' was not available to auto-login to).  If I try to run the program as root, it says there was no x server found (this is running the script from a remote desktop connection as a user).  I don't know why this happens, as on a normal machine I can run as whatever user I want and they always connect to the x server that's available.

I suppose I could just 'su user' in the python script before calling the c program, right?

thanks

---

### Post by bodhi.zazen on 2008-04-11
use sudo

sudo -u <user_to_run_script> /path/to/script

---

### Post by pointone on 2008-04-11
Probably better to run it from **System > Preferences > Sessions**.

Another option could be to explicitly set the DISPLAY variable.

---

