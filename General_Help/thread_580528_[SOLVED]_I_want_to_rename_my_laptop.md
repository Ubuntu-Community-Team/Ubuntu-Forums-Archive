---
title: "[SOLVED] I want to rename my laptop"
date: 2007-10-18
forum: General Help
---

### Post by horrorpunk138 on 2007-10-18
A few weeks ago I switched to 100% ubuntu, but I ran into some problems with the installation. Luckily, a more knowledgable friend of mine helped me out and got it running for me, but during the install he gave my comp a stupid name.
Naturally this doesn't affect performance what-so-ever, but doesn't change the fact that it ticks me off every time I look at it.
Any way I can re-name the computer, short of completley reinstalling?

---

### Post by 444 on 2007-10-18
sudo hostname putnamehere

Then restart.

---

### Post by horrorpunk138 on 2007-10-18
Didn't work, other ideas?

---

### Post by dondad on 2007-10-18
> **horrorpunk138 said:**
> Didn't work, other ideas?


Try looking in the system>network. In the general tab there is a place to put the host name.

---

### Post by bodhi.zazen on 2007-10-18
Change you hostname in both /etc/hosts and /etc/hostname

---

### Post by horrorpunk138 on 2007-10-21
Not working.

I'll clean my language here, but I'm gonna be stuck with seeing "rob@robisapoophead" every time I open the terminal aren't I?

---

### Post by FuturePilot on 2007-10-21
Left Click on the Network Manager Icon by the clock, and go to Manual Configuration. Click on the General tab and change the Host Name. Reboot then.

---

### Post by Taino on 2007-10-21
edit your hostname in 2 files.

in a terminal window type...

sudo gedit /etc/hostname

edit it, save it

sudo gedit /etc/hosts

edit it, save it, reboot.

---

### Post by horrorpunk138 on 2007-11-04
Heh. Oddly enough, trying all of the suggestions at once worked.

Thank you guys.

---

