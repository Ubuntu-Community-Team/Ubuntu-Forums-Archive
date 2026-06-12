---
title: "Unable to Connect to the Internet"
date: 2008-04-26
forum: General Help
---

### Post by daleeburg on 2008-04-26
I am brand new to Ubuntu and have almost no Linux experience under my belt, so if you tell me to do something please take me step by step though it.  Assume I know nothing.

I am running Ubuntu in a VM.  As I said, I have almost no Linux experience and am not quite ready to give up everything I know and jump in head first.

I downloaded heron and the install went fine.  Now when i try to connect to any website in firefox I can not.  In the bottom bar it states 'Connecting to [website name]' but nothing more happens.

Add/Remove programs does not work.  I can not add any programs, it just hangs at the downloading part.

If I attempt to sudo apt-get install (program) I get to the point where it should start downloading the program, but it does not.

I am able to go in terminal and ping [www.google.com](www.google.com) with replies, but I am not able to ping [www.woot.com](www.woot.com).  On woot.com it resolves an IP, but doesn't go any farther, just locks up.

Here is what I have tried from my own searching:
-Attempted to disable IPv6 in /etc/modprobe.d/alises (comment out the pf-10 line, add a pf-10 off, IPv6 off and pf-10 IPv6 off)
-Attempted to black list IPv6 in /etc/modprobe.d/blacklist (add line blacklist ipv6)
-Turn off IPv6 in Firefox (about:config - network.dns.disableipv6 true)

All of my other Vms work (a windows vm, reaction Os vm) and I do not have any firewalls on the VM connections.

Does anybody have any Ideas?

Thanks
~D

---

### Post by bsmanian on 2008-04-26
Do The Following.Open the terminal.sudo gedit /etc/dhcp3/dhclient.conf
and when the file opens Edit the line beginning with #prepend domain- name-servers 127.0.0.1 as follows.
prepend domain-name-servers 208.67.220.220,208.67.222.222,127.0.0.1;
and save the file.Restart the computer and internet should work.Please note to uncomment this line and don't forget the commas to separate the IP Addresses and the semicolon in the End.Wish you happy surfing.

---

### Post by daleeburg on 2008-04-26
I attempted the fix you posted and it seems as though it has not fixed the problem.  All the same symptoms still apply.

---

### Post by daleeburg on 2008-04-26
Ok sorry to bother you guys, It was a VM problem.  I needed to drop VM into bridge mode rather then Nat mode.

Sorry
~D

---

