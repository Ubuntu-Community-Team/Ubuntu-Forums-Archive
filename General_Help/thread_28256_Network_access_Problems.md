---
title: "Network access Problems"
date: 2005-04-19
forum: General Help
---

### Post by wingnut on 2005-04-19
please help a noob! I  have installed ubuntu and kind of have things running. I am unable to connect to most web sites. I can connect to ubuntu and google but nothing else. (like yahoo or earthlink.) I also cannot run apt-get update successfully. I get an error back about not being able to connect...I can browse my local xp shares. Any suggestions for missing settings would be appreciated.
Thanks in advance.

---

### Post by jbharrison on 2005-04-19
check /etc/resolv.conf

Make sure that the 'nameserver' is set correctly.
Test with:

nslookup [www.yahoo.com](www.yahoo.com)

---

### Post by siebzehn on 2005-04-19
It's probable your problem is the MTU size in your NIC (Ethernet card).

Try this, open a terminal and type "sudo eth0 mtu 1492"  (without the quotes).

---

### Post by Nob on 2005-04-19
[QUOTE=jbharrison]check /etc/resolv.conf

Make sure that the 'nameserver' is set correctly.
Test with:

nslookup [www.yahoo.com](www.yahoo.com)[/QUOTE]
 ok, what exactly should be in resolv.conf?
i have the same problem... :)

---

### Post by heimo on 2005-04-19
[QUOTE=siebzehn]It's probable your problem is the MTU size in your NIC (Ethernet card).

Try this, open a terminal and type "sudo eth0 mtu 1492"  (without the quotes).[/QUOTE]

Let me correct. sudo /sbin/ifconfig eth0 mtu 1492

resolv.conf should have your ISPs DNS servers (if you're using DHCP, these may be already configured). There should be at least one line like this:
 ```
nameserver 12.12.12.12
``` 
substitute 12.12.12.12 with correct ip address

---

### Post by siebzehn on 2005-04-19
[QUOTE=heimo]Let me correct. sudo /sbin/ifconfig eth0 mtu 1492

[/QUOTE]

You don't need to type  /sbin/ifconfig

sudo ifconfig eth0 mtu 1492   will work just fine, give it a try ;)

---

### Post by heimo on 2005-04-19
[QUOTE=siebzehn]
Try this, open a terminal and type "sudo eth0 mtu 1492"  (without the quotes).[/QUOTE]

You were missing the whole ifconfig.

---

### Post by siebzehn on 2005-04-19
[QUOTE=heimo]You were missing the whole ifconfig.[/QUOTE]
 You're absolutely right

---

### Post by wingnut on 2005-04-19
thanks for the response! Things are now working! Needed to modify my /etc/resolv.conf

---

