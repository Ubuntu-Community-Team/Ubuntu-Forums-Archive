---
title: "Cant log in, x-server rests"
date: 2013-04-04
forum: General Help
---

### Post by Falc7 on 2013-04-04
I cant log into my Kubuntu 12.10 install, I put the password in, the x-server resets (at least I think thats whats happening, i'm not really sure) as the screen goes black and I get a command line style writing for a second, and then I land back at the GUI log in screen.

---

### Post by raimo on 2013-04-04
Try this .. push **Ctrl+Alt+F2** and login, then remove  .Xauthority -file:
```
rm .Xauthority
```
and then **Ctrl+Alt+F7**

---

### Post by Falc7 on 2013-04-04
It says file not found :(

---

### Post by conradin on 2013-04-04
so can you login to a terminal session?
can you post you dmesg? like login, then try $startx see how that goes, then try the graphical login with i believe is KDM
hopefully you'll see some errors when it kicks you out. You could have missing software, a bug, or inappropriate hardware settings. 
is this a new install? or have you been using it, and now it doesn't work?
post errors

---

### Post by Falc7 on 2013-04-05
Yep I can log into a terminal session, and a guest session both.

Is there a way to copy the output of dmesg so I can paste it here? I didn't see any obvious errors in the output.

Startx command returns 'timeout' saying it cant find xauthority.

Its not a new install, I have Kubuntu 12.10, and a (backup, incase of situations where I cant boot into 12.10, as has happened now) 12.04, which both point towards the same encrypted home partition, it was working find until two weeks or so ago, when for seemingly no reason it stopped working.


Edit: I decided to reinstall the OS

---

### Post by rnerwein on 2013-04-06
> **Falc7 said:**
> Yep I can log into a terminal session, and a guest session both.

Is there a way to copy the output of dmesg so I can paste it here? I didn't see any obvious errors in the output.

Startx command returns 'timeout' saying it cant find xauthority.

Its not a new install, I have Kubuntu 12.10, and a (backup, incase of situations where I cant boot into 12.10, as has happened now) 12.04, which both point towards the same encrypted home partition, it was working find until two weeks or so ago, when for seemingly no reason it stopped working.


Edit: I decided to reinstall the OS
hi
for your question about to copy the output of anything --> e.g.: dmesg > blablu.txt
and then post blablu.txt as an attachment.
ciao

---

