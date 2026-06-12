---
title: "firestarter without gnome?"
date: 2005-07-25
forum: General Help
---

### Post by spacemonkey on 2005-07-25
As I understand it, firestarter runs regardless of if you launch the gui control for it in gnome.  Well I've got an ubuntu server that only has fluxbox, and I'd really like to avoid installing any gnome libs, but I want to install firestarter on it.  Is there any way to do this?  When I try to install it via apt-get it wants to install a bunch of other libs that I don't want on the server.

---

### Post by ubuntu_demon on 2005-08-03
you don't have to run a firewall unless you are paranoid or run a server.

but to answer your question : IMO you have four options
1)search for another GUI firewall (I think firestarter has the easiest/best gui)
2)just install the libs and firestarter. The libs probably don't hurt you that much
3)just install the libs and firestarter. Create your firewall settings and apply them.After this do : $ sudo iptables-save > somefile
use "somefile" to create your iptables script
4)create your iptables script from scratch

I also used firestarter to get me on my way with my own iptables script. If you want I can explain a bit more.

---

