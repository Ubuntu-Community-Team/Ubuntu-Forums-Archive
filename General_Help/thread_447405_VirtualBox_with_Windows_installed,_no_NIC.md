---
title: "VirtualBox with Windows installed, no NIC?"
date: 2007-05-18
forum: General Help
---

### Post by SnowPunk98 on 2007-05-18
I just installed VirtualBox and installed Windows in a VM fine. When I log in there is a network adapter there but for some reason it doesn't work. I set up the network in VirtualBox to NAT, everything is basically default. Can anyone help me get the NIC working so I can keep Windows in Linux?

---

### Post by kyphi on 2007-05-18
You may find your answer here:

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

I run VirtualBox with XP on Ubuntu host just for one graphics programme.  I would not dream of giving XP access to the net.  I am aware that any malicious activity picked up would disappear on closing VB but have made it my longstanding policy that XP has no internet access.

---

### Post by mdurham on 2007-05-18
You should be able to access Linux from VBox providing you have a 'shared' directory. You can't access from Linux to VBox guest though.

---

### Post by SnowPunk98 on 2007-05-18
Well, I would agree about the no internet access for Windows from Linux. However for my work laptop its either use Windows in a VM with internet access or use Windows as my main OS with internet access...

---

### Post by armware on 2007-10-26
i had this problem, searched all damn week for a solution.
i got it solved, so here it is.

setup: 
kubuntu 7.10
virtual box 1.5.0_OSE (gutsy repo)
windows xp in virtualbox

details:
kubuntu has internet access
windows in vm doesn't

i looked at the virtual box log for the xp machine (virtualbox machine selector screen, Machine->Show Log). it showed it had setup the dns as 127.0.0.1 and ignored the other two i entered in (opendns).

solution:
give xp dns servers (connection properties, look it up)

result:
worked instantly. clicked 'close' on the dns screen, opened ie and there was the interwebs.

---

