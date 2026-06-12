---
title: "Slaving my Old machine"
date: 2005-10-21
forum: General Help
---

### Post by Brandon14u2 on 2005-10-21
I want to slave my old pc to my new one and run it remotely.  What would be the best way to do this.  I don't have a network in my home.  Thanks for any advice.

Edit:  The main reason behind this is that my wife is getting just a tad bit annoyed that every so often the computer stops working.  I need something to experiment on.  With me, her, and our son in a two bedroom apartment, I definitely don't have enough room to set up a whole system.

---

### Post by jasmuz on 2005-10-21
Hello there,

The best way of linking two computers is obviously using the Ethernet cards.

Hence for linking up two computers you would need:

2 computers (duh!)
Ethernet cards on both
A small ethernet switch*
A ethernet cable of a considerable size*
Both machines running SSH (If both have Ubuntu or any other Linux, you could do even graphical logins)

*: If you use a special cable, called a crossover ethernet cable, you wont have to use the switch.

Next step would be configuring the IP on both ethernet cards, verify if you can ping both ways. After that is smooth sailing.

(By setting up a link between both computers, you can easily share any kind of data, as the internet connection or any other service that might interest you)

---

### Post by Brandon14u2 on 2005-10-21
will this set up work if I only have the box from the old pc (After I set it up of course)  I want to set the box right beside my new one and access it remotely without having to have the space for the whole set up.
Thanks

---

### Post by jasmuz on 2005-10-22
If your issue is budget and space, go with getting a crossover cable (it will make your life easier), and you dont need a full blown computer to access it, just the CPU will do (it must have SSH installed and enabled in order to allow remote logins)

---

