---
title: "Evolution &amp; Exchange 2003 -&gt; What am I doing wrong?"
date: 2006-11-08
forum: General Help
---

### Post by killerfish on 2006-11-08
Ok, I'm not sure if I'm doing something wrong, evo-connector is borked, or our work's server settings are borked.. I'm trying to connect to our works Exchange 2003 server with Evolution.

In the Exchange Configuration I put:
Username: domain/username
OWA URL : [http://server1.mywork.com](http://server1.mywork.com)

When I click authenticate, I get no errors.  Then, when I leave preferences and try to download mail, I get prompted for another password to another server on my work's domain (ie, server2.mywork.com)..  I put in my password and it never authenticates saying I'm entering an incorrect password or account not found on server. Net, I'm stuck!  

BTW, I can it the web url just fine: [http://server1.mywork.com/exchage](http://server1.mywork.com/exchage).

Any ideas?
KF

---

### Post by killerfish on 2006-11-09
No one?  I should mention that I'm on Edgy which has the version of Evolution that is supposed to work?

---

### Post by mn_kthompson on 2006-11-13
Well, I'm certainly no expert, but on my machine I point evolution to [https://mailserver.mywork.org/exchange](https://mailserver.mywork.org/exchange).

Notice that I'm using https, not http and I have included the /exchange at the end of the URL.  See if that does anything for you.

---

### Post by dcstar on 2006-11-14
> **mn_kthompson said:**
> Well, I'm certainly no expert, but on my machine I point evolution to [https://mailserver.mywork.org/exchange](https://mailserver.mywork.org/exchange).

Notice that I'm using https, not http and I have included the /exchange at the end of the URL.  See if that does anything for you.

Exactly, the OWA URL is the OWA URL, just using a default server URL does not get you to the OWA screen (just try it in a browser.....)

---

### Post by killerfish on 2006-11-14
Thanks guys, I've tried that combination as well, same issue.  It seems that possibly my work is using some sort of load balancing (net the server1 and server2 bit in my orig post.).  

Looks like the connector isn't handling it well...  Any other thoughts?

Thanks!
KF

---

### Post by dcstar on 2006-11-15
> **killerfish said:**
> Thanks guys, I've tried that combination as well, same issue.  It seems that possibly my work is using some sort of load balancing (net the server1 and server2 bit in my orig post.).  

Looks like the connector isn't handling it well...  Any other thoughts?

Thanks!
KF

If there is any sort of "load balancing" then possibly there are "real" IP addresses for each server behind a common one advertised for load sharing.

Your only hope may be to find out the DNS/IP of just one of the servers and use that.

BTW, I set up an Edgy Evolution Exchange config today and it all worked as it should first up, including the GAL.

---

### Post by ncarring on 2006-11-26
My problem is Evolution refuses to find the server, although I know it's correct. It's [https://webmail.company.domain](https://webmail.company.domain) - with no /exchange on the end in a browser connection. But Evolution just says "Could not locate server. Make sure the server name is spelled correctly and try again". I have a connection open to this very address in Firefox right now, so how come Evolution can't resolve it?

Thanks

Nick

---

### Post by bimargulies on 2007-12-06
Did you ever figure out what to change on evolution or the exchange server to make authentication work to the second server?

> **killerfish said:**
> Thanks guys, I've tried that combination as well, same issue.  It seems that possibly my work is using some sort of load balancing (net the server1 and server2 bit in my orig post.).  

Looks like the connector isn't handling it well...  Any other thoughts?

Thanks!
KF

---

