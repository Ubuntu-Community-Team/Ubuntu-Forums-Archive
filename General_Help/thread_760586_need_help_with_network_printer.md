---
title: "need help with network printer"
date: 2008-04-20
forum: General Help
---

### Post by terry f on 2008-04-20
Hi

This is my first post, and I am not sure ware to post this. I have a printer connected to a xp computer, this computer is connected to my network and the firewall is off. I have another Ubuntu computer connected to the network as well. I use to be able to print to the printer on the xp computer over the network. I can still print to the printer from the xp computer, but not from my Ubuntu computer. The printer is a Brothers HL-1230.

Can any one help?

---

### Post by ryanhaigh on 2008-04-20
Printing over the network is supported under ubuntu also, you should just need to go to System>Admin>Printing, add a new printer, Windows printer via samba, browse to find the printer on the network, select brother, select HL1230, apply and you should be done.

note these instructions are for gutsy (version 7.10)

---

### Post by Craigupdegrove on 2008-04-22
this didn't work for me all i get is noise as if it is going to print but doesn't hp5610. ubuntu 8.04

---

### Post by schnauzer93 on 2008-05-02
I also have this same problem, but with an HP D1420.

---

### Post by don_xvi on 2008-05-03
I'll throw into this topic as well.
I upgraded this computer from 7.10 to 8.04 and now I can't add a Samba printer.
One of the things I'd read for so long is supposed to be hard on linux, printing, and for the year I've been playing with it has been so easy, now when I go through the process, after I give the printer a description, and click APPLY, it asks for "Password for q2user on localhost?"  I've tried using the password for q2user on the linux box, and that's rejected, I've tried passwords that I think I used on the Windows box that hosts the printer and they all come back rejected.
Where did this new prompt come from (I don't remember one before) and why is it broken, and most importantly, how do I fix it ?

PS- I just tried on the 8.04 box next door and it doesn't ask me for any password and added just fine !

---

