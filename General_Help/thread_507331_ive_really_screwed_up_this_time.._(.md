---
title: "ive really screwed up this time.. :("
date: 2007-07-22
forum: General Help
---

### Post by luckyd on 2007-07-22
I wanted to install hplip-toolbox (dont know why it isnt in the repos) so i downloaded the installer for all of hplip and i guess i hadnt removed the hplip version from synapitic, so i ran into a bunch of errors in the installtion. In the end it finished and deposited all of its files in my home directory. I deleted those, but now when I tried to reinstall hplip it says this > E: hplip: subprocess post-installation script returned error exit status 1

So I guess the manual installation deposited files all over the place after all, and left the ubuntu version uninstllable, what do I do to remove those files?

---

### Post by brownknight on 2007-07-22
try sudo apt-get install -f

---

### Post by pashashome on 2007-07-22
I'm a very new linux user so you are warned. I looked in synaptic and the files you need appear there on my machine. You might want to check and see what repositories your synaptic is looking at.  A separate issue may be pyqt package see this link: [http://leetcode.net/2007/04/11-things-you-havent-seen-yet-in-ubuntu-feisty-fawn](http://leetcode.net/2007/04/11-things-you-havent-seen-yet-in-ubuntu-feisty-fawn)

Did you try to uninstall hplip? 

Google turns up more than a few llinks that look promising.

---

### Post by luckyd on 2007-07-22
Ok, i got the synaptic version to install, but when I run hp-toolbox i get

> error: Unable to connect to HPLIP I/O (hpssd).


---

### Post by pashashome on 2007-07-22
From a terminal try this:

```
sudo /etc/init.d/hplip restart

```
Does it start?

---

### Post by luckyd on 2007-07-22
It didn't :(

---

### Post by borris.morris on 2007-07-23
> **luckyd said:**
> It didn't :(

errors?

---

### Post by luckyd on 2007-07-23
the same ones, but i got it working by completely removing the /usr/share/hplip/ folder :) then reinstaling the new version from the web, maybe there is something wrong with the one in the repos?

---

### Post by borris.morris on 2007-07-23
most likely just conflicts.... but glad you got it working.

---

