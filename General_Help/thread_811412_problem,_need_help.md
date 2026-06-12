---
title: "problem, need help"
date: 2008-05-29
forum: General Help
---

### Post by aalami90 on 2008-05-29
hello, i started having a set of problems on my ubuntu 8.04
problems are :

1- it says i have 0 free space, while i know for a fact that i do have at least 10 GB ( i can edit a document file, but i cannot save it for example)
2- i cannot connect any external harddrive
3- my aMsn doesnt open anymore, however, it says in the processes that "wish" is there
4- i cant access my bookmarks in firefox , and i cannot perform a search in the "searching part" of the navigation toolbar(when i press enter or click on the button, nothing happens"
5- when i press the the power button in the Panel (the panel which has applications, places etc.) it just disappears completely
6- using any internet browser, i cannot watch a youtube video for more than 5 seconds

even my shortcuts on the left panel in file browser have dissapeared.

i noticed one thing though: in the system monitor, there is a process called "trackered" which keeps using a big percentage of the CPU

anyone might know what the problem is, i am new to ubuntu

can it be a virus or something

thanks in advance

---

### Post by kpkeerthi on 2008-05-29
Can you post the output of
```
df -h
```

Tracker is a search tool. I find it using a lot of CPU when it starts indexing. You can turn it off from starting from System -> Preferences -> Session -> Startup Programs. Reboot.

---

### Post by aalami90 on 2008-05-29
> **kpkeerthi said:**
> Can you post the output of
```
df -h
```

Tracker is a search tool. I find it using a lot of CPU when it starts indexing. You can turn it off from starting from System -> Preferences -> Session -> Startup Programs. Reboot.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  101G     0 100% /
varrun               1009M  112K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   44K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
lrm                  1009M   38M  972M   4% /lib/modules/2.6.24-17-generic/volatile
overflow              1.0M   36K  988K   4% /tmp



Also, when i start up the laptop, the networking and the battery sign and stuff take a long while to load

---

### Post by kpkeerthi on 2008-05-29
> 
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 106G 101G **[COLOR="Red"]0 100%[/COLOR]** /


You seem to have used up all your space and thats probably is causing 'most' of the problems. 

Total = 106G
Used = 101G
The remaining 5G (i.e 5%) of the total space is reserved for the root so he can still access your system when it is filled up 100% to fix things up.

Free up space for ubuntu and see how better it runs.

---

### Post by kpkeerthi on 2008-05-29
Use gparted to resize /dev/sda1

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

