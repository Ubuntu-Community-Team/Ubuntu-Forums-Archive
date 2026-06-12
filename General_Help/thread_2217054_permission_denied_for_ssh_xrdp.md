---
title: "permission denied for ssh xrdp"
date: 2014-04-15
forum: General Help
---

### Post by johnycage on 2014-04-15
Ubuntu 12.04 LTS alternative CD for LTSP setup. 
This is very common error message. I'm not able to access the VM via SSH. upon entering the ip address and username it doesnt accept my password & throwing 
"permission denied" message. I cannot access it via xRDP too.
I tried to login via PuTTy, other Ubuntu ssh, or windows RDC etc. but no success. I know my userid & password is OK, as I use the same to access the machine directly (via hyper-v). Other ubuntu VMs runs OK & can be accessed via SSH. 
I've checked /var/log/auth.log file & it shows that its incorrect/invalid username. 

sudo adduser new1
& Now I can ssh using new1 credentials (but it doesn't have sudo powers)
What I need to do in order to all ssh for my primary user?

---

### Post by johnycage on 2014-04-17
anyone?
Thank you.

---

### Post by johnycage on 2014-08-17
> **johnycage said:**
> anyone?
Thank you.

There was a spelling mistake in my username. Sorry for the trouble. 
Where is the delete thread button :(

---

