---
title: "Gtk-WARNING **: Unknown property: GtkComboBox.items"
date: 2008-06-19
forum: General Help
---

### Post by rpimenta on 2008-06-19
I use Ubuntu Hardy 8.04. When I do sudo network-admin -c eth0, I receive the output in title, and the application doesn't work.
My file /etc/network/interfaces is:
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0

Anyone know why of this output?
Thanks,
Rodrigo

---

### Post by nike984 on 2008-08-05
try to use different theme
and check whether the same error message pop out.

---

### Post by zenzid on 2010-01-20
I got the same problem:

network-admin --configure

** (network-admin:18617): CRITICAL **: Cannot create session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(network-admin:18617): Gtk-WARNING **: Unknown property: GtkComboBox.items
Segmentation fault

I'm using the mint. Ubuntu-derivative, with gnome and  all the network-admin gui works fine until you press "preferences"  on some of the sub menus:(

---

