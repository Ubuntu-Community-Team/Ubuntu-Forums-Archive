---
title: "Viruses and Spyware"
date: 2005-10-16
forum: General Help
---

### Post by Zad_ok on 2005-10-16
One of the major reasons for using Linux over Windows is that viruses and spyware are far less troublesome. I never heard of Linux spyware, and never come across a Linux virus myself. Anyone else had virus or spyware on their Linux box?

PS Someone stated that unless you are running as root viruses cannot do much damage. Anyone care to comment on that?

---

### Post by Hikaru79 on 2005-10-16
[QUOTE=Zad_ok]One of the major reasons for using Linux over Windows is that viruses and spyware are far less troublesome. I never heard of Linux spyware, and never come across a Linux virus myself. Anyone else had virus or spyware on their Linux box?

PS Someone stated that unless you are running as root viruses cannot do much damage. Anyone care to comment on that?[/QUOTE]
It is a MYTH that viruses do not exist for Linux. They do. In fact, the first viruses in the world were for UNIX-based systems. However, they are much less of a problem nowadays than they are for Windows for two reasons

A) Linux is built with security in mind. The open-ness makes it much easier to find and fix bugs.
B) It's not as much of a target, because of its lower market share.

You'll definitely have fewer problems on Linux. But that doesn't mean that you're invincible, just keep that in mind.

As for not being able to do as much damage without root, that is true. Which is why Ubuntu doesn't even enable root by default.

---

### Post by Pontux on 2005-11-09
What about worms like Lupper?

[http://www.wormblog.com/2005/11/new_worm_lupper.html](http://www.wormblog.com/2005/11/new_worm_lupper.html)

Any AV ideas for Hoary and Breezy?

---

### Post by bionnaki on 2005-11-09
sudo apt-get install chkrootkit

& 

then periodically run

sudo chkrootkit

---

### Post by nocturn on 2005-11-09
[QUOTE=Pontux]What about worms like Lupper?

[http://www.wormblog.com/2005/11/new_worm_lupper.html](http://www.wormblog.com/2005/11/new_worm_lupper.html)

Any AV ideas for Hoary and Breezy?[/QUOTE]


There is and has always been malware for Unix/Linux, but the scope and impact are different.

1#  There are about next to no desktop-infecting virusses for Linux out there.
2#  Inspite Linux/Unix/*BSD dominating the server market forever, there are very few worms that succesfully attack them (compare this to IIS, which has only a small market share).
3#  Even when Worms pop up for Linux, their spread and impact are low.
Lupper may be able to infect vulnerable PHP enabled sites, but should only compromise the Apache user (not root), limiting the impact.
Malware targetting Linux/Unix often only works against a limited number of distribution, variety is a good thing in defense.
4#  Installing a server with /tmp on a seperate partition and making it nosuid, noexec and sticky breaks most malware with little to no impact to your system.

---

### Post by kagashe on 2005-11-10
[QUOTE=Pontux]What about worms like Lupper?

[http://www.wormblog.com/2005/11/new_worm_lupper.html](http://www.wormblog.com/2005/11/new_worm_lupper.html)

Any AV ideas for Hoary and Breezy?[/QUOTE]Read this [article]("http://www.eweek.com/article2/0,1895,1884318,00.asp") it says > First, none of the trio of vulnerabilities in the luppi worm actually have a thing to do with Linux. Yes, these worms target Linux systems, but the holes they use to target aren't Linux holes at all. They're Web service script holes.

Saying that this is a Linux problem is like saying that the gaping Macromedia Flash hole is an XP problem.kagashe

---

### Post by zekolas on 2005-11-10
Well there have been a few virus for linux, but I have only heard of two that actually infected machines in the so called "wild". Also to be infected by these virus you needed to be running an older kernel and also running apache with some special services enabled. So even the machines these virus could infect was very limited. If you don't run server software and keep your system reasonable up to date you don't have anything to worry about.

---

