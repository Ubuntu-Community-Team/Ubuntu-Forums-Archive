---
title: "Updated from 7.10 to 8.04... where's the transmission client?"
date: 2008-04-26
forum: General Help
---

### Post by mrand on 2008-04-26
That I can tell, my update to 8.04 worked properly (including mythtv to 0.21), but it appears that it did not actually install the transmission bittorrent client.  Brasero is also missing.   Obviously I can install them myself, but now I'm wondering... what else is missing?

```
mrand@media:~$ uname -a
Linux media 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
mrand@media:~$ transmission
The program 'transmission' is currently not installed.  You can install it by typing:
sudo apt-get install transmission-gtk
bash: transmission: command not found
mrand@media:~$ brasero
The program 'brasero' is currently not installed.  You can install it by typing:
sudo apt-get install brasero
bash: brasero: command not found
mrand@media:~$ 

```

Thank you!

   Marc

---

### Post by GuitarRocker2562 on 2008-04-26
sudo apt-get install ubutnu-desktop


what does it say when you type that in?

---

### Post by mrand on 2008-04-26
> **GuitarRocker2562 said:**
> sudo apt-get install ubutnu-desktop


what does it say when you type that in?

Minor points I forget in the original:  I originally installed from the 7.10 alt cd (for RAID & LVM).  Got everything working and then installed mythbuntu on top of that.

Upgraded via update manager GUI after making sure that everything was up-to-date.

```
mrand@media:~$ sudo apt-get install ubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mrand@media:~$ 
```

   Marc

---

### Post by Sef on 2008-05-02
[Duplicate Post]("http://ubuntuforums.org/showthread.php?t=773072"). Locked.

---

### Post by mrand on 2008-05-03
Hmmm... Does anyone have any ideas on how I can get my system completely upgraded to Hardy?  Firefox 3b3 was installed, so it obviously got close.

Is there a more suitable forum or sub-forum that I should be asking this question in?


Thanks everyone!

Marc

---

### Post by zaussome on 2008-05-03
When I upgraded from 6.06 to 8.04, I ran into the same problem. It never really caused any inconvenience, you can go get most of the apps from Add/Remove or Synaptic.

---

### Post by mrand on 2008-05-03
> **zaussome said:**
> When I upgraded from 6.06 to 8.04, I ran into the same problem. It never really caused any inconvenience, you can go get most of the apps from Add/Remove or Synaptic. Thanks for the note.    I'm actually not that concerned with the missing packages... while it provides a slight bit of comfort that I'm not the only one on the planet that has seen this, I have to admit that thinking about the future doesn't give me warm fuzzies.  If my upgrade is incomplete, will upgrading next time work like it is supposed to?

Thanks again,

   Marc

---

