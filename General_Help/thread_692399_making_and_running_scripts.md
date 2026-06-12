---
title: "making and running scripts"
date: 2008-02-09
forum: General Help
---

### Post by thefatmoop on 2008-02-09
so i want a script that will do this in a terminal  

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo macchanger -r eth1 
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher start
sudo /etc/dbus-1/event.d/25NetworkManager start


how would i make this? how would i run it

---

### Post by HermanAB on 2008-02-09
Open a console and run an editor:
$ sudo bash
# gedit test &

Now type this:
#! /bin/bash
/etc/dbus-1/event.d/26NetworkManagerDispatcher stop
/etc/dbus-1/event.d/25NetworkManager stop
macchanger -r eth1
/etc/dbus-1/event.d/26NetworkManagerDispatcher start
/etc/dbus-1/event.d/25NetworkManager start

Save the file.

Make it executable:
# chmod 754 test

Run it:
# ./test

Cheers,

Herman

---

