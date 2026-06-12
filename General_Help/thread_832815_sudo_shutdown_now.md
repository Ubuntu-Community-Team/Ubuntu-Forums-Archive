---
title: "sudo shutdown now"
date: 2008-06-18
forum: General Help
---

### Post by dexter.deepak on 2008-06-18
is it right to invoke "sudo shutdown now" from the terminal to shutdown the system. what i have "observed" is that it usually leads to an abrupt shutdown(may be  i am wrong)
i need to make some "safe and clean" shutdown script for nautilus....and so i need a better command....can someone help me ??

---

### Post by sdennie on 2008-06-18
Using "shutdown", "halt", "reboot" and "poweroff" should all be perfectly safe.  What makes you think it's shutting off abrubtly?

---

### Post by m0ar on 2009-12-25
Sorry for bringing this old one to top, but I'm having the same problem with sudo shutdown now..

It closes my session, goes to the command line login and locks up, it wont respond to typing or any hotkeys. Any ideas?

---

### Post by Strongman332 on 2009-12-25
why ware you trying to shut down your computer via command line, just to be using the terminal or was it because x failed and you dropped to the command line?

i had this problem once when my graphics card failed

---

### Post by m0ar on 2009-12-26
> **Strongman332 said:**
> why ware you trying to shut down your computer via command line, just to be using the terminal or was it because x failed and you dropped to the command line?

i had this problem once when my graphics card failed

I usually have two or three terminals up, and I don't see why that question even is relevant?

The odd thing is that poweroff works fine, but shutdown always locks up..

---

### Post by AntiFlash on 2010-08-26
sudo shutdown -h now -> halts session...shuts down etc...

---

### Post by Iowan on 2010-08-26
This one seems finished...

---

