---
title: "ClamAV and Linubies like me"
date: 2007-07-25
forum: General Help
---

### Post by doctorbrowder on 2007-07-25
OK, here's another one...

I'm trying to get ClamAV to update its signatures. I open the ClamAV panel by going to APPLICATIONS --> ANTIVIRUS, then on the ClamAV panel I select HELP --> UPDATE SIGNATURES. I get a terse little message saying "You must be root to install updates."

OK, great. How do I become "root"?

---

### Post by Techboy_Miata on 2007-07-25
to become temp root SUDO "command" -options
if you need SU rights using a text editor SUDO gedit path-to-file
thats about all i know im not familiar with clam AV i am looking at installing a AV just for kicks tho

---

### Post by doctorbrowder on 2007-07-26
I'm new at all this; I don't know what "SU rights" are. I know how to open a terminal, though. Exactly what do I type into the terminal to the root, and what do I do once I get there to update the definitions for ClamAV? Thanks!

---

### Post by strabes on 2007-07-26
I don't use an antivirus on linux so I'll assume the command for ClamAV is "clamav"

All you would have to do to open it as root is run: ```
sudo clamav
```

---

### Post by Techboy_Miata on 2007-07-26
SU stands for Super User or to become Root user. as root you can do anything no limits! including destroying your linux install. most times you wont need to use SU but when you do SUDO is the way to go. SUDO temporarily makes you root for the duration of that command and then returns you back to normal user mode.
dont let that bit about the fact of being able to destroy your system scare you but just be aware of the power you hold when operating as root

---

