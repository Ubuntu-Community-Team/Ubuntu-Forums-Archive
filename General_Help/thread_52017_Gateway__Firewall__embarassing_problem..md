---
title: "Gateway / Firewall  embarassing problem."
date: 2005-07-26
forum: General Help
---

### Post by FuzzyTheBear on 2005-07-26
This is a weird one 

I got Ubuntu set-up on the gateway/firewall machine.
IT's a IBM Cyrix II processor with 64 MB  RAM and plenty
hard disk space left on it .

All goes well with most applications like web browsing and 
the likes .. only there's a hic .. 
When i start the updates on my gentoo box .. half the time the 
update session ends up with a hard reset of the gateway. 

ex : start emerge -u world  (  sorry for the people who are allergic ;) 
check the screen , when a large pack is downloaded .. " poof " 
the machine resets .. not go down ..  hard reset like pressing the 
switch. 

What's going on ? 
Why an update on a machine would reset the gateway is beyond me .. 
Any suggestions ?? 

PS  this aint no crank call .. :| 

help   :) 

Fuzzy

---

### Post by jason_dc on 2005-07-26
Could be a hardware issue...

Does this happen on any type of large download?

I had this on an IBM server, it didnt matter what O/S I had on it some large data transfer would cause a hard reset, no log information nada

I tried with Suse, Fedora and even W2k

Unfortunatly I tried changing disks, NIC's and memory without any success, I gave up in the end  ](*,)

---

### Post by FuzzyTheBear on 2005-07-26
Well no ..   that's part of the whole picture 
You can download an ISO .. ( just made sure by double
checking yet again and downloading a fresh ubuntu iso .. ) 
I can download large files with no problem .. 
It's just when i use emerge -u xyz    ( update ) 

Been told could be RAM ... memtestx86 reports nothing

Im just baffeled :)   ubuntu's running smoothly 
i even can use the gnome desktop on this small machine 
and have pretty impressive results for a machine this old  :)

The firewall is  Firestarter ..  i had this on several distros but 
im totally satisfied of the results on ubuntu.

It didnt have this when i was running fedora core 1 .. 
but the distro being old and the newer ones not agreeing with the 
old video card .. ubuntu is the only distro that works on it atm with the
newer firestarter. 

Im keeping an eye on the list .. but have to go to work :| 
So answers will have to wait for the end of the day 

Thanks 

Fuzzy

---

### Post by FuzzyTheBear on 2005-07-30
This turns out to be more specific : a single file.

glibc-2.3.5.tar.gz 

I tried wget  ftp  http and  dcc with IRC .. same result .. 
I tried several download mirrors also .. 

Everytime i try to download , by whatever means i get the same 

" poof " reset .. 

Im going to get tired later and plug my computer direct to the 
modem and just bypass this whole situation   :) 

If anyone has an explanation why a single file would do that 
you're more than welcomed to post  :D 

What's in the file that can actually cause this ? 
Ever saw something similar on your systems ? 

Happy hacking  :D

---

