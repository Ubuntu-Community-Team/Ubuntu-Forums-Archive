---
title: "setuid on a script"
date: 2007-06-13
forum: General Help
---

### Post by Phantom784 on 2007-06-13
I'm trying to make a script setuid so it'll always run as root (it needs root to run iptables).  I tried "sudo chmod u+s script.sh" and "sudo chmod g+s script.sh", but when I run it, I still get an error saying iptables doesn't have root permissions.  How can I get this to work?

---

### Post by stchman on 2007-06-13
> **Phantom784 said:**
> I'm trying to make a script setuid so it'll always run as root (it needs root to run iptables).  I tried "sudo chmod u+s script.sh" and "sudo chmod g+s script.sh", but when I run it, I still get an error saying iptables doesn't have root permissions.  How can I get this to work?

A script doing root stuff sounds like a big security hole.

I would do the following:

sudo script.sh

Then enter your password.  This is more secure.

---

### Post by Phantom784 on 2007-06-13
I need a webserver to be able to call this script, which of course can't type in passwords.  The webserver is my captive portal, and needs to be able to modify firewall rules to give permission to users once they click to agree to the terms of service.  This is the best way I could think to do this.

---

### Post by stchman on 2007-06-13
> **Phantom784 said:**
> I need a webserver to be able to call this script, which of course can't type in passwords.  The webserver is my captive portal, and needs to be able to modify firewall rules to give permission to users once they click to agree to the terms of service.  This is the best way I could think to do this.

Best thing to do in that case is change ownership of folders you are going to be performing these duties.

This will allow your script to function.

---

### Post by Phantom784 on 2007-06-13
It's in /usr/bin, so I don't get why it isn't working.  It shows up the same color as other suid programs like passwd when i run ls on it.  and yes, it is owned by root.  any idea why it isn't working?

---

### Post by stchman on 2007-06-14
> **Phantom784 said:**
> It's in /usr/bin, so I don't get why it isn't working.  It shows up the same color as other suid programs like passwd when i run ls on it.  and yes, it is owned by root.  any idea why it isn't working?

Files in the /usr/bin folder are root ownership.  I don't recommend that you give full ownership in the /usr folder.

---

### Post by Phantom784 on 2007-06-15
I was able to get it working by having a setuid wrapper c program call the scripts.  For some reason it worked fine on a c program in the same directory, but not on the script.

---

