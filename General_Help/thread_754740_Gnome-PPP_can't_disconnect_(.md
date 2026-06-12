---
title: "Gnome-PPP can't disconnect :("
date: 2008-04-14
forum: General Help
---

### Post by Dobroslav on 2008-04-14
I have Ubuntu 7.10.When I click on disconnect,Gnome-PPP disappear from notification area and I get new window for connection.But,when I get on the phone,there is no signal for calling.So,I must unplug the network cable and plug in again to disconnect.Can I disconnect on other way?

---

### Post by ScorpKing on 2008-04-14
You can try sudo poff to stop the modem.

---

### Post by Dobroslav on 2008-04-14
I've tried but no :(.

---

### Post by ScorpKing on 2008-04-15
something else that might do the trick. run pstree | grep ppp to see if the modem is still connected. is something shows close it with sudo killall <process_name>. hope it works

---

