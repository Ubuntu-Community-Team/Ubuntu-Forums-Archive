---
title: "init.d scripts question - seeme not to work"
date: 2008-05-15
forum: General Help
---

### Post by jambalaya on 2008-05-15
Hi everyone.
I wanted to check the init.d and runlevels thing. So, I created a /etc/init.d/killnet.sh script, which has this:

#!/bin/sh
ifconfig eth0 down

I created a symlink in the /etc/rcS.d directory:
ln -s /etc/init.d/killnet.sh /etc/rcS.d/S99killnet.sh

So this would invoke this script when the machine boots (and take down my eth0) as the last one (there are no others with S99 prefix), at least that's what I read. However, when I login (to KDE desktop), the network is just fine. I also tried putting the link in /etc/rc2.d, since this is the default runlevel. I know the scripts should have start, stop and similar parameters, but I think this is not necessary here.
(Please don't judge the question on the fuctionality of this script, it is just a test to learn how to do it.)
So, the question is, what am I missing here? Or is it the avahi-daemon that brings the interface up or something? Or maybe I'm just doing something completely wrong?
Also, the Debian Policy Manual states that the first line has to be #!/bin/sh, is that really true? Can't I use bash or other?
Thank you.

---

### Post by chrisccoulson on 2008-05-15
It is probably most likely being brought back up my Network Manager. If you want the behaviour you describe, then you probably need to add eth0 to /etc/network/interfaces

---

### Post by kevdog on 2008-05-15
Either rc4 or rc5 is the default run level.  I would just do a similar entry in both of these folders.

---

### Post by chrisccoulson on 2008-05-15
> **kevdog said:**
> Either rc4 or rc5 is the default run level.  I would just do a similar entry in both of these folders.

Actually, rc2.d is the default runlevel in Ubuntu and other Debian based systems. rc4/5 is default for Red Hat systems I think

---

### Post by kevdog on 2008-05-15
No that isn't entirely true --

> For example, runlevel 2 is the default runlevel for Debian in non-GUI mode

Multiuser or GUI mode is runlevel 3-5.

---

### Post by chrisccoulson on 2008-05-15
Yes, but Ubuntu's default multi-user GUI mode is runlevel 2. 1 is single user. 3, 4 and 5 aren't really used by default

---

### Post by chrisccoulson on 2008-05-15
In fact, according to [this]("http://www.debianhelp.co.uk/runlevels.htm"), run-levels 2, 3, 4 and 5 are full multi-user in Debian, and 1 is single user - which is exactly the same as Ubuntu

---

### Post by jambalaya on 2008-05-15
When I log in to KDE, run Konsole and issue "sudo runlevel" i get N 2, which mean that it started with runlevel 2, since the N stands for the previous one, and it is not set. So at least for my system, 2 is the default.
What do you mean by "add eth0 to /etc/network/interfaces"?
Thanks.

---

### Post by chrisccoulson on 2008-05-15
If you have something like:
```
auto eth0
iface eth0 inet dhcp
```
..in /etc/network/interfaces, it will cause eth0 to be brought up with DHCP by the runlevel scripts, and will allow you to control the interface with ifup/ifdown/ifconfig, but I don't know if it is sufficient to stop Network Manager from trying to control it as well.

However, if you remove the 'auto eth0' line, the interface won't be brought up by the run-level scripts and would remove the need for your extra script to bring it down.

---

### Post by jambalaya on 2008-05-15
Thanks for the exmplanation.
And now is mine - I don't really need to take ehh0 down, I simply want to see how one creates init scripts and make it work, bringing the net down was just an idea of what such a thing could do. It is also pretty easy to check if this worked or not.
What about my #!/bin/sh question? Are the scripts really limited to this shell?
Thanks.

---

