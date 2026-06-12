---
title: "please help: sharing cached packages??"
date: 2006-07-29
forum: General Help
---

### Post by ProjectGod on 2006-07-29
hiya
lets say i've got a few ubuntu computers on a network. they're not top notch machines and therefore i'd like to install breezy on them. and perhaps keep them upto date without upgrading to dapper. 

anyway. i would like to download all the updates/ upgrades on ONE machine using

aptitude update
aptitude upgrade

and then use the cached packages on that machine to also update / upgrade other machines that have ubuntu breezy installed.

is this possible??? i rather not wish to download 160 MB for each machine. 

many thanks.

---

### Post by eyequeue on 2006-07-29
_One possible method:_

They will all have identical packages installed on them?  If not, pick the machine with the most packages, and call that the "master" machine for now, since it will have the most .debs in the cache.


On that master machine, /var/cache/apt/archives/ will contain all the downloaded .debs.  (You can run *apt-get -d upgrade*, or similar, if you just want to d/l.  You can even do this via cron job if you prefer.)

On the master machine, NFS export that directory to your LAN netblock.  On the other machines, NFS import that directory, mounted to /var/cache/apt/archives/.  It will be **as if** you already ran *apt-get -d upgrade* on each of the machines, and now all you need to do is remove the -d switch, and run *apt-get upgrade* on each machine, to actually install the updated packages, after of course running *apt-get update* to make that machine aware of the currently available packages.

To review, *apt-get update && apt-get -d upgrade* on the "master" machine.  Followed by *apt-get update && apt-get upgrade* on all machines.

---

### Post by ProjectGod on 2006-07-29
hmmmm just might work! :)

i'll come and annoy you if it doesnt :twisted: :D

---

### Post by Beamerboy on 2006-07-29
I was thinking of a similar but slightly different method.  Use your cached debs to form you own repository on the main machine (I don't know how to do this but there must be plenty of documentation on it).  Then set your sources.list on the "slave" machine to only contain your home grown repo and no others.

---

