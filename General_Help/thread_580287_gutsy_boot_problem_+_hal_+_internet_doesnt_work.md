---
title: "gutsy boot problem + hal + internet doesnt work"
date: 2007-10-18
forum: General Help
---

### Post by cbo_x on 2007-10-18
Hi all

I installed 7.10 on my compaq presario v2000 but if I try to boot it normally it goes to a black screen.

I can go to recovery mode and run "gdm" and gnome runs but then it says "failed to initialise HAL"

And also the internet doesnt work.

I enabled the software modem driver from the restricted drivers manager, and now there is a tick next to it, but it says "not in use." I cannot enable the ATI accelerated graphics driver or the Firmware for Broadcom 43xx chipset family" since I can't connect to the net.

If I try to run nm-applet from the terminal I get a message like this:
(nm-applet:4942): WARNING **: <WARN> nma_dbus_init(): org.freedesktop.DBus.Error.FileNotFound raised:
Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Also if I click the shutdown button on the top right corner everything freezes for about 15 seconds except the mouse.

Any help most welcome.

---

### Post by cbo_x on 2007-10-18
just adding that  i tried the suggested solution (on other threads) of resetting dbus using sudo /etc/init.d/dbus restart 

the network manager icon loads but it wont detect any networks so I cannot connect to the net.

---

### Post by pescio on 2007-10-19
Hi,

I get the same behaviour. I have a 'hp compaq d330 dt', and I upgraded from ubuntu 7.04 [fresh install] to 7.10 yesterday.
I also resolved that going on rescue mode and giving 'gdm'.
My internet is working anyway [I'm on a lan at work].

---

