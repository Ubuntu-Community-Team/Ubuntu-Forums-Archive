---
title: "Why is SSH -X so slow compared to VNC/NX/RDP?"
date: 2014-11-26
forum: General Help
---

### Post by vperaino on 2014-11-26
SSH with the -X option seems like a very convenient option for, say, tweaking the browser settings of a remote machine. But it's so unbelievably slow that it's literally unusable for anything except LAN, which I just cannot fathom why that is. 

At the moment I typically use XRDP through Remmina with SSH enabled to connect to remote machines out of state via reverse SSH tunneling. XRDP runs pretty great, but it would be so much easier just to hit the command line, pull up a shell, and start an SSH session so I can load only the utility that I need to adjust.

---

### Post by Lars Noodén on 2014-11-26
Have you tried adding -C for compression?  That will reduce the load on the net and will save time if the processors on both ends are up to it.

---

### Post by vperaino on 2014-11-26
I have and it doesn't seem to help by any noticeable margin.

---

### Post by spjackson on 2014-11-26
It could be worth trying ssh -Y instead of -X.

---

### Post by vperaino on 2014-11-26
Still slow as molasses, unfortunately.

---

### Post by kevdog on 2014-11-26
I'm not sure exactly why it's slow but I found out it just is. I never tunnel a desktop, but have some applications like gedit or Kate. Usually I just change things using vim from the terminal and I find that to be suitable. If I need something more full featured I used to run freenx but have since found X2go is probably what you want to do. I'm not a big fan of Vnc, also very slow

---

### Post by stever3 on 2014-11-26
I also found X2go to be the best solution.  Additionally, I installed Openbox to use exclusively with X2go - which resulted in a vast improvement over Unity.

---

### Post by linuxtips.org on 2014-12-18
X protocol can not use network bandwidth efficiently, it is designed for local networks.

But you can speedup ssh with compression option -C

It uses gzip compression, but as you can see speed of the connection still slow when compared to RDP.

You have to use Nomachine NX technology for a real desktop comfort. See also: [Why remote ssh is so slow]("http://www.linux-forums.org/t/remote-x-programs-started-through-ssh-is-so-slow/38")

---

