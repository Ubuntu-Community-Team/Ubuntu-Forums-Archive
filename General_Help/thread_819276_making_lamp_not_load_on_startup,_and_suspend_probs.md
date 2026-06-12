---
title: "making lamp not load on startup, and suspend probs"
date: 2008-06-05
forum: General Help
---

### Post by Kinnza on 2008-06-05
hi

im pretty sure its all connected somehow...
the Lamp server is installed and starts on startup and stays up ...

before i installed it (im pretty sure that's the only thing that is differant) suspend worked perfectly
now, it takes it a few minutes to wake up from it
could that be related?

anyway, any ideas on how i can make it not start at startup and just do it on a script?

---

### Post by Kinnza on 2008-06-08
anyone?

---

### Post by NikoC on 2008-06-08
Hmmz I think at startup mysql and apache2 are being loaded, so in order to prevent these two from starting automatically type in a terminal:
sudo update-rc.d -f apache2 remove
sudo update-rc.d -f mysql remove

To start them up manually enter in a terminal:
sudo /etc/init.d/mysql start
sudo /etc/init.d/apache2 start

To stop them again, repplace start by stop

Hope this helps you out...
cheers.

---

### Post by Kinnza on 2008-06-08
thanks im sure it does. i will try that
:D

---

### Post by cariboo on 2008-06-08
Why do you want to put a server in suspend mode? The idea of a server is for it to always be available.

Jim

---

### Post by Kinnza on 2008-06-08
its not my server
its my laptop.... development station :D

---

