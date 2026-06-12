---
title: "Firestarter Firewall"
date: 2005-10-27
forum: General Help
---

### Post by ManongTenchi on 2005-10-27
I've read many posts that claim that Breezy is in stealth right from the start, and I've tested and proved that myself on Shields Up! and all. I'm just a newbie, but I'm just wondering what a firewall in Linux actually does.

Note that this due to the fact that I'm not overly aware of everything a firewall does to begin with.

---

### Post by Emerzen on 2005-10-28
My understanding is that a firewall is essential for any box w/ a broadband connection.  Stealth is helpful but, I believe, a firewall is an extra layer of security to make sure your box doesn't get hacked.  I use Firestarter myself and found it easy to configure, and have had no problem w/ it any any programs that access the internet.

---

### Post by dhpeterson on 2005-10-28
[QUOTE=ManongTenchi]I've read many posts that claim that Breezy is in stealth right from the start, and I've tested and proved that myself on Shields Up! and all. I'm just a newbie, but I'm just wondering what a firewall in Linux actually does.

Note that this due to the fact that I'm not overly aware of everything a firewall does to begin with.[/QUOTE]

Hi ManongTenchi,

A firewall in Linux does the same thing (conceptually-speaking) as a firewall on any other platform ... it filters incoming and outgoing packets according to a set of rules (sometimes called "policies") which you, the firewall administrator, set.

Since the 2.4 kernel the firewall implementation used in Linux is called "iptables" (or netfilter). You can try "man iptables" on the command line to see its syntax (can be a bit complex for a new user), or you can read the "netfilter howto" (by the netfilter author Rusty Russell) which should be present in your /usr/share/doc tree. 

A well-secured box (i.e patched up-to-date, not running unnessessary services etc) is a starting point, but if your machine is directly connected to the internet (e.g. via DSL) then you really should think about setting a default set of firewall rules.

HTH

Dave

---

### Post by ManongTenchi on 2005-10-28
Thanks for the informative replies. I was going back and forth on whether to install a firewall, so I think I'll go ahead and give it a shot for safety's sake.

---

