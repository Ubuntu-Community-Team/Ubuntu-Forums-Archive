---
title: "Run script at login"
date: 2007-02-26
forum: General Help
---

### Post by Sengkim on 2007-02-26
Hi,

I have a myth server based on ubuntu edgy and because of a problem with my NAS server I can't mount some network drives using my fstab file. So I need to mount them using a small script.

Now, how can I run this script automatically when the user logs in?

BB
Peter

---

### Post by Ramses de Norre on 2007-02-26
For the whole system: put it in /etc/rc.local.
To executed only on log in by certain users: put it in the users session > startup list (system > preferences > sessions ...).

---

### Post by Sengkim on 2007-02-26
Hi,

I want it only for a specific user but I don't have the gui completly installed (so no preferences and such). Can't I do it using the CLI?

BB
Peter

---

### Post by bodhi.zazen on 2007-02-26
To run your script as a user, without the gui, put it in ~/.bash_profile

[http://heimhardt.com/htdocs/bashrcs.html](http://heimhardt.com/htdocs/bashrcs.html)

---

### Post by punx45 on 2007-02-26
> **Sengkim said:**
> Hi,

I want it only for a specific user but I don't have the gui completly installed (so no preferences and such). Can't I do it using the CLI?

BB
Peter

i think if you include the script in the .bash_profile for the user, it will be executed at login.   what I am unsure of is if .bash_profile is executed once at the first login, or every time a terminal session is opened.   if the case is the latter, you might want to consider adding a test for the mounted drive in the script to avoid potential trouble from attempts to mounting it if it is already mounted.

---

### Post by Ramses de Norre on 2007-02-26
> **punx45 said:**
> i think if you include the script in the .bash_profile for the user, it will be executed at login.   what I am unsure of is if .bash_profile is executed once at the first login, or every time a terminal session is opened.   if the case is the latter, you might want to consider adding a test for the mounted drive in the script to avoid potential trouble from attempts to mounting it if it is already mounted.

It's executed with every opening of a login shell, so you should set gnome-terminal to not act as a login shell. The tty's could cause problems though.

---

### Post by punx45 on 2007-02-27
i see.. 

so would adding to the .bash_profile, .bashrc or .profile be an inappropriate way to achieve this?

---

