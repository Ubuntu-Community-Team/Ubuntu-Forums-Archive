---
title: "apt-get not working with INPUT DROP"
date: 2016-07-15
forum: General Help
---

### Post by SchnappiJedi on 2016-07-15
When iptables is used to drop incoming packets by default apt-get does not work.

What incoming ports need to be open (besides 80 and 443) for apt-get to work?

-A INPUT -p tcp -m tcp --sport 53 -j ACCEPT
-A INPUT -p udp -m udp --sport 53 -j ACCEPT

Didn't solve the issue.

---

### Post by SchnappiJedi on 2016-07-16
Adding the default rule:
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

Solved problem.

---

### Post by steeldriver on 2016-07-16
I don't think you need 80 and 443 *incoming *for apt-get to work - that would only be necessary if the machine is *serving *http and https

---

### Post by SchnappiJedi on 2016-07-16
> **steeldriver said:**
> I don't think you need 80 and 443 *incoming *for apt-get to work - that would only be necessary if the machine is *serving *http and https

Correct. Don't know why wrote the above about port 80 and 443.

-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

is the solution.

---

