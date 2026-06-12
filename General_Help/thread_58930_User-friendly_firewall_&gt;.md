---
title: "User-friendly firewall :&gt;"
date: 2005-08-22
forum: General Help
---

### Post by Pikapooh on 2005-08-22
Is there any application-based firewall (probably just front-end for iptables ;-)) for Linux? What "application-based" means:
- firewall works in so-called "learning mode"
- when some application tries to connect to some host, popup is showed with some info (what app, what host, what port etc.) and the choice is given - allow or block (and advanced options like "allow this app to connect to host 111.111.111.11 on port 999")
- after choosing appropiate rule is created.

This is the way that Windows firewalls (ZoneAlarm, Kerio, Outpost Firewall) usually works.

I've tried Firestarter but it doesn't look that this firewall allow described customization.

---

### Post by Teren on 2005-08-22
[QUOTE=Pikapooh]Is there any application-based firewall (probably just front-end for iptables ;-)) for Linux? What "application-based" means:
- firewall works in so-called "learning mode"
- when some application tries to connect to some host, popup is showed with some info (what app, what host, what port etc.) and the choice is given - allow or block (and advanced options like "allow this app to connect to host 111.111.111.11 on port 999")
- after choosing appropiate rule is created.

This is the way that Windows firewalls (ZoneAlarm, Kerio, Outpost Firewall) usually works.

I've tried Firestarter but it doesn't look that this firewall allow described customization.[/QUOTE]
 You can try Firestarter.

---

### Post by hashimoto on 2005-08-22
Firestarter does allow customisation. To understand how it works, see: 
[http://www.fs-security.com/docs/policy.php#outbound](http://www.fs-security.com/docs/policy.php#outbound)

---

### Post by Pikapooh on 2005-08-24
I'm talking about per-application filtering. For example:

allow Opera to connect on port 80 to any host
disallow Mozilla to connect on port 80 to any host

AFAIK iptables can filter outgoing packets (only outgoing, sadly) using per-application rules. But I wasn't able to find apropiate options in Firestarter.

---

### Post by mort1 on 2005-08-24
Guarddog ? or easyfw ?

---

