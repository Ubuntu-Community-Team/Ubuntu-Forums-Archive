---
title: "Xine Stumper"
date: 2005-04-27
forum: General Help
---

### Post by uberlinux on 2005-04-27
So, when I have a network connection , not just interface up, but dhcp'd as well, XINE and Kaffiene work fine, but if i try to open XINE or play a dvd on kaffiene with the network not established, the programs dissapear and shut off without a warning...odd isnt it?

---

### Post by ape on 2005-04-27
I've noticed that in the strace output from xine, it is looking at the /etc/nsswitch.conf file for some reason.  What does this file look like?  It may be that some sort of name resolution isn't working properly.  Is your hostname properly configured to return your machines hostname?

---

