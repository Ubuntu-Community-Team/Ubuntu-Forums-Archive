---
title: "How to configure ufw in 18.04 so as to drop unsolicited pings?"
date: 2019-02-13
forum: General Help
---

### Post by kpfuser on 2019-02-13
Past experience with 12.04 and 14.04 regarding the above was that to achieve the stated goal for a single computer placed behind a router, the rules contained in /etc/ufw/before.rules under # ok icmp codes in the case of 12.04, i.e.,

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

or under # ok icmp codes for INPUT as well as # ok icmp codes for FORWARD in the case of 14.04, i.e.,

# ok icmp codes for INPUT
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

and

# ok icmp code for FORWARD
-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type echo-request -j ACCEPT 

should be edited by replacing "ACCEPT" with "DROP" in all cases. Now after a leap past 16.04 landed me in 18.04, I am facing once again the same problem . True to the established tradition, the before.rules set is getting lengthier and thus more complicated with each new LTS version of Ubuntu. Nevertheless the corresponding blocks of rules in before.rules, i.e., # ok icmp codes for INPUT and # ok icmp code for FORWARD are still there and presumably the same editing as before (DROP instead of ACCEPT) can be applied.  Am I right on this?

However, besides the above we now have /etc/ufw/before6.rules where the blocks # ok icmp codes for INPUT (rfc4890, 4.4.1 and 4.4.2), # ok icmp codes for OUTPUT (rfc4890, 4.4.1 and 4.4.2), and # ok icmp codes for FORWARD (rfc4890, 4.3.1) can be found. Should these be edited the same way too? Are there any other files that should be edited in this manner?

Returning to the file before(6).rules. there is also the rule

# allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT

or its equivalent for before6.rules. Can this be edited out (DROP) if no MULTICAST activities (what are they anyway?) are engaged into?

---

