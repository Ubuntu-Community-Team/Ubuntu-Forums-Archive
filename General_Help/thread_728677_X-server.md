---
title: "X-server"
date: 2008-03-19
forum: General Help
---

### Post by v5lur on 2008-03-19
I have been running Ubuntu Desktop 7.10 almost 1 week and one day I cant login to graphical enviroment, after I enter my username and password, it gives me error:

(process:5970): Gtk-WARNING **: This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details see:

[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(Process:5974): Gtk-WARNING **: This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details see:

[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/x-desktop:/tmp/.ICE-unix/5967
Failed to start message bus: Failed to read directory "/etc/dbus-1/session.d": No such file or directory dbus-deamon exited unexpectedly

** ERROR **: file gsm-dbus.c: line 118 (gsm_dbus_daemon_start): assertion failed:  |(dbus_deamon_pid !=0)
aborting...

I found the same bugs report in other forums, but I didnt find any solution how to fix it. Can anyone help? 

Thanx!

---

### Post by danwood76 on 2008-03-19
Are you able to login to the failsafe gnome?
You can select it under sessions in the bottom right hand corner.

Its possible that some config you have edited has caused this.
Have you made any changes recently?

---

### Post by v5lur on 2008-03-19
I cant login to failsafe mode, it gives me same error. I did update with update manager. I also installed samba and edited the smb.conf file.

---

### Post by danwood76 on 2008-03-19
Did you change your UID (user ID) or GID (group ID) anything like that?

---

### Post by v5lur on 2008-03-19
No I didnt. But after the problem appeared, I tried to create new user account and password, it had exactly same error.

---

