---
title: "Installing software in other partition"
date: 2013-11-03
forum: General Help
---

### Post by courtney2 on 2013-11-03
Hey guys! So this is getting really frustrating, and I've spent hours searching but there is no answer. I want to install my software outside of my /root partition. My /root is limited to 20GB, not nearly enough for what I plan to install. I have a 20GB /root, 4GB /swap and 400GB /home partition. There are applications and games in the software center that I wish to install, as well as Steam and some of those games. That just means that this space will be eaten up FAST. Is there any way I can install all of this in a different partition like my /home partition or some other partition that I could make?

---

### Post by Mark Phelps on 2013-11-03
Basically -- no.  Software is best installed using .debs -- and they decide where, in the filesystem, the different components are stored.  If you try to mess around with that, you'll only end up hosing up the installations, and then the apps won't run.

---

### Post by CatKiller on 2013-11-03
It's unlikely that you have a partition for /root. Do you mean /?

The only sensible way to achieve what you're after is to use something like GParted to shrink your /home and increase the size of /.

---

### Post by Impavidus on 2013-11-04
You have a / partition also known as root partition. There is no /root partition, as the /root directory has to be on the / partition. Also there is no /swap partition. It's just known as swap partition, because it's not mounted at /swap.

That aside, the best way to solve your problem is by enlarging the / partition and shrinking the /home partition.

There are some alternative hacks available too. Assuming those games store their data in, for example, /usr/share/games/, you could make a separate partition for that. Not really worth the effort, unless you know the data stored there is independent of your Ubuntu version, manually installed and so large that you don't want to redownload it when you reinstall. I made a separate partition for /usr/local/ for that reason, containing manually installed flightgear data and manually installed latex packages and tools (scripts).

---

### Post by philinux on 2013-11-04
> **courtney2 said:**
> Hey guys! So this is getting really frustrating, and I've spent hours searching but there is no answer. I want to install my software outside of my /root partition. My /root is limited to 20GB, not nearly enough for what I plan to install. I have a 20GB /root, 4GB /swap and 400GB /home partition. There are applications and games in the software center that I wish to install, as well as Steam and some of those games. That just means that this space will be eaten up FAST. Is there any way I can install all of this in a different partition like my /home partition or some other partition that I could make?

I have three installs all with a root partition of 10 gig. Never hit the limit yet. One thing that can cause a problem is old kernels building up. It easy to clean that up though.

---

