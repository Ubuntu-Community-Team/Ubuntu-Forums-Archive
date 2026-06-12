---
title: "Electrical outage made bad blocks"
date: 2008-05-11
forum: General Help
---

### Post by DeVonne on 2008-05-11
Hello I was running 7.10 Ubuntu, and a tree fell on the powerline down the road and deprived my computer of power while it was running ubuntu

Well I booted back up and got to the screen where it fixes blocks ETC and then it complained about duplicate blocks and some stuff like that

went through some things and then said GDM could not start, so I hit ALT + F2 and logged in and shutdown -r now

Well I tried to boot again and the EXACT same thing happened

What happened? can I fix it without a format? can I save my files?
Someone help me I don't want to panic,

I don't like windows :(

Solved:: Read Below if you had the same problem

I let it go through the repair block screen after it scanned during boot, then it gave me my terminal, so I did fsck (drive)
and I held down Y to fix all the problems

and I used the shutdown command and booted right into ubuntu :D

---

### Post by frodon on 2008-05-12
If you want to avoid this in future there's some cheap ups systems for home computers, i have one at home (manufacturer is MGE) which even provide the associated software for linux. I have it working on ubuntu and it's working great.
[http://en.wikipedia.org/wiki/Uninterruptible_power_supply](http://en.wikipedia.org/wiki/Uninterruptible_power_supply)

---

### Post by DeVonne on 2008-05-15
Thank you frodon, I knew something like that existed but I did not know the name of it or any of the details,

---

