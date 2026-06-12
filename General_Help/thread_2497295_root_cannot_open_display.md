---
title: "root cannot open display"
date: 2024-04-29
forum: General Help
---

### Post by hakelm on 2024-04-29
Using expect under gnome i login as root:

expect -c 'spawn su - ;expect senord:;send "assword";interact'

but opening a GUI-application doesn't work:


spawn su -
Lösenord: 
root@x22:~# nautilus


(org.gnome.Nautilus:50916): Gtk-WARNING **: 13:56:46.709: cannot open display: 
root@x22:~# 

Doing the same using su insted of expect works OK.
Why is this so?
My system is Ubuntu 22.04 on an Intel i7.

---

### Post by TheFu on 2024-04-29
Nope.  Root can't use a GUI login.  Nothing to see here. Move along.  This should not work.

---

### Post by MAFoElffen on 2024-04-29
In Ubuntu, the 'root' user does not have right to use a GUI. It is felt as a security risk.

The root account is disabled by default, GDM is by default set to AllowRoot=false, and PAM is set to not allow root to log into GDM...

So yes, there are many things set up to not allow a root user access to a GUI Desktop or GUI App's. It can be done, but is felt to be like running with scissors.

---

### Post by hakelm on 2024-04-29
I have AllowRoot=yes and I can log in to gnome with my root account so this shouldn't' be the problem.

---

### Post by TheFu on 2024-04-29
> **hakelm said:**
> I have AllowRoot=yes and I can log in to gnome with my root account so this shouldn't' be the problem.

I thought X/Windows had built-in code to prevent running from a root session.  Could be wrong.  Might just be a PAM setting in /etc/pam.d/

---

### Post by MAFoElffen on 2024-04-29
Also the setting in the GDM conf file... <--- Becaseu that has a setting there locking root out also. Then after all that, you would have to generate an .Xauthority file for the root user...

Just remembering that: "Just because something is possible, doesn't make it a good idea."

---

