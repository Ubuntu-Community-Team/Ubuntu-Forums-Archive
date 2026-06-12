---
title: "iptables - how to save my chains?"
date: 2005-08-15
forum: General Help
---

### Post by cristianommxp on 2005-08-15
Hi,

I'm trying to use iptables on Hoary, but I'm having a problem.

I'm doing like this:

    $ sudo iptables -t nat -A POSTROUTING -s 192.168.0.3 -o eth0 -j MASQUERADE

And it works fine. But when I restart the computer, the table "nat" is clean.

What do I have to do to iptables save my configurations?

10ks

Cristiano M. Magalhaes

---

### Post by PeP on 2005-08-15
make a script:

#!/bin/bash
iptables -t nat -A POSTROUTING -s 192.168.0.3 -o eth0 -j MASQUERADE

name it whateveryouwant.sh

add this line to /etc/network/interfaces after "iface eth0 inet xxxx"
        pre-up /path/whateveryouwant.sh

---

### Post by cristianommxp on 2005-08-16
it didn't work.

---

### Post by PeP on 2005-08-19
can you show us the /etc/network/interfaces file 
(change personal info and ip if you wish)

---

### Post by tsujigiri on 2005-11-20
worked for me.

Did you remember to change permissions?

chmod +x whateveryouwant.sh

---

### Post by kedmond on 2007-11-15
I can't get this to work.  But this thread is from 2 years ago...so I guess Ubuntu's system has changed, perhaps?

---

