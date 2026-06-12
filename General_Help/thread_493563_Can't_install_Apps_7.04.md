---
title: "Can't install Apps 7.04"
date: 2007-07-05
forum: General Help
---

### Post by shooter902 on 2007-07-05
Hey guys, first time user and first time posting. Just installed 7.04 on an older HP Pent III machine to try it out. Install went fine, but when I was trying to install an app using "gdebi 0.2.4ubuntu1" it hung and had to force kill it, I rebooted and tried it again using Syaptic but I get the following error whenever I try to add or remove ANY app! :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to open a term window and enter this command but was told I needed to be a superuser to do this. Any tips? like I said, today was the first time playing with Ubuntu or anything other than gatesware, and LOVE it..just need a little newbie help.

Thanks loads
Phil

---

### Post by NeoLithium on 2007-07-05
> **shooter902 said:**
> Hey guys, first time user and first time posting. Just installed 7.04 on an older HP Pent III machine to try it out. Install went fine, but when I was trying to install an app using "gdebi 0.2.4ubuntu1" it hung and had to force kill it, I rebooted and tried it again using Syaptic but I get the following error whenever I try to add or remove ANY app! :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to open a term window and enter this command but was told I needed to be a superuser to do this. Any tips? like I said, today was the first time playing with Ubuntu or anything other than gatesware, and LOVE it..just need a little newbie help.

Thanks loads
Phil

Just open the terminal window back up, and type in:
```
sudo dpkg --configure -a
```
Then enter the password for your user, and it will run the command with the proper permissions :)  sudo essentially makes you a temporary super-user. All the power, none of the hassles of stayiing in root as some other distro's do :)

---

### Post by shooter902 on 2007-07-05
Thanks NEO, 

That was so simple I feel stupid..lol..I will remember that one..I'm sure I will have pleanty more questions before I'm done. Everything is going pretty well, I am shocked. We will see how it goes when I move it over to my AMD 64 I built just for Ubuntu.

Thanks so much for your help

Regards
Phil

---

### Post by NeoLithium on 2007-07-05
You're very welcome. Never ever feel stupid. Linux is a new learning curve that just takes time. Us in the forums realize that and are happy to help! :) Welcome to Ubuntu!

---

