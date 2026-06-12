---
title: "about firewall in ubuntu"
date: 2005-04-14
forum: General Help
---

### Post by pranith on 2005-04-14
hi,
I some where saw that ubuntu doesnt have ne kind of firewall installed by default.
Is it necessary that we should install them.Why should we install firewall. ne way linux doesnot have ne virus right.Plz somebody explain.

Is there ne virus in linux too?????????

---

### Post by Nano on 2005-04-14
[QUOTE=pranith]hi,
I some where saw that ubuntu doesnt have ne kind of firewall installed by default.
Is it necessary that we should install them.Why should we install firewall. ne way linux doesnot have ne virus right.Plz somebody explain.

Is there ne virus in linux too?????????[/QUOTE]
 There are many threads about this. If you use the search function you will find much info.
However, there is a "built-in" firewall called iptables in your system and a program you can install which is a GUI that helps you to manage graphically iptables called Firestarter.

---

### Post by XDevHald on 2005-04-14
Linux does not get virus's, spyware or anythingrelated to windows. Linux does however get bugs and which you can get fixed very easily with the knowledge you might have in linux.

Now as far as a firewall, you can easily install one, which I would recommend "FireStarter". Great application, fast, easy to use and you can just have it hiding in the background of your desktop without even seeing it. Which is what I find to be very useful for saving space on my taskbar. :)

If you want this application, type as root:  [b]
apt-get install firestarter [/b]
then [b]
apt-get upgrade [/b]which will do the rest for you :)

---

### Post by az on 2005-04-14
A firewall is something that prevents your computer from communicating with the outside.  If there is nothing that is installed that communicates with the outside (no open ports) you do not need a firewall.

Usually, the first thing you do when you install a firewall is punch holes in it for the applications that need to talk to the outside (open ports)

Ubuntu does not include anything which listens to the outside world by default.  If you install a package that does, it is assumed that you know what are the risk.

Insofar as viruses and worms, Windows is like a rotting peice of flesh.  There is a lot there to attract viruses.  Unix systems are like a clean piece of plastic -  nothing there to make them grow.

---

### Post by segrewb on 2005-04-14
Good description of windoze!

---

### Post by XDevHald on 2005-04-14
[QUOTE=azz]Insofar as viruses and worms, Windows is like a rotting peice of flesh. There is a lot there to attract viruses. Unix systems are like a clean piece of plastic - nothing there to make them grow.[/QUOTE]

lmao, that is the BEST description about the two OS's I have ever seen hehe, nicely said azz.

---

### Post by Nano on 2005-04-14
[QUOTE=azz]A firewall is something that prevents your computer from communicating with the outside.  If there is nothing that is installed that communicates with the outside (no open ports) you do not need a firewall.

Usually, the first thing you do when you install a firewall is punch holes in it for the applications that need to talk to the outside (open ports)

Ubuntu does not include anything which listens to the outside world by default.  If you install a package that does, it is assumed that you know what are the risk.

Insofar as viruses and worms, Windows is like a rotting peice of flesh.  There is a lot there to attract viruses.  Unix systems are like a clean piece of plastic -  nothing there to make them grow.[/QUOTE]
 It is not 100% right. It comes with Gnome Bittorrent and you need to open the port 6881 in order to make it work properly.

---

