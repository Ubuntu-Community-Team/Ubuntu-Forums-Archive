---
title: "HP 712c in 7.10"
date: 2007-12-24
forum: General Help
---

### Post by mitchell2345 on 2007-12-24
Hi,

I just installed Ubuntu 7.10 and am trying to get my Printer to work.  It is a old HP 712c connected via parallel port.  

The printer wizard doesnt find it automatically so i have to do it manaually.  Here is what I do:

System>admin>printing>new printer

select LPT #1 (only lpt option)
Choose the correct PPD (HP 712c)
next, apply
looks like it worked.

When i print a test page i get no response from the printer.  When looking through the CUPS web interface I can see when a submit a job it goes to a 'stopped' state immediately.  What is the issue?

Thanks,
Mitchell

---

### Post by linuxwizard on 2007-12-24
Read through this
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530)

Look on this page for : Printing with AppArmor (info above came from)
[https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes)

---

### Post by mitchell2345 on 2007-12-25
Thank You!  

I searched around for bugs but couldnt find that one.


I did a 

sudo aa-complain cupsd
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
owner@main-computer:~$ 


and set the printer up again and BINGO!  Printing away!

Thanks
Mitchell

---

### Post by linuxwizard on 2007-12-25
You're Very Welcome, Glad to hear that took care of your problem.

---

