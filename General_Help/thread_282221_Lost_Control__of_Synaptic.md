---
title: "Lost Control  of Synaptic"
date: 2006-10-22
forum: General Help
---

### Post by WorkingOnGoingLinux on 2006-10-22
Ive lost control of synaptic on my notebook. This is the second time this has happened. The first time I just re-installed ubuntu. I must be doing something wrong since I'm in the same place again.

If I try to use synaptic,update manager, change my network settings or make any changes for that matter the curser just spins then stops. Nothing happens the program never starts.   Any suggestions how to fix this or what I did wrong ? Thanks

---

### Post by DarkN00b on 2006-10-22
Try running 'sudo synaptic' from a terminal window. Any errors or problems should show up there.

---

### Post by WorkingOnGoingLinux on 2006-10-22
Thanks Darknoob

This is the reply I get back from that command.

skip@:~$ sudo synaptic
sudo: unable to lookup  via gethostbyname()
skip@:~$ sudo synaptic
sudo: unable to lookup  via gethostbyname()
skip@:~$

---

### Post by djf on 2006-10-22
gethostbyname() is a function that retrieves the IP address of a given domain name. Is DNS working properly where you are? E.g. can you browse the internet?

Normally you should have at least one nameserver entry in /etc/resolv.conf, these should also be listed under System->Administration->Networking. Under the DNS tab.

---

### Post by WorkingOnGoingLinux on 2006-10-22
I can't get networking to work. When I click on it I just get timed out.
Yes I can connect to the net via wireless or wired connection. It's almost like all my admin privledges have been removed.

---

