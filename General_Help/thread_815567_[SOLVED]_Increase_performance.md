---
title: "[SOLVED] Increase performance"
date: 2008-06-01
forum: General Help
---

### Post by LitusMayol on 2008-06-01
Hi everyone!

I'd like to know if there is any kind of the dos and don'ts about increasing **Ubuntu**'s performance. I'd like to improve it's stability, speed, security... But I'm talking about general use, I mean: I know that if I get better hard disk more memory capacity, or if I get a new prcessor it'll be speedest. General advice about how to use the computer without getting the computer to the deadline.

I don't know if I've been able to explain...


Thanks! ;)

And pardon the newbie!

---

### Post by Lord Xeb on 2008-06-01
O_o Computer specs? I can figure out what you can do from there.

---

### Post by jamewill on 2008-06-01
go to system - admin - service and disable any services you don't need

e.g. if you don't have a printer disabling the printer daemon on boot will result in a (tiny) advantage etc etc

another boot related one is to install bootchart
sudo apt-get install bootchart (if not there already)
to see what your computer spends time on during boot

if you want faster response then use a lighter window manager e.g. Xubuntu
* less funcationality
* more speed
better?
the choice is yours...


perhaps others will have more useful contributions :-)


jw

---

### Post by LitusMayol on 2008-06-01
> **jamewill said:**
> go to system - admin - service and disable any services you don't need

e.g. if you don't have a printer disabling the printer daemon on boot will result in a (tiny) advantage etc etc

another boot related one is to install bootchart
sudo apt-get install bootchart (if not there already)
to see what your computer spends time on during boot

if you want faster response then use a lighter window manager e.g. Xubuntu
* less funcationality
* more speed
better?
the choice is yours...


perhaps others will have more useful contributions :-)


jw

That's exactly about the kind of advice I was talking about! That's the idea, thanks **jamewill**, thanks dude! ;)

---

### Post by Rocket2DMn on 2008-06-01
I like to use a program called bum (boot-up manager)
```
sudo apt-get install bum
```
Then use System->Administration->Boot-Up Manager
Here are some other links, too:
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)
[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by LitusMayol on 2008-06-02
> **Rocket2DMn said:**
> 
Here are some other links, too:
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)
[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Wow **Rocket2DMn**! That's finally what I was looking for! Thanks man!

---

