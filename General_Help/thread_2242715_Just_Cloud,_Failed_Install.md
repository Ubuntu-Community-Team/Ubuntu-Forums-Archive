---
title: "Just Cloud, Failed Install"
date: 2014-09-03
forum: General Help
---

### Post by Ronald_Barboza on 2014-09-03
I had Just Cloud before on Ubuntu LTS 14.04, I redid my hard drive with same O/S. Tried to install Just Cloud and this is what I get

 "(Reading database ... 
(Reading database ... 5% 
(Reading database ... 10% 
(Reading database ... 15% 
(Reading database ... 20% 
(Reading database ... 25% 
(Reading database ... 30% 
(Reading database ... 35% 
(Reading database ... 40% 
(Reading database ... 45% 
(Reading database ... 50% 
(Reading database ... 55% 
(Reading database ... 60% 
(Reading database ... 65% 
(Reading database ... 70% 
(Reading database ... 75% 
(Reading database ... 80% 
(Reading database ... 85% 
(Reading database ... 90% 
(Reading database ... 95% 
(Reading database ... 100% 
(Reading database ... 208374 files and directories currently installed.) 
Preparing to unpack .../Downloads/JustCloud_32.deb ... 
Unpacking justcloud (3.3.0.15) over (3.3.0.15) ... 
Setting up justcloud (3.3.0.15) ... 
dpkg: error processing package justcloud (--install): 
 subprocess installed post-installation script returned error exit status 1 
Processing triggers for man-db (2.6.7.1-1) ... "

I tried it on another PC that has same O/S and it gave me the same message. Is there a way to install it through "Terminal"? Thanks for all your help, Ron.

---

### Post by moore.bryan on 2014-09-03
You could always try the trusty "sudo apt-get -f install" method and see if that resolves anything...

---

### Post by Ronald_Barboza on 2014-09-04
No that didn't work, but this is what I got.[ATTACH]256155[/ATTACH]

---

### Post by moore.bryan on 2014-09-08
Hmm... that's weird. Are you installing justcloud via a repo or from deb?

---

### Post by nerdtron on 2014-09-08
And did you follow a tutorial on how you are installing Just Cloud? Can you post the link?

---

