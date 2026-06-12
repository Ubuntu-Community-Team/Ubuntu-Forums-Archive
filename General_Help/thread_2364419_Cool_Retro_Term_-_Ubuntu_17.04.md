---
title: "Cool Retro Term - Ubuntu 17.04"
date: 2017-06-23
forum: General Help
---

### Post by Cer3alK1ll3r on 2017-06-23
Has anyone got the Cool Retro Term working in Ubuntu 17.04?  I know they had it working and officially supported in 16.10, but I have seen nothing for 17.04.  I tried to get it working, but I keep getting different qt errors.  Thank you for the help.

---

### Post by zerobytez on 2017-06-23
Whilst I am probably not experienced enough to deal with this, you should at least post the error so we can see what went wrong.

---

### Post by Cer3alK1ll3r on 2017-06-23
I will post a screenshot tonight.  The first error I got was about qt, which I resolved by installing qt5 in terminal.  The error I'm stuck on is one where it stops the "make" command because of....

I think it may be missing a file, but will double check and post it here tonight,  Thank you.

---

### Post by Habitual on 2017-06-23
> **Cer3alK1ll3r said:**
> The error I'm stuck on is one where it stops the "make" command because of....

I think it may be missing a file, but will double check and post it here tonight,  Thank you.
Try 
```
sudo apt-get install build-essential 
```
and re-run make again.

---

### Post by deadflowr on 2017-06-23
Why not add the ppa?
[https://launchpad.net/~bugs-launchpad-net-falkensweb/+archive/ubuntu/cool-retro-term]("https://launchpad.net/~bugs-launchpad-net-falkensweb/+archive/ubuntu/cool-retro-term")

---

