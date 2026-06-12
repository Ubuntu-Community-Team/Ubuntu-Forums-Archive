---
title: "Help with Error Message in Synaptic Package Manager"
date: 2007-01-15
forum: General Help
---

### Post by healthpellets on 2007-01-15
I was trying to use the Synaptic Package Manager, but I got this error when I loaded it:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Using Edgy...

Any tips?

---

### Post by samden on 2007-01-15
Try doing exactly what the error message tells you to do, that is why it is there!

ie type
sudo dpkg --configure -a
in a terminal.

I get this message occasionally, just doing what it says always fixes the problem.

---

### Post by JimmyBEng on 2007-01-15
What happened when you ran 'dpkg --configure -a' ?

---

### Post by healthpellets on 2007-01-15
my apologies for the n00bness of it all...

i simply forgot to add 'sudo' in front and it wouldn't let me do anything....

thanks for your help!!!

---

