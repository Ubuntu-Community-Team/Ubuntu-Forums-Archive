---
title: "3 migration issues on 12.04"
date: 2012-12-24
forum: General Help
---

### Post by lekofraggle on 2012-12-24
Ugh, I have headache after smoke inhalation... ..metaphorically speaking anyway.

Okay, so it has been a while since I have been over here.  I recently recieved a lenovo w500 after a fire sale at my wife's work.  I am using ubuntu 12.04 to build android cm10 on a vm on my macbook pro.  I want to let the new machine do all the building, but I am having three headaches.

1) I would love to migrate my build enviroment from the vm to the new pc, but it keeps failing every way I try (pybackpack, cp, % tar).  Most fail on backup (I have very little space free on my vm), but those that succeed fail on restore.

2) I tried to start from scratch, but every time I try to repo sync (after the first one, I get this error...
fatal: unable to connect to github.com:
github.com[0: 207.97.227.239]: errno=Connection refused

3) this one is just annoying, after a few days on the new install, the snap to resize (or any opengl effects other than a transparent terminal window seem to fail).

So, I think my system is not quite there yet.  Does anyone have any advice?  Thank you in advance.

---

### Post by gordintoronto on 2012-12-24
How and what did you install on the Lenovo? It sounds like you did a Wubi install of Ubuntu 12.04. Wubi is really just for evaluating Ubuntu.

---

### Post by lekofraggle on 2012-12-24
Thank you for your reply. I used 12.04 and grabbed the installer from here[HTML]. http://www.ubuntu.com/pre-download?distro=desktop&bits=32&release=lts/[/HTML] using dd.
Then, I urned it to an sd card and put it in a bootable Sd reader. 
I installed it to main memory. 

~Leko

---

