---
title: "Bittornado, nothing but red. Help?"
date: 2005-10-10
forum: General Help
---

### Post by sad780 on 2005-10-10
Bittornado downloads nothing, connects to no peers, and stays red. 

Gnome bittorrent downloads some things, but very slowly. I often get the "invalid client port" message, even on very healthy torrents.

Im connected via an Actiontec Dsl modem/router. Im not aware of any firewalls running on my comp. 

I am new to Ubuntu/Linux, so any dumbed-down advice or help would be appreciated.

---

### Post by gorkhal on 2005-10-10
your router should have a built in firewall, open up the ports in that firewall, see if that helps...good luck

---

### Post by sad780 on 2005-10-10
I never had any problems with my router under windows. It is supposed to automatically forward my ports (It is set up to forward "10000-60000 to anyIP"). Is it different with linux. Should I set up a static ip address and manually forward ports? Could it be just the version of Bittornado(installed with syanptic 0.3.8)?

---

### Post by kingsidy on 2005-10-10
my problem with the bittorrent was similar to yours. turned out that firestarter was blocking the communication. so try disabling your firewall (if u have one) and see if it is going to change anything. also when u use bitorrents you have to make sure that u have seeds or at least peers (i assume you already know that).

good luck

---

### Post by gorkhal on 2005-10-10
[QUOTE=sad780]I never had any problems with my router under windows. It is supposed to automatically forward my ports (It is set up to forward "10000-60000 to anyIP"). Is it different with linux. Should I set up a static ip address and manually forward ports? Could it be just the version of Bittornado(installed with syanptic 0.3.8)?[/QUOTE]

no you are quite right...it is just with ubuntu, with windows your bittornado ports would be forwarded automatically, but not so with ubuntu, dont know about the other distros though :D

so yeah manually set up the ports and see how that goes...

---

