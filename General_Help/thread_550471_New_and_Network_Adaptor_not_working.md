---
title: "New and Network Adaptor not working"
date: 2007-09-13
forum: General Help
---

### Post by Vagabond102 on 2007-09-13
Hello,

I'm very new to Ubuntu and linux.  My last experience was with Slaskware 8.0 about 10 years or so ago.  I did use openBSD in a bash shell for work purposes so I am semi familiar with the idea and structure.

I have 7.04

How do I actually shut down X to get to a true commandline interface?

Also, the first think I need to do is get the nic up and running.  It's a Realtek RTL8168/8111 PCIE-E according to XP.  It will not DHCP an address from my router and the router does not show a request. I think the lights on the (nic) port do not light up and the router doesn't show a connection.  I looked in Hardware and it sees the NIC (Though not much else).  What do I need to provide for assistance?  I've read my brains out tonight and nothing seems to be what I need. 

Keep in mind this is a fresh install, I have done nothing but look through some of the options and menus.  I only have the one box dual booting XP.  Also I wasn't sure if this was the forum, but looking at the others, none seemed appropriate, I'll gladly move to the appropriate one if I am incorrect.

Thank you

---

### Post by dcstar on 2007-09-14
> **Vagabond102 said:**
> Hello,

I'm very new to Ubuntu and linux.  My last experience was with Slaskware 8.0 about 10 years or so ago.  I did use openBSD in a bash shell for work purposes so I am semi familiar with the idea and structure.

I have 7.04

How do I actually shut down X to get to a true commandline interface?

Also, the first think I need to do is get the nic up and running.  It's a Realtek RTL8168/8111 PCIE-E according to XP.  It will not DHCP an address from my router and the router does not show a request. I think the lights on the (nic) port do not light up and the router doesn't show a connection.  I looked in Hardware and it sees the NIC (Though not much else).  What do I need to provide for assistance?  I've read my brains out tonight and nothing seems to be what I need. 

Keep in mind this is a fresh install, I have done nothing but look through some of the options and menus.  I only have the one box dual booting XP.  Also I wasn't sure if this was the forum, but looking at the others, none seemed appropriate, I'll gladly move to the appropriate one if I am incorrect.

Thank you

CTRL-ALT-F1 will get you a text terminal login.

```
sudo lshw
sudo lspci
``` will list all of your detected hardware (use your own password).

---

### Post by Vagabond102 on 2007-09-14
Thank you for your response!

I ran the commands suggested, got the output, and looks well, but still the port appears dead.  I read how to force it up and all to no avail.

I need to research more, as I can't seem to get write access to my windows drive so I can save a document there so I can relay it here.

EDIT: 

It didn't appear that getting the console as shown helped me do what I need.  Evidently X is still running in the background.

---

### Post by Vagabond102 on 2007-09-15
I found the problem.  With these Realtek 8111B nics, and you dual boot XP, need to configure the adapter to wake on lan after shutdown.

Evidently windows shuts down the port and Ubuntu doesn't know how to bring it back up.  This fixed my issue.

---

