---
title: "UFW help, not blocking IP addresses."
date: 2014-11-24
forum: General Help
---

### Post by oliver18 on 2014-11-24
Hi,

I'm using UFW and trying to block some IP addresses. Below is the rule set I have but it seems that the IP's listed are still able to access open ports. What do I need to do to make sure the IP's cannot access the server at all?


Ubuntu 12.04 LTS
Status: active


     To                         Action      From
     --                         ------      ----
[ 1] Anywhere                   DENY IN x.x.x.x
[ 2] Anywhere                   DENY IN x.x.x.x
[ 3] Anywhere                   DENY IN x.x.x.x
[ 4] Anywhere                   DENY IN x.x.x.x
[ 5] Anywhere                   DENY IN x.x.x.x
[ 6] Anywhere                   DENY IN x.x.x.x
[ 7] Anywhere                   DENY IN x.x.x.x
[ 8] Anywhere                   DENY IN x.x.x.x
[ 9] Anywhere                   DENY IN x.x.x.x
[10] Anywhere                   DENY IN x.x.x.x
[11] Anywhere                   DENY IN     x.x.x.x
[12] 5555/tcp                   ALLOW IN    Anywhere
[13] 80/tcp                     ALLOW IN    Anywhere
[14] 25/tcp                     ALLOW IN    Anywhere
[15] 10050/tcp                  ALLOW IN    Anywhere
[16] 2222/tcp                   ALLOW IN    Anywhere
[17] 143/tcp                    ALLOW IN    Anywhere
[18] 110/tcp                    ALLOW IN    Anywhere
[19] 21/tcp                     ALLOW IN    Anywhere

Thanks

---

### Post by oliver18 on 2014-11-25
Anyone?

---

### Post by Lars Noodén on 2014-11-25
One way you can see the exact rules that IPTables is using with [iptables-save](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-save.8.html)

```

sudo iptables-save | less

```

Then step through the INPUT chain one line at a time, following to another target chain (and back again) if necessary.  It will jump to the chain 'ufw-user-input' from the 'ufw-before-input' chain and there you can see the settings you added to UFW.  It's complicated until you know what to look at and what to ignore, but if you post the output here, we can walk you through it.  It's just a sequence of yes/no decisions.

---

