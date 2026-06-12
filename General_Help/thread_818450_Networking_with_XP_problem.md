---
title: "Networking with XP problem"
date: 2008-06-04
forum: General Help
---

### Post by edno99 on 2008-06-04
Hello :)

I'm trying to network an xp machine with an ubuntu machine. I've got samba setup and can see the shared folders in windows explorer, but when i try to connect to them, it asks for a username and password. I put in the username and password for the administrator account for ubuntu into these boxes and it does nothing?!

I've tried setting up a guest user, but that does the same thing. Do i need to edit samba somehow to get it to work?

Thanks for helping the noob!

---

### Post by prince_niceguy on 2008-06-04
Yes you will have to add samba user who can access the shares. You can refer [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server") for adding the user to samba.

---

### Post by edno99 on 2008-06-04
Oh dear.... my first day with linux was going so well :(

Now I can't do anything in the terminal. It just keeps saying 

sudo: unable to resolve host (username)-desktop

I'm more confused now :(

---

### Post by prince_niceguy on 2008-06-04
Please do not mix the question. It would be a good idea to have separate thread for this issue and leave this thread for samba sharing.

did you try doing a reboot, hopefully itshould resolve the problem. if not you may have to change some network properties. nothing scary as such. after reboot just let us know if the issue persists.

---

