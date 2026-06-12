---
title: "Using Firefox fromthe live CD"
date: 2007-02-05
forum: General Help
---

### Post by rainwalker on 2007-02-05
My high school uses only Windows computers and only IE, so I wanted to use run Firefox from a live CD (to have the best of both worlds, OS and browser), but FF can never find the server. In System -> Administration -> Networking it says the DHCP connection is already configured, but I still can't access the internet. I would just go ahead and install Ubuntu, but I doubt they'd want me to do that. Any suggestions?

---

### Post by etank on 2007-02-05
Try to open a terminal and run 
```
ifconfig
```
Do you get an IP. Could your school be using static IPs only?

You could also check with the school to see if it would be OK to install Firefox onto the Windows machine.

---

### Post by Ryan450 on 2007-02-05
pull up a terminal and type in ifconfig

then check under eth0 to see if your getting and ip. if not you can try 

sudo dhclient eth0 and see if you get a dhcp offer.

Keep in mind that in a school setting most admins set up domain controllers to control thier network. you could just very well be getting blocked.

---

### Post by rainwalker on 2007-02-05
I have installed FF on the school boxes, I just wanted to see what you could do from the live CD (like if the blocks still applied and stuff like that)

---

### Post by Hendrixski on 2007-02-05
Some places turn off DHCP.

Also, tell your school you want to have Linux computers.  Start a Linux club or something and have them turn over a computer or two over to Ubuntu.  Linux runs on something like 60% of the server market, and if you want to have a career in computers it may be helpful to know.  I Work as a consultant and I use Linux at work, and I make more money than your principle does.

Also show off Edubuntu to the elementary school teachers.  It's PACKED with tons of great educational software, and it's completely virus free (as is all of Linux).  It's a great tool.  Also show your principle the "One laptop per child" program.  It aims to give Linux laptops to students in poor parts of the world (like West Virginia, or Uganda) so that they can become the technology force of tomorrow.  The French government is planning on migrating its computer systems to Linux.

:) I'm sure that if you explain the open source philosophy (that all software should be free as in free speech) they will really like it.  It prevents vendor lock-in, promotes educational use of the software, and allows everyone to be an owner.  It's kind of like Wikipedia.  Some of it is even free of charge (not all, but Ubuntu is).  Don't take no for an answer, make them install Linux at your school!

---

