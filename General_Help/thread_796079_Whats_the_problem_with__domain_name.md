---
title: "Whats the problem with  domain name"
date: 2008-05-16
forum: General Help
---

### Post by worldy on 2008-05-16
I have a standalone desktop with a wired internet connection and i use gutsy.

Once i set a domain name for fun, i am having trouble in using nautilus. Its take so much time in accesing places like HOME,COMPUTER and in opening files.
My usplash screen which was working fine earlier is now breaking in between,taking too much time and showing messages,which i cudn't read till now become the gnome login is coming too soon. What should i do to view the messages. I tried 'dmesg' but i cant figure out where is the problem.i think 'dmesg' is not showing everything.

When i did the same on my laptop to test, exactly the same problems are occuring.

The problem is not going even after removing the domain name.

What is the problem with domain names.

PS: I am a linux newbie

---

### Post by Monicker on 2008-05-16
Also look at the following logs:

/var/log/messages
/var/log/daemon.log
/var/log/auth.log

---

### Post by worldy on 2008-05-16
i am unable to diagnose anything from those logs.

/var/log/boot is empty
it would have been good if i could enable bootlogging.
How to enable bootlogging?

---

### Post by worldy on 2008-05-16
could any of you standalone gutsy users mind to set a domain name for its sake in SYSTEM > ADMINISTRATION > NETWORK > General > Domain name and make sure its working fine.

I got this complaint in two systems . I use a  shipit Gutsy CD .

---

