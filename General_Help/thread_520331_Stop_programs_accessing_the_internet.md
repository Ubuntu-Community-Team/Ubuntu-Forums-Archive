---
title: "Stop programs accessing the internet"
date: 2007-08-08
forum: General Help
---

### Post by startling on 2007-08-08
On my Windows machine I used a firewall that notified me when an application was attempting to access the internet and then gave me the option of allowing or disallowing access. Is there anything in Ubuntu that will do the same job?

---

### Post by hikaricore on 2007-08-08
You could setup **firestarter** and configure your ports.

But why exactly would you need this?

There are very few applications short of an all-out rootkit that will maliciously access the internet when running Linux.

---

### Post by startling on 2007-08-08
I'm thinking of running some Windows apps under Wine and, from a privacy perspective at least, I wouldn't want applications to access the internet. I'm just being cautious, I suppose - I got used to the way the windows firewall alerted me. 

Is there a way to block outbound internet access for Wine and therefore any application that might be running under it?

---

### Post by hikaricore on 2007-08-08
> **startling said:**
> Is there a way to block outbound internet access for Wine and therefore any application that might be running under it?

There may be a way, but I sure don't know of it.  lol

---

### Post by Elle Stone on 2008-01-15
bump - maybe an iptables setting?  anyone know how to write an iptables line that would block wine (or any other given program)?  Is this even possible?  Windows programs are notorious for trying to phone home.  I've been turning off my router when I run wine, but that is cumbersome, to say the least.

Elle

---

### Post by startling on 2008-01-16
Hi Elle. I had forgotten about this thread! 

I was advised to look into [_Apparmor_,]("https://help.ubuntu.com/community/AppArmor") but I haven't had a chance to do so yet. If you try it please post your experiences.

---

### Post by Elle Stone on 2008-01-16
Hmm, I've looked into this issue several times over the last couple of months.

[http://liquidat.wordpress.com/2007/07/19/application-wise-network-filtering-on-linux/](http://liquidat.wordpress.com/2007/07/19/application-wise-network-filtering-on-linux/)
[http://www.usenet-forums.com/linux-networking/71474-forbid-internet-access-application-2.html](http://www.usenet-forums.com/linux-networking/71474-forbid-internet-access-application-2.html)
above links have discussions of problem but all proposed solutions seem flawed

[http://www.tresys.com/products/brickwall-standard.html](http://www.tresys.com/products/brickwall-standard.html)
seems to be redhat only and a bit of overkill.

[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)
seems to be no longer in development and not stable

I've never gotten a handle on exactly what firestarter does.

AppArmor, a simple how-to-block-a-specific-application would be nice.  I am afraid apparmor is over this newbie's head.

If you come up with anything, please share! and I will bookmark this thread, just in case I figure out something useful.

I am a bit confused as to why the average linux user isn't more concerned about privacy.  When I was using windows, my firewall was there more to let me know when programs tried to get OUT than it was to prevent stuff from getting IN, as I am behind a router.  A very high percentage of windows programs (not to mention malware) try to "phone home" on a regular basis.  I would assume that at least a few linux programs also "phone home".  And of course anything installed under wine is VERY likely to be phoning home.  

IPtables allows stuff initiated from the inside to "have its way" with the internet, as far as I know.  Great! if you have complete control over what is on one's computer.  But if "program X" wants to silently contact the mother ship - how do you know?  And when the day comes that someone writes a "bot-net" program for linux and cleverly gets people to  install it by offering a really nice bit of free software, well, an awful lot of linux users don't have any idea of what is going "out" of their machines, including this linux user, alas.

Elle

---

