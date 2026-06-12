---
title: "Brasero incorrectly working after upgrade."
date: 2008-05-06
forum: General Help
---

### Post by Nevermore on 2008-05-06
Hello everyone
after a disastrous upgrade to Hardy that was full of problems:
first ati driver didn't want to work
then mesa problem appeared
then i had to manually edit /usr/bin/compiz since was wrongly looking for /usr/local/bin/compiz
then i started to experience problems with firefox
and now

Brasero doesn't want to burn me Cd.
If i want to burn an iso, i put in a blank cd and it tells me: only 480Mb free..and i have 700mb free on a cdr..
Plus when burning something smaller, it doesn't eject after burning

this is a recurrent error i get

 brasero

** (brasero:10435): WARNING **: Could not connect to system bus: The maximum number of active connections for UID 1000 has been reached
process 10435: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3280.
This is normally a bug in some application using the D-Bus library.

** (gnome-mount:10449): WARNING **: Cannot connect to system bus: org.freedesktop.DBus.Error.LimitsExceeded : The maximum number of active connections for UID 1000 has been reached

What can i do?

---

### Post by original_jamingrit on 2008-05-06
You may want to consider a clean install.  From what I've read, not many people had problems upgrading, but the people who did got it really bad.

As a temporary substitute, check out this [HOWTO](http://ubuntuforums.org/showthread.php?t=363666) for burning from the command line.  you could also try installing a different burning app.

---

