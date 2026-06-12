---
title: "Startup error"
date: 2007-09-13
forum: General Help
---

### Post by Firippu on 2007-09-13
I let my six year old nephew play around on my computer and now i get this error on every startup
[IMG]http://img465.imageshack.us/img465/1999/snapshot2hm2.jpg[/IMG]

---

### Post by s26c.sayan on 2007-09-13
Post the output of the command 'groups'  from a terminal.

I think, somehow your user got removed from the privileged 'admin' group, and hence cannot use sudo.

---

### Post by debianchick on 2007-09-13
> **Firippu said:**
> I let my six year old nephew play around on my computer and now i get this error on every startup
[IMG]http://img465.imageshack.us/img465/1999/snapshot2hm2.jpg[/IMG]



Don't worry your nephew much didn't do much damage. Just have to backup and reinstall :tongue:

J/K, Looks like you shutdown your computer while adept or another package manager was running. Just click close

---

### Post by Firippu on 2007-09-13
i still have sudo..
when i click close, it opens up Synaptic Package Manager.
its annoying :|

---

### Post by s26c.sayan on 2007-09-13
> **debianchick said:**
> 
J/K, Looks like you shutdown your computer while adept or another package manager was running. Just click close

If you still have sudo, I think the above is indeed the case.

The session manager of Ubuntu has 'saved' an open synaptic window. Look under Preferences -> Sessions and remove the synaptic entry!

---

### Post by Firippu on 2007-09-13
i have xubuntu and it doesn't let me select sessions like ubuntu does..
can i edit it in the terminal?

---

### Post by s26c.sayan on 2007-09-13
In XFCE, that might be easier than in Gnome!!
Look at the startup applications list (or maybe it is called Autostart applications).

Look for any entry concerning synaptic!

---

### Post by Firippu on 2007-09-13
theres only two entries in Autostart applications, restricted drivers and printer

---

