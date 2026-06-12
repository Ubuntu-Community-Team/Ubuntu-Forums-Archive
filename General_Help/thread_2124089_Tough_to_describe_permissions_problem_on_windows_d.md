---
title: "Tough to describe permissions problem on windows domain"
date: 2013-03-09
forum: General Help
---

### Post by trivialpackets on 2013-03-09
So, this is the problem.  I have a freshly installed 12.10 on a dell laptop for work.  I am able to join the domain with no issues utilizing centrifydc.  Before rebooting, and before logging out, I make some changes to the sudoers file to allow particular users to have sudo power on the box.  

This works great.  The initial user I set up though at this point does not work.  But when I'm in the system in a gui, such as adding a network connection and I try to make a change that requires me to provide the password, it's still prompting for that specific user's (by name) password, which no longer works.  I can work around this by starting the gui from the command line, but I would much rather solve this.

---

### Post by trivialpackets on 2013-03-09
Also, when I downloaded the tgz from Centrify, after unpacking, should I be installing all of the files using install.sh?  Now I'm curious if that could possibly solve the problem, but haven't done so yet.

---

