---
title: "Ports on iptables"
date: 2006-10-24
forum: General Help
---

### Post by Coruba67 on 2006-10-24
Hi guys

Have setup ubuntu on a machine and am trying to SSH into it... however I keep getting a connection refused error.  SO after trawling thru these forums I installed firestarter.  I have setup port 22 - SSH - to allow for everyone.

I am now still though getting a connection refused.  SO I restarted the server still connection refused even though Firestarter is telling me its all ok!

Any idea's?

---

### Post by matthewstory on 2006-10-24
this isn't an iptables issue, if iptables was blocking on port 22, then you wouldn' get a connection refused error, you would get a connection timed out error.  If it is an iptables issue however this should do the trick:

iptables -A INPUT -p tcp --dport 22 -j ACCEPT

Note that you will have to run this every time you start the system, but you could script it in /etc/init.d, there are many good howtos on this subject out there.

---

### Post by matthewstory on 2006-10-24
should also note that the ssh daemon is not automatically installed on Ubuntu, only the ssh client, to install ssh in ubuntu:

sudo aptitude install ssh

Then to make sure it's running:

ps aux | grep sshd

should do the trick if the ssh daemon isn't installed.

---

