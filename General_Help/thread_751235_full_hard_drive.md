---
title: "full hard drive"
date: 2008-04-10
forum: General Help
---

### Post by Tim0miT on 2008-04-10
i have done nothing apart from install the needed apps on Ubuntu, i recently loaded virtual box up and set a a machine, i then deleted that machine before i even install windows. now my ubuntu is telling me my disk is 86% full when i have fu*k all on it...

how can this be, i have had the same problem before and the only way i ofuld was a complete re-format, but as you can see, this is not practical!!!:mad:


anyone able to help me, any way of freeing up Ubuntu of all the non-necessary files??:confused:

---

### Post by sefs on 2008-04-10
I'm not at my system right now but, there is a program called bonsai or something similar in the repositories, that can give you an idea of what is using up so much of your space in your Ubuntu installation.  

Go in to synaptic and search for either bonsai or the phrase "disk space usage"  and see if you find this program, and use it to check out how your disk space is allocated.

---

### Post by ryanhaigh on 2008-04-10
The application is actually called baobab and it may be installed by default, check accessories>disk usage analyser. I had this happen once when launching an application using nohup, basically it filled my home partition and I could not log in.

What size is the partition you allocated for ubuntu I made mine 20GB but with a lot of stuff installed its only at 5.2GB

As for clearing up some space I can suggest ```
sudo apt-get autoremove
``` which will remove uneccessary applications such as dependencies of software that may have been removed ```
sudo apt-get clean
``` which will remove the debs from your cache for all but the latest versions of applications and ```
sudo apt-get install localepurge
``` which will obviously install localepurge which removes uneccessary documentation in launguages other than those you configure.

---

### Post by Tim0miT on 2008-04-10
my total capacity is 17.2GB and i have used 11.6GB of it, i have no large files on my ubuntu HDD and not that many apps, not so many that it would take up 6GBs

the advice you gave didn't work and i am getting annoyed, windows neva did his sort of thing!!

sice getting ubuntu i have re-formated 3 times, twice is one day!

if ubuntu 8.04 has more annoying problems im going back to windows XP, sorry, lol

---

### Post by prshah on 2008-04-10
> **Tim0miT said:**
> my total capacity is 17.2GB and i have used 11.6GB of it, i have no large files on my ubuntu HDD and not that many apps, not so many that it would take up 6GBs


Can you post the result of ```
df -i
```

---

### Post by ryanhaigh on 2008-04-10
Remember that 8.04 is still under development.
Also remember that the ext3 file system reserves 5% of all partitions for root access only so that if you were to fill your area you could still boot and resolve your issues although this obviously doesn't account for your storage shortage unless you messed with it when installing of using tune2fs?

---

### Post by chayon on 2008-04-10
Hi all,

I recently installed Ubuntu 7.10 in my HP pavilion DV6666ez laptop. Everything except the sound is ok. I tried several solutions that I found on the posts but nothing worked. Does anybody here facing the same problem? If someone has a solution, please write back.

Thanks

Chayon

---

### Post by ryanhaigh on 2008-04-10
> **chayon said:**
> Hi all,

I recently installed Ubuntu 7.10 in my HP pavilion DV6666ez laptop. Everything except the sound is ok. I tried several solutions that I found on the posts but nothing worked. Does anybody here facing the same problem? If someone has a solution, please write back.

Thanks

Chayon

You should probably start your own thread as this is completely unrelated to the problem being discussed here.

[http://ubuntuforums.org/newthread.php?do=newthread&f=131](http://ubuntuforums.org/newthread.php?do=newthread&f=131)

---

### Post by TheLions on 2008-04-10
> **chayon said:**
> Hi all,

I recently installed Ubuntu 7.10 in my HP pavilion DV6666ez laptop. Everything except the sound is ok. I tried several solutions that I found on the posts but nothing worked. Does anybody here facing the same problem? If someone has a solution, please write back.

Thanks

Chayon

hijacking thread isn't nice, you should open a another thread and describe better your problem...
About your sound, you don't have any sounds or ?
Do you know manufacturer of your sound card?
is your sound card ever listed at alsamixer???

---

### Post by chayon on 2008-04-10
Sorry sorry. my mistake!! wrong thread!! Sorry to disturb you guys!!

---

### Post by Tim0miT on 2008-04-10
> **prshah said:**
> Can you post the result of ```
df -i
```

ill do it in the morning, on windows atm, lol

---

