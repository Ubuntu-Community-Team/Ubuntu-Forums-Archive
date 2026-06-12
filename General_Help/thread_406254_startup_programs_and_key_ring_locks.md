---
title: "startup programs and key ring locks"
date: 2007-04-10
forum: General Help
---

### Post by Drate on 2007-04-10
How do I add a program to startup... like... say... fire starter?

Also, how do I make it so I don't have to type my password (when I log on and Network Manager starts) everytime I start the computer?  I just want it to startup and log on... internet ready to go.

---

### Post by josephus on 2007-04-11
Go into System->Preferences->Session to add startup programs.

I don't have any experience with network manager as I don't use it myself, but this link seems promising:

[http://ubuntuforums.org/showthread.php?t=316927](http://ubuntuforums.org/showthread.php?t=316927)

---

### Post by spankymasterc on 2007-04-11
man that guide was to much hassle look at this one its a .deb so its easy 

[http://ubuntuforums.org/showthread.php?t=192281&highlight=network+manager](http://ubuntuforums.org/showthread.php?t=192281&highlight=network+manager)

it worked for me just read on if it doesnt work .....

---

### Post by Drate on 2007-04-11
well thanks yall!  my machine works great now with the whole internet bit... but one problem, my dad's machine (the one running firestarter), when I added firestarter to the startup programs it complains it needs root priviledges. I've tried putting the user account in the root group, ive tried changing the ownership of firestarter to the user that is needing to do it... both with no effect.... how to i get the dern thing to just START!

Dad suggested a script... but it would have to be a script that put in the sudoers password at the appropriate time... so..... how does one begin this? or is there a better way?

---

### Post by Drate on 2007-04-12
Bump

---

### Post by josephus on 2007-04-12
There are a couple of posts on this forum that addresses the issue, as well as the the Firestarter FAQ:
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

But according to this post that method might not work:
[http://ubuntuforums.org/showthread.php?t=238505](http://ubuntuforums.org/showthread.php?t=238505)

Anyways, your firewall is controlled by iptables, as is running even when the Firestarter gui is not loaded, so this whole process may not be necessary (depending on your objective).

---

